---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

const vonageNumber = { type: "sms", number: "447700900000" };
const to = "447700900001";

await messages.send({
    message_type: "text",
    to: to,
    from: vonageNumber.number,
    channel: vonageNumber.type,
    text: "Hi"
}).execute();
```