---
title: NeRu Secrets
description: This documentation describes the NeRu Secrets
meta_title: NeRu Secrets
---

# NeRu Secrets

NeRu Secrets allow you to store sensitive information for use in your projects. Secrets are managed through the NeRu CLI.

## Creating a Secret

To create a secret, you can use the NeRu CLI secrets create command.

```sh
neru secrets create --name <name> --value <value>
```

So to create a secret `FOO` with the value `bar`:

```sh
neru secrets create --name FOO --value bar
```

You can also add files as secrets:

```sh
neru secrets create --name <name> --file <path/to/file>
```

## Accessing your Secrets

To access a secret in your instance, you need to add it to your configuration file to expose it. Add a `secrets` key to your configuration file with a list of the secrets you want to expose:

```yml
project:
    name: neru-app
instance:
    name: dev
    runtime: nodejs
    region: aws.euw1
    application-id: fcd08ece-f3c2-4adf-bf84-5ba8a1c86e0e
    secrets:
        - FOO
```

Now that the secret is in your configuration file, they will be injected into your instance when you run the NeRu deploy your project. When secrets are injected into your instance, they are converted into upper snake case and prefixed with `NERU_SECRET`.

So for the earlier example of `FOO`, it will be available on your instance's environment as `NERU_SECRET_FOO`:

```javascript
const fooSecret = process.env.NERU_SECRET_FOO;
```

## Updating Secrets

Updating secrets works similarly to creating secrets, but to update you use `neru secrets update`:

```sh
neru secrets update --name <name> --value <changed-value>
```

To update the `FOO` example:

```sh
neru secrets update --name FOO --value baz
```

## Removing Secrets

Secrets can be removed using `neru secrets remove`:

```sh
neru secrets remove <secret_name>
```

To remove the `FOO` example:

```sh
neru secrets remove FOO
```

## Working with Secrets Locally

When you are debugging your project locally, you will not have access to the secrets stored on the NeRu platform. It is recommended that you create a `.env` file in your project directory and add your development secrets there:

```
export NERU_SECRET_FOO=BAR
export NERU_SECRET_BAZ=BAT
export NERU_SECRET_X=Y
```

Then before you start debugging run:

```
source .env
```

> The environment variables need to be set in the same shell process that you are running the NeRu debugger in. 

This will export the development secrets in your current terminal shell process, allowing the NeRu debugger to access them. Note how the `.env` file secrets follow the same naming scheme as the production NeRu platform secrets, this means you will not need to change any code when you are running the project locally or when it is deployed.