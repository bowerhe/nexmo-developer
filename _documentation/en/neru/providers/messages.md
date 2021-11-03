---
title: Messages
description: The Messages Provider
navigation_weight: 3
---

# Messages Provider

The Messages provider gives you an interface for the [Messages API](/messages/overview). Depending on which version of the Messages API your application is using, the provider has different functions.

## Functions
* V0.1: [`sendText`](/neru/code-snippets/messages-provider/send-message#v0-1)
* V0.1: [`sendImage`](/neru/code-snippets/messages-provider/send-image)
* V0.1: [`listenMessages`](/neru/code-snippets/messages-provider/listen-messages#v0-1)
* V0.1: [`listenEvents`](/neru/code-snippets/messages-provider/listen-events#v0-1)
* V1: [`send`](/neru/code-snippets/messages-provider/send-message#v1)
* V1: [`onMessage`](/neru/code-snippets/messages-provider/listen-messages#v1)
* V1: [`onMessageEvents`](/neru/code-snippets/messages-provider/listen-events#v1)
* [`unsubscribeEvents`](/neru/code-snippets/messages-provider/unsubscribe-events)

## Initializing the Messages Provider

To use the Messages Provider you need to create an instance of the provider using a session:

```javascript
const session = neru.createSession();
const messaging = new Messages(session);
```

## Use Case

For example, to use the use the Messages provider to send a text message using V0.1 of the Messages API:

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

const to = { type: "sms", number: "447700900000" };
const from = { type: "sms", number: "447700900001" }; 

await messaging.sendText(from, to, "Hello World").execute();
```

Here is the same code using V1 of the Messages API:

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

const vonageNumber = { type: "sms", number: "447700900000" };
const to = "447700900001";

await messages.send({
    message_type: "text",
    to: to,
    from: vonageNumber.number,
    channel: vonageNumber.type,
    text: "Hello World"
}).execute();
```