---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const scheduler = new Scheduler(session);

await scheduler.cancel("scheduleID").execute();
```