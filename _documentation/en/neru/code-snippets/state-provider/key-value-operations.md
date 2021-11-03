---
title: Key-Value State Operations
description: How to use the State provider's key-value operations
navigation_weight: 1
---

# Key-Value State Operations

The State provider has key-value operations for storing state.

## Set a Value

Using a key, you can store a value for retrieval later.

### Method Signature
```javascript
set<T>(key: string, value: T)
```

### Setting a Value

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/set-value
```

## Get a Value

Using a key, you can fetch a value previously stored.

### Method Signature
```javascript
get<T>(key: string)
```

### Getting a Value

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/get-value
```

## Delete a Value

Using a key, you can delete a value previously stored.

### Method Signature
```javascript
del<T>(key: string)
```

### Deleting a Value

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/del-value
```