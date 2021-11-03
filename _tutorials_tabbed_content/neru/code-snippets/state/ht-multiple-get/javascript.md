---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const number = req.body.number;
const otherNumber = "447000000001";

const customers = await state.hmget("customers", [number, otherNumber]);
```