---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
import { neru } from "neru-alpha";

const session = neru.createSession();

session.log("info", "test info");
session.log("debug", "test debug");
session.log("warn", "test warn");
session.log("error", "test error");
session.log("error", "test error with context", { actionName: "creating user", payload: "{ user: Alice }", result: "fail" });
```