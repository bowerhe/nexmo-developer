---
title: Create a NeRu Project
description: In this step you learn how to create a NeRu Project.
---

# Create a NeRu Project

In your project folder, run:

```sh
neru init
```

- Choose project name (You can leave it with the folder name as default by pressing enter)
- Choose the application you created earlier
- Choose runtime environment - `nodejs`
- Choose a region
- Choose the instance name - `dev`
- Choose the template for this sample - `AkiraQuizVoice`

## Configure your project 

- Open the `neru.yml` file in a text editor
- Update the configuration object with the number you bought earlier, and linked to your application.

Your file should look similar to this, with `$VONAGE_NUMBER` being your Vonage number:

```yml
project:
    name: neru-test-app
instance:
    name: dev
    runtime: nodejs
    region: aws.euw1
    application-id: d9725658-1dcb-4e99-80b5-5ec1b75f47dc
    configurations:
        contact:
            number: "$VONAGE_NUMBER"
            type: "phone"
```

## Install the JavaScript dependencies

By initializing your NeRu project with the `AkiraQuizVoice` template you now have in your folder the code to run the quiz.

You now need to make sure to have all the dependencies of the JavaScript code installed correctly, run:

```sh
npm install
```