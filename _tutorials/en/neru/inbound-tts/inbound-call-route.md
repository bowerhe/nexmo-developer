---
title: Handle inbound calls
description: In this step you learn how to handle inbound calls with NeRu.
---

# Handle inbound calls

As mentioned in the previous step, you need to define a route to handle your inbound calls. Add the following code below your existing code in the `index.js` file:

```javascript
router.post("/onCall", async (req, res) => {
    const session = neru.createSession();
    const voice = new Voice(session);
    const conversation = await voice.createConversation();
  
    await conversation.acceptInboundCall(req.body).execute();
    await conversation
      .sayText({
        text: `<speak>Hello user, your number is: <say-as interpret-as='digits'>${req.body.body.channel.from.number}</say-as></speak>`,
        ssml: true
      })
      .execute();
  
    res.status(200);
});

export { router };
```

The above code create a NeRu session, but this time it creates it from the incoming request. The session is used to create a voice provider, which is then used to create a [conversation](/conversation/concepts/conversation).

This conversation accepts the inbound call, and then the `sayText` function allows you to greet your caller with text-to-speech. `sayText` is using [SSML](https://www.w3.org/TR/speech-synthesis11/) to read the phone number out digit by digit.

## Deploy an instance of your project

By deploying you are creating an instance of your project - a running service that is built from the current version of the code with the current configuration (neru.yml). You can deploy your project by running:

```sh
neru deploy
```

Once complete you can now call your Vonage Number and hear the greeting!