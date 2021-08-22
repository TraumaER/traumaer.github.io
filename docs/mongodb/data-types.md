---
layout: default 
title: Data Types 
parent: MongoDB 
nav_order: 2
---

# Data Types

Documents can be thought of as "JSON-like".

## Types

```javascript
// Null
let foo = {x: null}
// Boolean
let foo = {x: true}
// Number
let foo = {w: 3.14, x: 3, y: NumberInt("3"), z: NumberLong("3")}
// String
let foo = {x: "foobar"}
// Date
let foo = {x: new Date()}
// Regular Expression
let foo = {x: /foobar/i}
// Array
let foo = {x: ["a", "b", "c"]}
// Embedded Document
let foo = {x: {y: "bar"}}
// Object ID
let foo = {x: ObjectId()}
// Binary Data
// Code
let foo = {x: function(){/* ... */}}
```

### Dates

* Make sure to use `new Date()` instead of `Date()` which only returns a string not a date object.
* Dates are stored in ms since epoch.

### Arrays

* Can be used for ordered and unordered operations
* Can contain different data types `let foo = ["pie", 3.14]`
* Can contain any of the supported data types
* MongoDB can "reach" in and perform operations. Can even index on contents of an array

### Embedded Documents

* Like arrays MongoDB can reach in and perform operations and indexing.

### Object IDs

* Unique `_id` per document within a collection. Two collections could both have documents with `_id: 123`
* Generated with 3 parts
  * timestamp
  * random value
  * counter starting at random value (avoids collisions across machines)
* First nine bytes of the id guarantee uniqueness across machines and processes for a single second
* 