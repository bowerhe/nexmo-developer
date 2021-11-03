---
title: Use Text to Speech
description: How to use text-to-speech in a conversation with the Voice provider
navigation_weight: 7
---

# Use Text to Speech

The Voice provider allows you to use text-to-speech (TTS) to play machine generated speech in a conversation. You can read more about Vonage's text-to-speech offering and the languages available on the [text-to-speech guide](/voice/voice-api/guides/text-to-speech).

## Say Text

The Voice provider's `Conversation.sayText` function allows you to start playing text-to-speech in a conversation.

### Method Signature
```javascript
Conversation.sayText(body: SayTextBody)
```

#### Types

The function uses the NeRu `SayTextBody` type for customizing the text to be said.

```partial
source: _partials/neru/type-say-text-body.md
```

### Usage

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/say-text
```

## Say Stop

The Voice provider's `Conversation.sayStop` function allows you to stop playing text-to-speech in a conversation.

### Method Signature
```javascript
Conversation.sayStop(sayId: string, to?: string)
```

### Usage

This builds on top of the above snippet, and stops the TTS using the ID from `Conversation.sayText` response. You can use the `to` parameter to stop the TTS for a specific conversation member.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/play-stop
```