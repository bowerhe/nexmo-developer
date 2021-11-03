---
title: Use Audio Streams
description: How to use audio streams in a conversation with the Voice provider
navigation_weight: 8
---

# Use Audio Streams

The Voice provider allows you to play audio streams in a conversation. 

## Play Stream

The Voice provider's `Conversation.playStream` function allows you to start playing an audio stream in a conversation.

### Method Signature
```javascript
Conversation.playStream(body: PlayStreamBody, to?: string)
```

#### Types

The function uses the NeRu `PlayStreamBody` type for customizing the audio stream.

```partial
source: _partials/neru/type-play-stream-body.md
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/play-stream
```

## Stop Stream

The Voice provider's `Conversation.playStop` function allows you to stop playing an audio stream in a conversation.

### Method Signature
```javascript
Conversation.playStop(playId: string, to?: string)
```

### Usage

This builds on top of the above snippet, and stops playing audio using the ID from `Conversation.playStream` response. You can use the `to` parameter to stop the audio for a specific conversation member.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/play-stream
```