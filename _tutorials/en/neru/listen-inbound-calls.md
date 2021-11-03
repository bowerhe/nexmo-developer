---
title: Listen for inbound calls
description: In this step you learn how to listen for inbound calls with NeRu.
---

# Listen for inbound calls

To listen for inbound calls you will need to use the [Voice Provider](/neru/providers/voice). Add the following function below your existing code in the `index.js` file:

```javascript
const startListening = async () => {
    const session = neru.createSession();
    const voice = new Voice(session);
    const contact = JSON.parse(process.env['NERU_CONFIGURATIONS']).contact;

    await voice.onInboundCall('onCall', contact).execute();
}

startListening();
```

The above code creates a NeRu [session](neru/concepts/session), then uses the session to create a voice provider. The `onInboundCall` listener on the voice provider is used to listen for incoming calls to your Vonage number.

The `onInboundCall` function takes a route name as its first parameter. So when your Vonage number gets and incoming call, NeRu will make an call to this route, so next you will define the `onCall` route. 