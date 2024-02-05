### 1. Update Document:
   - `updateOne()`: Updates a single document based on a filter.
   - `updateMany()`: Updates multiple documents based on a filter.

   **Example:**
   Suppose you have a collection named `users` with documents like this:
   ```json
   { "_id": 1, "name": "John", "age": 25, "status": "active" }
   { "_id": 2, "name": "Jane", "age": 30, "status": "inactive" }
   ```

   Now, let's update the status of a single document and multiple documents:

   ```javascript
   // Update a single document
   db.users.updateOne({ "_id": 1 }, { $set: { "status": "inactive" } });

   // Update multiple documents
   db.users.updateMany({ "age": { $gte: 30 } }, { $set: { "status": "active" } });
   ```

   After these updates, the collection would look like:
   ```json
   { "_id": 1, "name": "John", "age": 25, "status": "inactive" }
   { "_id": 2, "name": "Jane", "age": 30, "status": "active" }
   ```

### 2. Update with Aggregation Pipeline:
   - `updateOne()` and `updateMany()` with aggregation pipeline: Allows for more complex updates using aggregation expressions.

   **Example:**
   Let's say you want to increment the age of users by 5, but only for those whose status is "active":

   ```javascript
   // Update a single document using aggregation pipeline
   db.users.updateOne(
     { "name": "John" },
     [
       { $set: { "age": { $add: ["$age", 5] } } }
     ]
   );

   // Update multiple documents using aggregation pipeline
   db.users.updateMany(
     { "status": "active" },
     [
       { $set: { "age": { $add: ["$age", 5] } } }
     ]
   );
   ```

   After these updates, the collection would reflect the incremented ages.

### 3. Replace Document:
   - `replaceOne()`: Replaces a single document based on a filter.

   **Example:**
   Replace the document with `_id` equal to 1 with a new document:

   ```javascript
   db.users.replaceOne(
     { "_id": 1 },
     { "name": "John Doe", "age": 28, "status": "active" }
   );
   ```

   After this update, the collection would have the following document:
   ```json
   { "_id": 1, "name": "John Doe", "age": 28, "status": "active" }
   ```

### 4. Upsert:
   - `update()` with the `upsert` option: Updates an existing document or inserts a new one if no match is found.

   **Example:**
   Update a document if it exists; otherwise, insert a new one:

   ```javascript
   db.users.update(
     { "name": "Bob" },
     { $set: { "age": 22, "status": "inactive" } },
     { upsert: true }
   );
   ```

   If a document with the name "Bob" exists, it will be updated. If not, a new document will be inserted.

### 5. Update If Current:
   - `update()` with the `w` (write concern) option: Updates the document only if it hasn't been modified since the last read.

   **Example:**
   Suppose you read a document, and then you want to update it only if it hasn't been modified since the read:

   ```javascript
   var doc = db.users.findOne({ "name": "Jane" });
   
   db.users.update(
     { "name": "Jane", "_id": doc._id },
     { $set: { "age": 31 } },
     { w: doc }
   );
   ```

   In this example, the update will only succeed if the document hasn't been modified since it was read. The `w` option here ensures this.

## 6. Atomic Update Operators :

1. **`$set`: Sets the value of a field in a document.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $set: { status: "active", updatedAt: new Date() } }
   );
   ```
   This example sets the `status` field to "active" and adds or updates the `updatedAt` field with the current date for the document with `_id` equal to 1.

2. **`$unset`: Removes a field from a document.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $unset: { status: "", updatedAt: "" } }
   );
   ```
   This example removes the `status` and `updatedAt` fields from the document with `_id` equal to 1.

3. **`$inc`: Increments the value of a field.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $inc: { quantity: 5 } }
   );
   ```
   This example increments the `quantity` field by 5 for the document with `_id` equal to 1.

4. **`$mul`: Multiplies the value of a field by a specified number.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $mul: { price: 1.1 } }
   );
   ```
   This example multiplies the `price` field by 1.1 for the document with `_id` equal to 1.

5. **`$rename`: Renames a field.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $rename: { "oldName": "newName" } }
   );
   ```
   This example renames the field from `oldName` to `newName` for the document with `_id` equal to 1.

6. **`$min`: Only updates the field if the specified value is less than the existing value.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $min: { score: 90 } }
   );
   ```
   This example updates the `score` field to 90 only if the existing value is greater than 90 for the document with `_id` equal to 1.

7. **`$max`: Only updates the field if the specified value is greater than the existing value.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $max: { temperature: 100 } }
   );
   ```
   This example updates the `temperature` field to 100 only if the existing value is less than 100 for the document with `_id` equal to 1.

8. **`$currentDate`: Sets the value of a field to the current date or time.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $currentDate: { lastModified: true } }
   );
   ```
   This example sets the `lastModified` field to the current date for the document with `_id` equal to 1.

9. **`$addToSet`: Adds elements to an array only if they do not already exist in the set.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $addToSet: { tags: "newTag" } }
   );
   ```
   This example adds the "newTag" to the `tags` array if it doesn't already exist for the document with `_id` equal to 1.

10. **`$push`: Adds an element to an array.**
   ```javascript
   db.collection.updateOne(
     { _id: 1 },
     { $push: { comments: "New comment" } }
   );
   ```
   This example adds "New comment" to the `comments` array for the document with `_id` equal to 1.

## 7. Array update operators

### 1. `$pop`

The `$pop` operator removes the first or last element from an array.

#### Example:

Suppose you have a document in a collection like this:

```json
{
  "_id": 1,
  "colors": ["red", "green", "blue"]
}
```

To remove the last element from the "colors" array, you can use `$pop` as follows:

```javascript
db.collection.updateOne(
  { "_id": 1 },
  { "$pop": { "colors": 1 } }
);
```

After this update, the document will be:

```json
{
  "_id": 1,
  "colors": ["red", "green"]
}
```

Here, `1` signifies removing the last element, and `-1` would remove the first element.

### 2. `$pull`

The `$pull` operator removes all occurrences of a specified value from an array.

#### Example:

Suppose you have a document like this:

```json
{
  "_id": 2,
  "fruits": ["apple", "orange", "banana", "orange", "grape"]
}
```

To remove all occurrences of "orange" from the "fruits" array, you can use `$pull` as follows:

```javascript
db.collection.updateOne(
  { "_id": 2 },
  { "$pull": { "fruits": "orange" } }
);
```

After this update, the document will be:

```json
{
  "_id": 2,
  "fruits": ["apple", "banana", "grape"]
}
```

### 3. `$push`

The `$push` operator adds an element to the end of an array.

#### Example:

Suppose you have a document like this:

```json
{
  "_id": 3,
  "numbers": [1, 2, 3]
}
```

To add the number `4` to the end of the "numbers" array, you can use `$push` as follows:

```javascript
db.collection.updateOne(
  { "_id": 3 },
  { "$push": { "numbers": 4 } }
);
```

After this update, the document will be:

```json
{
  "_id": 3,
  "numbers": [1, 2, 3, 4]
}
```

### 4. `$pullAll`

The `$pullAll` operator removes all occurrences of specified values from an array.

#### Example:

Suppose you have a document like this:

```json
{
  "_id": 4,
  "languages": ["JavaScript", "Java", "Python", "Java", "C++"]
}
```

To remove all occurrences of "Java" and "C++" from the "languages" array, you can use `$pullAll` as follows:

```javascript
db.collection.updateOne(
  { "_id": 4 },
  { "$pullAll": { "languages": ["Java", "C++"] } }
);
```

After this update, the document will be:

```json
{
  "_id": 4,
  "languages": ["JavaScript", "Python"]
}
```
