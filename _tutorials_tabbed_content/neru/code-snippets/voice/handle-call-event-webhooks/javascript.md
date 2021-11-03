---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voice = new Voice(session);

await voice.onVapiEvent({ vapiUUID: "uuid", callback: "onEvent" }).execute();
```