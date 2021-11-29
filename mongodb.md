# **Mongodb Basic Queries**
* To create a database
```csharp
use testdb
```

* To switch from one database to another database
```csharp
use databseName
```
* In `mongodb` there is a concept of `collections` and `documents`
`document` is just like a `record` of one person and the `collection` contains records of various persons just like a `table` you can compare a `document` with a `row` in `MYSQL` `database` and a `collection` with `table`
* To insert a `document` in `mongodb` we have to insert the document in a `collection`
* In `mongodb` if we insert a document and if there is no collection `mongodb` will automatically a collection when we `insert` the first `document`
* To insert a document steps 
1. switch to that particular database 
```csharp
db test
```
2. insert the document
```csharp
db.collectionName.insert({"name":"Ahmad","Rollno":"123"})
```
Output of above query
```csharp
WriteResult({ "nInserted" : 1 })
```
* If we want to insert multiple records
```csharp
db.post.insert([
	{
		title: "MongoDB Overview",
		description: "MongoDB is no SQL database",
		url: "http://www.tutorialspoint.com",
		tags: ["mongodb", "database", "NoSQL"],
		likes: 100
	},
	{
	title: "NoSQL Database",
	description: "NoSQL database doesn't have tables",
	url: "http://www.tutorialspoint.com",
	tags: ["mongodb", "database", "NoSQL"],
	likes: 20,
	comments: [
		{
			user:"user1",
			message: "My first comment",
			dateCreated: new Date(2013,11,10,2,35),
			like: 0
		}
	]
}
])
```
The output of above query
```csharp
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 2,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
```
* In mongoDB There are two commands for inserting a document
`save` and `insert`
`save behaves differently if it is passed with an "_id" parameter.

For save, If the document contains `_id`, it will `upsert` querying the collection on the _id field, If not, it will insert.`


`MongoDB insertMany() Method – db.Collection.insertMany()
`
The insertMany() method inserts one or more documents in the collection. It takes array of documents to insert in the collection.
[insertmany](https://www.mongodbtutorial.org/mongodb-crud/mongodb-insertmany/)
```javascript
db.books.insertMany([
   { title:  "NoSQL Distilled", isbn: "0-4696-7030-4"},
   { title:  "NoSQL in 7 Days", isbn: "0-4086-6859-8"},
   { title:  "NoSQL Database", isbn: "0-2504-6932-4"},
]);
```


`MongoDB insertOne() Method – db.Collection.insertOne()
`
In MongoDB, insertOne() method inserts a document into the collection. This method inserts only one document at a time
[insertOne](https://www.mongodbtutorial.org/mongodb-crud/mongodb-insertmany/)
```javascript
db.books.insertOne({ 
    title: 'MongoDB insertOne',
    isbn: '0-7617-6154-3'
});
```

