---
title: Get Instance Level State
description: How to use instance level state
navigation_weight: 1
---

# Get Instance Level State

The `neru` object on the SDK allows you to access instance level state. Instance level state is a singleton which you can use to share data across multiple instances, compared to the [session state](/neru/providers/state#initializing-the-state-provider) which is specific to a session.

## Method Signature
```javascript
neru.getGlobalState()
```

## Getting Instance Level State

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/global/instance-state
```