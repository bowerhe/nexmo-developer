---
title: View a NeRu Project
description: In this step you learn how to view a NeRu Project in the dashboard.
---

# View a NeRu Project

To view your NeRu projects you can run the following command:

```sh
neru project list
```

This will display your NeRu projects in a list like so:

```json
[
  {
    "id": "5e2e9cd3-5f31-4fdd-8e45-48a20799824c",
    "name": "neru-test-app",
    "api_account_id": "febe6726",
    "created_at": "2022-01-27T15:19:26.194148",
    "updated_at": "2022-01-27T15:19:26.194148"
  }
]
```

To take a deeper look at your project and deployments you can use the [NeRu dashboard](https://dashboard.serverless.vonage.com/).

![Screenshot of the neru dashboard home page](/images/neru/neru-dashboard-home.png)

You can click on your deployed instance which will give you access to logs, events, your instance's configuration, and deployment history.

![Screenshot of the neru dashboard instance page](/images/neru/neru-dashboard-instance.png)