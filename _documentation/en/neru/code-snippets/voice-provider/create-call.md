---
title: Create an Outbound Call
description: How to create an outbound Voice API call with the Voice provider
navigation_weight: 1
---

# Create an Outbound Call

The Voice provider's `vapiCreateCall` function allows you to create an outbound call via the [Voice API](/voice/voice-api/overview), using an [NCCO](/voice/voice-api/ncco-reference).

## Method Signature
```javascript
vapiCreateCall(from: Contact, to: Contact[], ncco: Record<string, unknown>[])
```

## Creating an Outbound Call

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/voice/create-call
```