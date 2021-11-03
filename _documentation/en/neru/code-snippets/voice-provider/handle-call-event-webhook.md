---
title: Handle Call Event Webhooks
description: How to handle call event webhooks with the Voice provider
navigation_weight: 4
---

# Handle Incoming Call Webhooks

The Voice provider's `onVapiEvent` function allows you to handle call event webhooks using the [Voice API](/voice/voice-api/overview).

## Method Signature
```javascript
onVapiEvent(params: onVapiEventParams)
```

### Types

`onVapiEventParams`:

* `vapiUUID` | `conversationID`: (String) Use either a VAPI call's UUID or a conversation's ID.
* `callback`: (String) The route to be called for an incoming VAPI Event.

## Handle Call Webhooks

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/voice/handle-call-event-webhooks
```