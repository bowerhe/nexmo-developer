---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voice = new Voice(session);

const conversation = await voice.createConversation();

await conversation.addUser("Alice").execute();
```