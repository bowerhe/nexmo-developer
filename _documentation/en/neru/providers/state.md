---
title: State
description: The State Provider
navigation_weight: 4
---

# State Provider

The State provider allows you to store data on NeRu for your project instance to use. The state provider has a key-value store at its root. As well as lists and maps with various operations you can perform on them.

## Functions

* [`set<T>(key: string, value: T)`](/neru/code-snippets/state-provider/key-value-operations#set-a-value)
* [`get<T>(key: string)`](/neru/code-snippets/state-provider/key-value-operations#get-a-value)
* [`del(key: string)`](/neru/code-snippets/state-provider/key-value-operations#delete-a-value)
* [`hset(htable: string, keyValuePairs: [string, string][])`](/neru/code-snippets/state-provider/hash-table-operations#set-hash-table-values)
* [`hget<T>(htable: string, key: string)`](/neru/code-snippets/state-provider/hash-table-operations#get-a-hash-table-value)
* [`hmget<T>(htable: string, keys: string[])`](/neru/code-snippets/state-provider/hash-table-operations#getting-multiple-hash-table-values)
* [`hvals<T>(htable: string)`](/neru/code-snippets/state-provider/hash-table-operations#getting-all-hash-table-values)
* [`hgetall<T>(htable: string)`](/neru/code-snippets/state-provider/hash-table-operations#get-a-hash-table)
* [`hexists(htable: string, key: string)`](/neru/code-snippets/state-provider/hash-table-operations#check-a-hash-table-key-exists)
* [`hdel(htable: string, key: string)`](/neru/code-snippets/state-provider/hash-table-operations#delete-a-hash-table-value)
* [`lpush<T>(list: string, value: T)`](/neru/code-snippets/state-provider/list-operations#insert-elements-at-the-list-s-start)
* [`rpush<T>(list: string, value: T)`](/neru/code-snippets/state-provider/list-operations#insert-elements-at-the-list-s-end)
* [`llen(list: string)`](/neru/code-snippets/state-provider/list-operations#get-a-list-s-length)
* [`lrange<T>(list: string, startPos: number, endPos: number)`](/neru/code-snippets/state-provider/list-operations#get-a-list-elements-with-a-range)

## Initializing the State Provider

To can access the state provider from a NeRu session:

```javascript
const session = neru.createSession();
const state = session.getState();
```

On subsequent calls to your code, you want to make sure that you are using the same session to have access to your state. You can do so by initializing your instance from an incoming request: 

```javascript
router.post("/onMessage", async (req, res, next) => {
  try {
    const session = neru.getSessionFromRequest(req);
    const state = session.getState();

    // Handle incoming message
  } catch (error) {
    next(error);
  }
});
```

## Instance Level State

Instance level state is a singleton which you can use to share data across multiple instances. It comes handy when different flows are working together e.g. data is coming through 3rd party API that affect logic of voice/messages flow:


```javascript
router.post("/onMessage", async (req, res, next) => {
  try {
    const state = neru.getGlobalState();

    // Handle incoming message
  } catch (error) {
    next(error);
  }
});
```

## Use Case

For example, you can store, retrieve, and delete objects on a session using the key-value operations:

```javascript
router.post("/key-value", async (req, res, next) => {
  try {
    const session = neru.createSession();
    const state = session.getState();

    // store object
    await state.set("test_obj", { "foo": bar });

    // retrieve object
    const obj2 = await state.get("test_obj");

    // delete object
    await state.del("test_obj");

  } catch (error) {
    next(error);
  }
})
```

Or you can use instance state, and the hash table operations to persist data between sessions:

```javascript
router.post("/add-customer", async (req, res, next) => {
	try {
	  const instanceState = neru.getGlobalState();
  
	  const customer = req.body;
	  await instanceState.hset("customers", [[customer.phone , customer]]);
	} catch (error) {
	  next(error);
	}
})
  
router.get("/on-phone-call", async (req, res, next) => {
	try {
	  const instanceState = neru.getGlobalState();
	  const number = req.query.number;
	  const customer = await instanceState.hget("customers", number);
	  console.log("customer", customer);
	  res.send(customer.name);
	} catch (error) {
	  next(error);
	}
})
```

```sh
curl --location --request POST '{INSTANCE_ENDPOINT}/add-customer' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":"1",
    "name": "John",
    "phone": "101"
}'


curl --location --request GET '{INSTANCE_ENDPOINT}/on-phone-call?number=101'
```