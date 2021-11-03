---
title: Javascript
language: javascript
menu_weight: 1
---

```javascript
const session = neru.createSession();
const voice = new Voice(session);

await voice.uploadNCCO('callID', 
    {
        "action": "transfer",
        "destination": {
            "type": "ncco",
            "ncco": [
            {
                action: 'talk',
                text: "Updated call from NeRu!"
            }
            ]
        }
    }
).execute();
```