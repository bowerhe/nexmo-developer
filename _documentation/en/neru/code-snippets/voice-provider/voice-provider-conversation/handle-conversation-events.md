---
title: Handle Conversation Events
description: How to handle conversation events with the Voice provider
navigation_weight: 5
---

# Handle Conversation Events

The Voice provider's [`Conversation.listenForEvents`](/neru/code-snippets/voice-provider/voice-provider-conversation/listen-events) function allows you to listen for all conversation [events](/conversation/concepts/event) and filter as you like. NeRu also offers some wrappers around `Conversation.listenForEvents` covering some of the common events. Similarly to other listeners, pass in a callback route for NeRu to call.

## Conversation Created

When a conversation is created.

### Method Signature
```javascript
Conversation.onConversationCreated(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/conversation-created
```

---
## Leg Status Update

When a [leg](/conversation/concepts/leg) is updated.

### Method Signature
```javascript
Conversation.onLegStatusUpdate(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-leg-status
```

---
## DTMF

When a [DTMF](/voice/voice-api/guides/dtmf) event is received.

### Method Signature
```javascript
Conversation.onDTMF(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-dtmf
```

---
## Say Start

When text-to-speech starts.

### Method Signature
```javascript
Conversation.onSay(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-say
```

## Say Stop

When text-to-speech stops.

### Method Signature
```javascript
Conversation.onSayStop(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-say-stop
```

## Say Done

When text-to-speech completes.

### Method Signature
```javascript
Conversation.onSayDone(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-say-done
```

---
## Play Start

When an audio stream starts.

### Method Signature
```javascript
Conversation.onPlay(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-play
```

## Play Stop

When an audio stream stops.

### Method Signature
```javascript
Conversation.onPlayStop(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-play-stop
```

## Play Done

When an audio stream completes.

### Method Signature
```javascript
Conversation.onPlayDone(callback: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-play-done
```

---
## Member Invited

When a conversation member is invited. `memberName` is optional and can be omitted.

### Method Signature
```javascript
Conversation.onMemberInvited(callback: string, memberName?: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-member-invited
```

## Member Joined

When a conversation member joins. `memberName` is optional and can be omitted.

### Method Signature
```javascript
Conversation.onMemberJoined(callback: string, memberName?: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-member-joined
```

## Member Left

When a conversation member leaves. `memberName` is optional and can be omitted.

### Method Signature
```javascript
Conversation.onMemberLeft(callback: string, memberName?: string)
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/on-member-left
```