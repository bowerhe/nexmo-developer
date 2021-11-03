---
title: Create a NeRu Project
description: In this step you learn how to create a NeRu Project.
---

# Create a NeRu Project

In your project folder, run

```
neru init
```

- Choose project name
- Choose the application you created earlier
- Choose runtime environment - `nodejs`
- Choose a region
- Choose the instance name - `dev`
- Skip a template

## Install the NeRu SDK

You now need to install the NeRu SDK and other dependencies, run:

```sh
npm init -y
```

This will create a `package.json` file for your project, then run:

```sh
npm install -s neru-alpha
```

This will install the NeRu SDK.

## Configure your project 

- Open the `neru.yml` file in your text editor and update the configuration object with the number you bought earlier, and linked to your application. Your file should look similar to this, with `$VONAGE_NUMBER` being your Vonage number:

```yml
project:
    name: neru-test-app
instance:
    name: dev
    runtime: nodejs
    region: aws.euw1
    application-id: f739b3d4-3d49-43b2-91d3-593905857f3a
    configurations:
        contact:
            number: "$VONAGE_NUMBER"
            type: "phone"
```

- Open the `package.json` file and add the `type` property with value "module" to the file. Your file should look similar to this:

```json
{
  "name": "neru-test-app",
  "version": "1.0.0",
  "type": "module",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "neru-alpha": "^0.3.0"
  }
}
```