---
title: Handle inbound DTMF
description: In this step you learn how to handle inbound DTMF with NeRu.
---

# Handle inbound DTMF

Much like the previous step you now need to define a route for the DTMF listener defined in the previous step. Add the follow code to the bottom of the `index.js` file:

```javascript
router.post("/onDTMF", async (req, res) => {
    const digit = req.body.event.body.digit;

    const session = neru.getSessionFromRequest(req);
    const state = session.getState();
    
    const voice = new Voice(session);
    const conversationId = await state.get('conversationId');
    const conversation = voice.getConversation(conversationId);
  
    conversation.sayText({text: `I received ${digit}`}).execute();
  
    res.status(200);
});
    
export { router };
```

The above code gets the digit pressed from the incoming request's body, and creates a NeRu session using that request. The NeRu session is used to create state and voice providers. The conversation ID is retried from the state and used to get the existing conversation, which then uses text-to-speech to relay the digits pressed back to the caller.

## Deploy an instance of your project

By deploying you are creating an instance of your project - a running service that is built from the current version of the code with the current configuration (neru.yml). You can deploy your project by running:

```sh
neru deploy
```

Once complete you can now call your Vonage Number and hear the digits you press!