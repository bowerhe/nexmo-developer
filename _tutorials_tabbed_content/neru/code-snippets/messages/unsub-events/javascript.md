---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const messaging = new Messages(session);

await messaging.unsubscribeEvents("listenerId").execute();
```