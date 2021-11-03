---
title: Voice
description: The Voice Provider
navigation_weight: 2
---

# Voice Provider

The Voice provider gives you an interface for the [Voice](/voice/voice-api/overview) and [Conversation](/conversation/overview) APIs.

## Functions

* [`vapiCreateCall`](/neru/code-snippets/voice-provider/create-call)
* [`onInboundCall`](/neru/code-snippets/voice-provider/handle-calls)
* [`onVapiAnswer`](/neru/code-snippets/voice-provider/handle-call-webhook)
* [`onVapiEvent`](/neru/code-snippets/voice-provider/handle-call-event-webhook)
* [`uploadNCCO`](/neru/code-snippets/voice-provider/update-call)
* [`createConversation`](/neru/code-snippets/voice-provider/voice-provider-conversation/create-conversation)
* [`getConversation`](/neru/code-snippets/voice-provider/voice-provider-conversation/get-conversation)
* [`Conversation.acceptInboundCall`](/neru/code-snippets/voice-provider/voice-provider-conversation/accept-inbound-call)
* [`Conversation.listenForEvents`](/neru/code-snippets/voice-provider/voice-provider-conversation/listen-events)
* [`Conversation.onConversationCreated`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#conversation-created), [`Conversation.onLegStatusUpdate`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#leg-status-update), [`Conversation.onDTMF`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#dtmf), [`Conversation.onSay`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#say-start), [`Conversation.onSayStop`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#say-stop), [`Conversation.onSayDone`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#say-done), [`Conversation.onPlay`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#play-start), [`Conversation.onPlayStop`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#play-stop), [`Conversation.onPlayDone`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#play-done), [`Conversation.onMemberInvited`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#member-invited), [`Conversation.onMemberJoined`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#member-joined), [`Conversation.onMemberLeft`](/neru/code-snippets/voice-provider/voice-provider-conversation/handle-conversation-events#member-left)
* [`Conversation.sayText`](/neru/code-snippets/voice-provider/voice-provider-conversation/use-text-to-speech#say-text), [`Conversation.sayStop`](/neru/code-snippets/voice-provider/voice-provider-conversation/use-text-to-speech#say-stop)
* [`Conversation.playStream`](/neru/code-snippets/voice-provider/voice-provider-conversation/use-audio-streams#play-stream), [`Conversation.playStop`](/neru/code-snippets/voice-provider/voice-provider-conversation/use-audio-streams#stop-stream)
* [`Conversation.addUser`](/neru/code-snippets/voice-provider/voice-provider-conversation/create-user)
* [`Conversation.inviteMember`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#invite-a-member), [`Conversation.transferMember`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#transfer-a-member), [`Conversation.deleteMember`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#delete-a-member)
* [`Conversation.muteOn`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#mute-a-member), [`Conversation.muteOff`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#unmute-a-member)
* [`Conversation.earmuffOn`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#earmuff-a-member), [`Conversation.earmuffOff`](/neru/code-snippets/voice-provider/voice-provider-conversation/manage-members#unearmuff-a-member)

## Initializing the Voice Provider

To use the Voice Provider you need to create an instance of the provider using a session:

```javascript
const session = neru.createSession();
const voice = new Voice(session);
```

## Use Case

For example, you can use the Voice provider to answer an incoming Voice API Call:

```javascript
const router = neru.Router();
const session = neru.createSession();
const voice = new Voice(session);

await voice.onVapiAnswer('onCall').execute();

router.post('/onCall', async (req, res, next) => {
    res.json([
        {
            action: 'talk',
            text: 'Hello from Vonage!'
        }
    ]);
});
```

Or, you can handle inbound calls using the Conversation API:

```javascript
const router = neru.Router();
const session = neru.createSession();
const voice = new Voice(session);

const vonageNumber = { type: "phone", number: "447000000000"}
await voice.onInboundCall('onCall', vonageNumber).execute();

router.post("/onCall", async (req, res) => {
    const session = neru.createSession();
    const voice = new Voice(session);
    const conversation = await voice.createConversation();
  
    await conversation.acceptInboundCall(req.body).execute();
    await conversation.sayText({ text: "Hello from Vonage!" }).execute();
  
    res.sendStatus(200);
});
```