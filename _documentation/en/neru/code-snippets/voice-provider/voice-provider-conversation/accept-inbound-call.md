---
title: Accept an Inbound Call
description: How to accept an inbound call with the Voice provider
navigation_weight: 3
---

# Accept an Inbound Call

The Voice provider's `Conversation.acceptInboundCall` function allows you to accept an inbound call. You can use it in the callback function of [`onInboundCall`](/neru/code-snippets/voice-provider/handle-calls.md) to accept calls in your application.

## Method Signature
```javascript
Conversation.acceptInboundCall(event: AcceptInboundCallEvent)
```

### Types

This function uses the NeRu `AcceptInboundCallEvent` type for information of the incoming call. It is expected that you will use `Conversation.acceptInboundCall` in a callback function, so you can pass in the `req.body` of the incoming request to your application.

## Accepting an Inbound Call

This route is a callback for [`onInboundCall`](/neru/code-snippets/voice-provider/handle-calls.md).

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/inbound-call
```