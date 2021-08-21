# Concepts

## Document

* Core of MongoDB
* Analogous to a row in a relational database
* Ordered set of keys and values

### Keys

* Must not contain the `\0` (the `null` character)
* Should not use `.` or `$`
* Type and case sensitive
  ```js
  let allTheseAreConsideredUnique = [
    {"count" : 5},
    {"count" : "5"}, 
    {"count" : 5}, 
    {"Count" : 5}
  ]
  ```
* Duplicate keys are not allowed
* **_Best practice_** keep characters to `[a-zA-Z_]`

### Values

* Can be several types including another document

## Collections

* Group of documents
* Analogous to a table in a relational database

### Dynamic Schemas

* Documents within a collection don't have to have the same "shape"
* **_Best practice_** Keep the schemas within a collection the same.
  * Much faster to fetch a list of collections instead of documents and filtering.
* Schema begins to be enforced when indexes are introduced.
* Schemas can be enforced by MongoDB's documentation validation, and object document mapping libaries.

### Naming

* Must not contain the `\0` (the `null` character)
* Should not start with `system`
* Should not use `$`
* **_Best practice_** keep characters to `[a-zA-Z_]`

### Subcollections

* Namespacing collections can be useful `blog`, `blog.posts`, `blog.authors`, etc.
* No actual relationship between collections and their children
* Some drivers support syntax sugar for subcollections. E.g. `db.blog.posts`

## Databases

* Group of Collections
* Single instance of MongoDB can host several Databases

### Naming

* Even more restrictive than Collections or Document keys
* Case insensitive
* Max of 64 bytes
* **_Best practice_** keep characters to `[a-zA-Z_]`

### Reserved Names

* `admin`
* `local`
* `config`

### Fully qualifying collection name

* Considered namespacing
* E.g. `blog.posts` Collection in `cms` Database would be `cms.blog.posts`