---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const router = neru.Router();
const session = neru.createSession();
const state = session.getState();

await state.set("neru_obj", { "foo": bar });
```