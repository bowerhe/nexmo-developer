---
title: Deploy a NeRu Project
description: In this step you learn how to deploy a NeRu Project.
---

# Deploy an instance of your project

By deploying you are creating an instance of your project - a running service that is built from the current version of the code in the folder you specify with the current configuration (neru.yml).

```sh
neru deploy
```

Once the deployment is running you should see the URL in which your application is accessible, similar to the following:

`https://api-eu.vonage.com/v1/neru/i/neru-$API_KEY-$PROJECT_NAME-$ENV_NAME`

The host name indicates the location of the deployment. The path is comprised of your account id (API key), project name, and the environment of the deployment.

In this sample, the trigger to start is making a phone call so there's no need to call an API endpoint to do anything at this point.

## Start using your project

Now that your project is up and running, you can start communicating with your application. 

The sample application we chose for this guide needs to be triggered by a phone call to the number you bought and set in the `neru.yml` file.

Call the number and start the Quiz! Good luck!