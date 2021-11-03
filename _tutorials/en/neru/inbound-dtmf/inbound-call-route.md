---
title: Handle inbound calls
description: In this step you learn how to handle inbound calls with NeRu.
---

# Handle inbound calls

As mentioned in the previous step, you need to define a route to handle your inbound calls. Add the following code below your existing code in the `index.js` file:

```javascript
router.post("/onCall", async (req, res) => {
    const session = neru.createSession();
    const state = session.getState();

    const voice = new Voice(session);
    const conversation = await voice.createConversation();
  
    await state.set('conversationId', conversation.id);

    await conversation.acceptInboundCall(req.body).execute();
    await conversation.sayText({ text: "Please, use your keyboard to provide your date of birth" }).execute();
  
    await conversation.onDTMF('onDTMF').execute();
  
    res.status(200);
});
```

The above code creates a NeRu session. The session is used to create voice provider and get a state provider. The voice provider used to create a [conversation](/conversation/concepts/conversation). The conversation's ID is then stored with the state provider for use later.

The conversation is used to accept the inbound call, and then the `sayText` function allows you to ask the caller for their date of birth. Finally it adds a new listener for DTMF events on this conversation with a route, `onDTMF`. 