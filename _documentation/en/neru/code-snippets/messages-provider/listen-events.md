---
title: Listen for Incoming Events
description: How to listen for incoming events with the Messages provider
navigation_weight: 4
---

# Listen for Incoming Events

The Messages provider allows you to listen for incoming events using the [Messages API](/messages/overview). NeRu Supports both v0.1 and v1 of the Messages API.

## v0.1

### Method Signature
```javascript
listenEvents(from: Contact, to: Contact, callback: string)
```

#### Types

This function uses the NeRu `Contact` type for the sender and recipient of the message.

```partial
source: _partials/neru/type-contact.md
```

## Listening for Events

Using `null` as a wild card character, you can listen for any incoming events to a specified Vonage number. In this example, incoming message status events will call the `onEvent` route.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/listen-events
```

## v1

### Method Signature
```javascript
onMessageEvents(callback: string, from: Contact, to: Contact)
```

#### Types

This function uses the NeRu `Contact` type for the sender and recipient of the message.

```partial
source: _partials/neru/type-contact.md
```

### Listening for Events

Using `null` as a wild card character, you can listen for any incoming events to a specified Vonage number. In this example, incoming message status events will call the `onEvent` route.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/listen-events-v1
```