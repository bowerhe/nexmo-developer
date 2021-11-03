---
title: List State Operations
description: How to use the State provider's list operations
navigation_weight: 3
---

# List State Operations

The State provider has list operations for storing state.

## Insert Elements at the List's Start

Using a list name, you can add an element to a list at the start.

### Method Signature
```javascript
lpush<T>(list: string, value: T)
```

### Inserting Elements at the List's Start

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/list-start-push
```

## Insert Elements at the List's End

Using a list name, you can add an element to a list at the end.

### Method Signature
```javascript
rpush<T>(list: string, value: T)
```

### Inserting Elements at the List's End

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/list-end-push
```

## Get a List's Length

Using a list name, you can get the length of the list.

### Method Signature
```javascript
llen(list: string)
```

### Getting a List's Length

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/list-length
```

## Get a List Elements With a Range

Using a list name and a range, you can get the elements in the specified range.

### Method Signature
```javascript
lrange<T>(list: string, startPos: number, endPos: number)
```

### Getting a List Elements With a Range

```tabbed_content
source: _tutorials_tabbed_content/neru/code-snippets/state/list-range
```