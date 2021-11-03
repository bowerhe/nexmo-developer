---
title: Handle Incoming Call Webhooks
description: How to handle incoming call webhooks with the Voice provider
navigation_weight: 3
---

# Handle Incoming Call Webhooks

The Voice provider's `onVapiAnswer` function allows you to return an [NCCO](/voice/voice-api/ncco-reference) for incoming call webhooks using the [Voice API](/voice/voice-api/overview).

## Method Signature
```javascript
onVapiAnswer(callback: string)
```

## Handle Call Webhooks

In the `onAnswer` route, you can return an NCCO to instruct the Voice API on how to handle the call.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/voice/handle-call-webhooks
```