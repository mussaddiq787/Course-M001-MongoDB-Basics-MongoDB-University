#insert error

MongoDB can store duplicate documents in the same collection, as long as their _id values are different.

This is true.

The only value that is being checked for duplicates on insertion by default is the _id value, since it serves as a unique identifier for the document.

If a document is inserted without a provided _id value, then that field and value will be automatically generated for the inserted document before insertion.

This is true.

MongoDB ensures that each inserted document has a unique _id value.

MongoDB can always store duplicate documents in the same collection.

This is false.

While documents that have duplicate content are allowed, they still have to have unique _id values.

There is no way to ensure that duplicate records are not stored in MongoDB.

This is false.

You can place additional rules on which documents can and cannot be inserted into a collection using MongoDB's schema validation functionality.

If a document is inserted without a provided _id value, then that document will fail to be inserted and cause a write error.

This is false.

MongoDB will automatically add an _id field and assign it an ObjectId type value when inserting such documents into a collection.