---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const scheduler = new Scheduler(session);

const response = await scheduler.startAt({
    startAt: new Date(Date.now() + 5000).toISOString(),
    callback: 'onScheduler',
    payload: {
        text: 'hello world!',
    },
}).execute();

const scheduleID = response.body.schedule_id;
```