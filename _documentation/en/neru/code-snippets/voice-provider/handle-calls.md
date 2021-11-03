---
title: Handle Incoming Calls
description: How to handle incoming calls with the Voice provider
navigation_weight: 2
---

# Handle Incoming Calls

The Voice provider's `onInboundCall` function allows you to handle incoming calls using the [Voice API](/voice/voice-api/overview).

## Method Signature
```javascript
onInboundCall(callback: string, to: ChannelPhoneEndpoint, from?: ChannelPhoneEndpoint)
```

### Types

This function uses the NeRu `ChannelPhoneEndpoint` type for the caller and recipient of the call.

```partial
source: _partials/neru/type-channel-phone-endpoint.md
```

## Handle Calls

Omitting the `from` parameter, you can handle any incoming calls to a specified Vonage number. Incoming calls will call the `onCall` route.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/voice/handle-call
```