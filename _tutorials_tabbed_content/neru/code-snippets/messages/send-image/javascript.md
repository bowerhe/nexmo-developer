---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

const to = { type: "mms", number: "447700900000" };
const from = { type: "mms", number: "447700900001" }; 
const imageData = {
    url: "https://example.com/image.png",
    caption: "Example image"
    };

await messaging.sendImage(from, to, imageData).execute();
```