---
title: Use the NeRu Logger
description: How to use the NeRu Logger
navigation_weight: 3
---

# Use the NeRu Logger

NeRu sessions come equipped with a logger to generate detailed events from your application. The logs will be visible on the [NeRu dashboard](https://dashboard.serverless.vonage.com). 

## Method Signature
```javascript
log(level: LogLevels, message: string, context?: LogContext)
```

### Types

This function uses `LogLevels` for the severity of the log and `LogContext` to attach additional information to the log:

`LogLevels`: (String) The log level, e.g. `error`, `warn`, `info`, or `debug`.

`LogContext`:

* `actionName`: (String)
* `payload`: (String) 
* `result`: (String)

## Using the NeRu Logger

The NeRu Logger has multiple log levels for you to use depending on your needs and supports attaching a context to the log:

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/global/logger
```

Here is an example of a log:

```sh
{
  id: '4f7db707-6ef5-442c-845c-3c3e4a80fd3a',
  session_id: '961fc231-b15c-4137-99a2-b0586ad46da3',
  instance_id: 'debug',
  api_application_id: 'f29538e1-db58-4211-aa4c-adc6dcc83fa0',
  api_account_id: 'abcd1234',
  timestamp: '2022-05-03T11:31:40.560Z',
  log_level: 'error',
  message: 'test error with context',
  source_type: 'application',
  source_id: 'neru-abcd1234-debug-5a590',
  context: {
    actionName: 'creating user',
    payload: '{ user: Alice }',
    result: 'fail'
  }
}
```

Here is the same log on the dashboard:

![NeRu dashboard rendering the above log object](/images/neru/neru-dashboard-log.png)

By using varying log levels, you are able to filter specifically for the severity level you are interested in on the dashboard.



