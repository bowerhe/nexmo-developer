---
title: Manage Conversation Members
description: How to manage conversation members with the Voice provider
navigation_weight: 9
---

# Manage Conversation Members

The Voice provider allows you to manage conversation [members](/conversation/concepts/member).

## Invite a Member

Inviting a member adds them to a conversation.

### Method Signature
```javascript
Conversation.inviteMember(name: string, channel: Channel)
```

#### Types

The function using the NeRu `Channel` type for the information of how to invite the member. 

```partial
source: _partials/neru/type-channel.md
```

### Inviting a Member

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/invite-member
```

## Transfer a Member

Transfer a member between conversation legs.

### Method Signature
```javascript
Conversation.transferMember(userId: string, legId: string)
```

### Transferring a Member

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/transfer-member
```

## Delete a Member

Delete a conversation member.

### Method Signature
```javascript
Conversation.deleteMember(memberId: string)
```

### Deleting a Member

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/delete-member
```

---
## Mute a Member

Mute a conversation member.

### Method Signature
```javascript
Conversation.muteOn(to: string, from?: string)
```

### Muting a Member

You can pass another member ID to the optional `from` parameter to show one member muting another.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/mute-member
```

## Unmute a Member

Mute a conversation member.

### Method Signature
```javascript
Conversation.muteOff(to: string, from?: string)
```

### Unmuting a Member

You can pass another member ID to the optional `from` parameter to show one member unmuting another.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/unmute-member
```

---
## Earmuff a Member

Earmuff a conversation member.

### Method Signature
```javascript
Conversation.earmuffOn(to: string, from?: string)
```

### Earmuffing a Member

You can pass another member ID to the optional `from` parameter to show one member earmuffing another.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/earmuff-member
```

## Unearmuff a Member

Mute a conversation member.

### Method Signature
```javascript
Conversation.earmuffOff(to: string, from?: string)
```

### Unearmuffing a Member

You can pass another member ID to the optional `from` parameter to show one member unearmuffing another.

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/conversation/unearmuff-member
```