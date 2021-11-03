---
title: Send a Message
description: How to send a message with the Messages provider
navigation_weight: 1
---

# Send a Message

The Messages provider allows you to send a message using the [Messages API](/messages/overview). NeRu Supports both v0.1 and v1 of the Messages API.

# v0.1

### Method Signature
```javascript
sendText(from: Contact, to: Contact, message: string)
```

#### Types

This function uses the NeRu `Contact` type for the sender and recipient of the message.

```partial
source: _partials/neru/type-contact.md
```

### Sending a Message

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/send-text
```

## v1

### Method Signature
```javascript
send(message: BaseMessage)
```

#### Types

This function uses the NeRu `BaseMessage` type. Depending on your `message_type` you will need to use additional parameters:

`BaseMessage`:

* `message_type`: (String) The type of the message, e.g. `text`, `image`, `audio`, `video`, `file`, `template` or `custom`.
* `to`: (String) The recipients phone number in in the E.164 format or ID number, for use with Facebook Messenger.
* `from`: (String) Your Vonage Number phone number in in the E.164 format or ID number, for use with Facebook Messenger.
* `channel`: (String) The channel of the message, e.g. `sms`, `mms`, `whatsapp`, `messenger` or `viber_service`.

For text add:

* `text`: (String) The text to be sent.

For Image add an `image` object with the following:

* `url`: (String) A URL to the image.
* `caption`: (Optional String) A caption for the image.

For Audio add an `audio` object with the following:

* `url`: (String) A URL to the audio file.

For MMS VCard add an `vcard` object with the following:

* `url`: (String) A URL to the image.
* `caption`: (Optional String) A caption for the image.

### Sending a Message

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/send-message
```

### Sending an Image

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/send-message-image
```

### Sending Audio

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/messages/send-message-audio
```