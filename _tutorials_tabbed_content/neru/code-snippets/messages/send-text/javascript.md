---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

const to = { type: "sms", number: "447700900000" };
const from = { type: "sms", number: "447700900001" }; 

await messaging.sendText(from, to, "hello world").execute();
```