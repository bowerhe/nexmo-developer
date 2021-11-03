---
title: NeRu Deploying
description: This documentation describes NeRu Deploying
meta_title: NeRu Deploying
---

# NeRu Deploying

NeRu allows you to quickly create a running instance on the NeRu platform by deploying. Deploying your bundles your source code with a configuration file, this creates a package. Then the package is uploaded to the NeRu platform and becomes a running instance.

## Configuration File

The configuration files gives information to the NeRu platform on how to deploy your source code. Here is an example configuration file:

```
project:
    name: neru-app
instance:
    name: dev
    runtime: nodejs
    region: aws.euw1
    application-id: fcd08ece-f3c2-4adf-bf84-5ba8a1c86e0e
    configurations:
        contact:
            number: "44700000000"
            type: "phone"
    secrets:
        - FOO
        - BAR
```

A project is a namespace for grouping instances. In the `project` object, `name` is a unique string identifier for your project. You can have multiple instances within a project. For example, an instance for running your production code, and an instance running your development code.

In the instance object, `name` is a unique string identifier for your instance. This allows you to differentiate when you have multiple instances in your project. The name of the instance has no bearing on what environment your instance will be running, this is controlled by the `region`. `region` is the region where the instance will run. The current available regions are:

* EU - `aws.euw1`
* US - `aws.use1`
* APAC - `aws.apse1`

`configurations` allows you to include data in your configuration file to be available to your instance at runtime via the environment. For example, to access the contact object on the above example:

```javascript
const contact = JSON.parse(process.env.NERU_CONFIGURATIONS).contact;
```

`secrets` allows you to expose previously added secrets to your instance at runtime. You can read more about this in the [NeRu Secrets guide](/neru/secrets).

## How to Deploy

You can deploy using the NeRu CLI. To deploy, run:

```sh
neru deploy
```

> If you get a "credentials not found error", run `neru app configue` to configure your Vonage application for NeRu. Credentials are stored per region, so if you want to deploy to a different region, run `neru configure`.

By default, the deploy command will look for a configuration file called `neru.yml` in the current directory. To use a different configuration file you can run:

```sh
neru deploy --filename <path/to/file>
```

So to deploy your current code with a configuration file called `prod.yml`:

```sh
neru deploy --filename production.yml
```

## View your Deployment

To take a deeper look at your project and deployments you can use the [NeRu dashboard](https://dashboard.serverless.vonage.com/).

![Screenshot of the neru dashboard home page](/images/neru/neru-dashboard-home.png)

You can click on your deployed instance which will give you access to logs, events, your instance's configuration, and deployment history. For example opening the config tab will show the configuration for this instance:

![Screenshot of an instance's config page](/images/neru/neru-dashboard-config.png)

Then clicking on the history tab will show you the history of deploys for this instance:

![Screenshot of an instance's history page](/images/neru/neru-dashboard-history.png)

If you deploy more than one instance for your project it will show like so:

![Screenshot of the neru dashboard showing multiple instances](/images/neru/neru-dashboard-instances.png)

This is a project named `vapi`, which has two configuration files. One configuration file has an instance named `dev` and the other has an instance named `prod`. This allows you to have multiple instances running the same code but with different secrets and configurations.