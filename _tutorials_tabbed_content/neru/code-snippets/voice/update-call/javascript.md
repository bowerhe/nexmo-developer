---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voiceApi = new Voice(session);

await voiceApi.uploadNCCO('callID', ncco).execute();
```