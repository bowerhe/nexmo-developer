---
title: NeRu Sessions
description: This documentation describes the NeRu Sessions
meta_title: NeRu Sessions
---

# NeRu Sessions

Sessions allow you to create and persist context within your instance seamlessly. Your instance can have many sessions, a one (instance) to many (sessions) relationship. Sessions are created when you want to use a provider or access state. Then sessions can be restored on subsequent calls to your instance to access previous context. 


## Creating a Session

Sessions can be created by calling the `createSession` function:

```javascript
const session = neru.createSession();
```

The new session can be used to access providers and state:

```javascript
import { neru, Voice } from 'neru-alpha';

const session = neru.createSession();
const voice = new Voice(session);
const state = session.getState();
```

Calling functions on the `voice` or `state` object will now be associated with this session. This is done by NeRu setting a header on requests with the session ID.

## Session Restoration

You can store a session for use later, then restore the session from a session ID:

```javascript
const session = neru.getSessionById('sessionID');
```

When you have subsequent incoming requests into your application you can restore an existing session using the `getSessionFromRequest` function:

```javascript
router.post('/onMessage', async (req, res, next) => {
    const session = neru.getSessionFromRequest(req);
    ...
});
```

`getSessionFromRequest` will look for a header on the request:

```
'x-neru-sessionid': '44092039-fa65-41a6-a9ce-97a7d1274b96',
```

Then using the session ID on the request header, `getSessionFromRequest` internally will call `getSessionById`. This allows you to reason about your code in relation to a session and events in a session. 

This simplifies state operations since you can be certain that the session's state object is only aware of this session. 

## Session Restoration Example

To demonstrate, here is the example of a NeRu application that carries context between an incoming phone call and text message from the same user:

```javascript
router.post('/onCall', async (req, res, next) => {
    const session = neru.createSession();
    const voice = new Voice(session);
    const messages = new Messages(session);

    await voice.onVapiEvent({ vapiUUID: req.body.uuid, callback: "onEvent" }).execute();
    await messages.onMessage(
        'onMessage',
        {type: 'sms', number: req.body.from },
        vonageNumber
    ).execute();

    res.json([
        {
            action: 'talk',
            text: 'Say some words, then text this number for a transcript',
        },
        {
          "action": "input",
          "type": ["speech"]
        }
    ]);
});
```

The `onCall` route is called when there is an incoming call to the application. A new session is created which is used to set up a listener for incoming sms messages from the number calling as well as voice events from the call.

The NeRu platform receives incoming RTC, Voice, and Messages webhooks to your Vonage application as configured by `neru app configure`. If you have a listener for these webhooks, they will be sent to your application if the incoming webhook satisfies the filters on the listener e.g. the from number. 

Since the listeners are set up with a session, any requests that satisfy the filters on the listener will be sent to your application on the route specified with the `x-neru-sessionid` set. 


```javascript
router.post('/onEvent', async (req, res, next) => {
    if (req.body.speech != null) {
        const session = neru.getSessionFromRequest(req);
        const state = session.getState();
        await state.set('text', req.body.speech.results[0].text);
    } else {
        console.log(req.body)
    }
    res.sendStatus(200);
});
```

In the `onEvent` route, a session is being restored by using `getSessionFromRequest`. That session's state is being used to store the speech to text results from the phone call. Notice how there was no need to use any form of identifier on the state since the state is local to this session, which is the same session created when the user called.

```javascript
router.post('/onMessage', async (req, res, next) => {
    const session = neru.getSessionFromRequest(req);
    const messages = new Messages(session);
    const state = session.getState();
    const text = await state.get('text');
   
    await messages.send({
        message_type: "text",
        to: req.body.from,
        from: vonageNumber.number,
        channel: vonageNumber.type,
        text: text
    }).execute();

    res.sendStatus(200);
});
```

Finally, once the user sends an incoming text to request the transcript from their call in `onMessage`, the original session is restored again, which has the state on it.