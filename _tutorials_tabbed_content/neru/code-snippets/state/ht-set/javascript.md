---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const router = neru.Router();
const session = neru.createSession();
const state = session.getState();

const customer = req.body;
const number = customer.number;

await state.hset("customers", [[number , customer]]);
```