---
title: Listen for All Conversation Events
description: How to listen for all conversation events with the Voice provider
navigation_weight: 4
---

# Listen for Conversation Events

The Voice provider's `Conversation.listenForEvents` function allows you to listen for all conversation [events](/conversation/concepts/event) and filter as you like.

## Method Signature
```javascript
Conversation.listenForEvents(callback: string, filters: Filter[])
```

### Types

This function uses the NeRu `Filter` type to filter the events that will trigger your callback. 

```partial
source: _partials/neru/type-filter.md
```

## Listening for Conversation Events

Incoming events matching your filter will call the `onEvent` route.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/listen-events
```