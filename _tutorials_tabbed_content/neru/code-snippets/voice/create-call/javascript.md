---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voice = new Voice(session);

const vonageNumber = { type: "phone", number: "447000000000"}
const to = { type: "phone", number: "447000000001"}

await voice.vapiCreateCall(
    vonageNumber,
    [to],
    [
        {
            action: 'talk',
            text: "Hello from NeRu!",
        }
    ]
).execute();
```