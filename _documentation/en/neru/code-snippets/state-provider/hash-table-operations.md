---
title: Hash Table State Operations
description: How to use the State provider's hash table operations
navigation_weight: 2
---

# Hash Table State Operations

The State provider has hash table operations for storing state.

## Set Hash Table Values

Using a hash table name, you can store key-value pairs for retrieval later.

### Method Signature
```javascript
hset(htable: string, keyValuePairs: [string, string][])
```

### Setting Hash Table Values

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-set
```

## Get a Hash Table Value

Using a hash table name and key, you can fetch a value.

### Method Signature
```javascript
hget<T>(htable: string, key: string)
```

### Getting a Hash Table Value

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-get
```

## Getting Multiple Hash Table Values

Using a hash table name and an array of keys, you can fetch multiple values.

### Method Signature
```javascript
hmget<T>(htable: string, keys: string[])
```

### Getting Multiple Hash Table Values

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-multiple-get
```

## Getting All Hash Table Values

Using a hash table name, you can fetch all the stored values.

### Method Signature
```javascript
hvals<T>(htable: string)
```

### Getting All Hash Table Values

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-values
```

## Get a Hash Table

Using a hash table name, you can fetch the entire hash table.

### Method Signature
```javascript
hgetall<T>(htable: string)
```

### Getting a Hash Table

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-get-all
```

## Check a Hash Table Key Exists

Using a hash table name and key, you can check if a key exists on a hash table.

### Method Signature
```javascript
hexists(htable: string, key: string)
```

### Checking a Hash Table Key Exists

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-exists
```

## Delete a Hash Table Value

Using a hash table name and key, you can delete a value.

### Method Signature
```javascript
hdel(htable: string, key: string)
```

### Deleting a Hash Table Value

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/ht-del
```

> You can delete an entire table by using the [`del`](/neru/code-snippets/state-provider/key-value-operations#delete-a-value) function.