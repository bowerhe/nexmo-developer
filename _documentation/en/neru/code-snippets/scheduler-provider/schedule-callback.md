---
title: Schedule a Callback
description: How to schedule a callback with the Scheduler provider
navigation_weight: 1
---

# Schedule a Callback

The Scheduler provider allows you schedule a route on your application to be called in the future after a specified time, or repeatedly on an interval.


## Method Signature
```javascript
startAt(params: startAtParams)
```

### Types

This function takes parameters to configure the scheduled callback:

* `startAt`: (String) - The date to start the scheduled callback in ISO format.
* `callback`: (String) - The route to be called.
* `id`: (Optional String) - Identifier for the scheduled callback.
* `interval`: (Optional `IntervalParams`) - If specified, the scheduled callback will repeat on this interval.
* `payload`: (Optional Object) - Optional data to send to the callback.

`IntervalParams`:

* `cron`: (String) - Use a [CRON](https://en.wikipedia.org/wiki/Cron) expression schedule how often the route is called.
* `until`: (`UntilParams`) - Stop the scheduler after a specified time.

`UntilParams`:

* `date`: (String) - A date in ISO format.
* `maxInvocations`: (Int) - The maximum number of times the scheduler should run.

## Scheduling a Callback

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/scheduler/schedule
```