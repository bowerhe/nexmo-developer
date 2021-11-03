---
title: Create an Outbound Call
description: In this step you learn how to create an Outbound Call with NeRu.
---

# Create an Outbound Call

Now that the form is displaying, you will need to handle the form submission. Create a new route for `/call`:

```javascript
router.post('/call', async (req, res, next) => {
    try {
        const session = neru.createSession();
        const voice = new Voice(session);

        const vonageNumber = JSON.parse(process.env.NERU_CONFIGURATIONS).contact;
        const to = { type: 'phone', number: req.body.number };
    
        const response = await voice
            .vapiCreateCall(
                vonageNumber,
                [to],
                [
                    {
                        action: 'talk',
                        text: "Hi! This is a call made by VAPI and NeRu",
                    }
                ]
            )
            .execute();
    
        await voice.onVapiEvent(response?.uuid, 'onEvent').execute();
        res.redirect('/');
    } catch (error) {
        next(error);
    }
});
```

The above route creates a session, which is used to create a voice provider object. The Vonage number you linked to this application is parsed from the `contact` configuration that was added to the `neru.yml` file. 

Then, `vapiCreateCall` is used to create the outbound call. `vapiCreateCall` takes a from number, a to number, and a call control object. The response for the outbound call is stored so `onVapiEvent` can be used to subscribe to the call's events.

Add a route to your `index.js` file to handle the incoming events:

```javascript
router.post('/onEvent', async (req, res) => {
    console.log('event status is: ', req.body.status);
    console.log('event direction is: ', req.body.direction);
    res.sendStatus(200);
});
```

If you save the file, the debugger will reload with your new code. If you refresh the website and enter your phone number you will receive a call!

## Deploy an Instance of your Project

By deploying you are creating an instance of your project - a running service that is built from the current version of the code with the current configuration (neru.yml). 

Stop your debug process, then deploy your project by running:

```sh
neru deploy
```

