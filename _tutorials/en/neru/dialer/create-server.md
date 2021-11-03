---
title: Create your Node server
description: In this step you learn how to create a node server for your NeRu Project.
---

# Create your Node server

In your project folder create a new file by running:

```
touch index.js
```

Then open the new file in your text editor. This file will house the Node server that you will deploy to NeRu. At the top of the file import the dependencies:

```javascript
import { Voice, neru } from 'neru-alpha';
import { fileURLToPath } from 'url';
import express from 'express';
import path from 'path';
```

This NeRu is using express to run a Node server. Below the imports, create a express router: 

```javascript
const router = neru.Router();
```