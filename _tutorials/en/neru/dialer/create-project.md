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
npm init esnext -y
```

This will create a `package.json` file for your project, then run:

```sh
npm install -s neru-alpha express
```

This will install the NeRu SDK and Express JS.

## Configure your project 

- To use the Voice API with your NeRu project you need to enable the Voice API webhooks. You can do so with the NeRu CLI:

```sh
neru app configure --voice=true --messages=true --rtc=false --app-id=$YOUR_VONAGE_APP_ID
```

> Currently you can only use either Voice or RTC webhooks, so make sure to disable RTC for this tutorial.

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