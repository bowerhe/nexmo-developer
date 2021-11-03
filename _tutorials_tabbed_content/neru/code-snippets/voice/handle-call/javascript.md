---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voice = new Voice(session);

const vonageNumber = { type: "phone", number: "447700900000" };

await voice.onInboundCall('onCall', vonageNumber).execute();
```