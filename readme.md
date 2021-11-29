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
   { title:  "NoSQL Database", isbn: "0-2504-6932-"},
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

## Querying A Document
* To fetch all the documents
```javascript
db.collectionName.find()
```
* To get the documents in a formatted way
```javascript
db.collectionName.find().pretty()
```
* To fetch only specific document
```javascript
db.testdb9.findOne({"name":"zeeshan"})
```
* To use where clause methods in mongoDB. There are various operators for that
# Some common Query and Projection Operators

<table>
<thead>
	<tr>
		<th>Name</th>
		<th>Description</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/eq/#mongodb-query-op.-eq" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$eq`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches values that are equal to a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/gt/#mongodb-query-op.-gt" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$gt`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches values that are greater than a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/gte/#mongodb-query-op.-gte" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$gte`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches values that are greater than or equal to a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/in/#mongodb-query-op.-in" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$in`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches any of the values specified in an array.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/lt/#mongodb-query-op.-lt" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$lt`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches values that are less than a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/lte/#mongodb-query-op.-lte" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$lte`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches values that are less than or equal to a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/ne/#mongodb-query-op.-ne" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$ne`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches all values that are not equal to a specified value.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/nin/#mongodb-query-op.-nin" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$nin`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Matches none of the values specified in an array.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/and/#mongodb-query-op.-and" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$and`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Joins query clauses with a logical<span> </span><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap; margin: 0px;">AND`<span> </span>returns all documents that match the conditions of both clauses.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/not/#mongodb-query-op.-not" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$not`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Inverts the effect of a query expression and returns documents that do<span> </span><em style="box-sizing: border-box; margin: 0px;">not</em><span> </span>match the query expression.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/nor/#mongodb-query-op.-nor" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$nor`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Joins query clauses with a logical<span> </span><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap; margin: 0px;">NOR`<span> </span>returns all documents that fail to match both clauses.</span></div></td>
	</tr>
	<tr>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;"><a href="https://docs.mongodb.com/manual/reference/operator/query/or/#mongodb-query-op.-or" style="box-sizing: border-box; color: rgb(0, 124, 173); text-decoration: none; margin: 0px;"><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; color: rgb(0, 124, 173); font-weight: 400; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap;">$or`</a></span></div></td>
		<td><div class="leafygreen-ui-1sg2lsz" data-leafygreen-ui="td-inner-div" style="box-sizing: border-box; display: flex; -webkit-box-align: center; align-items: center; min-height: 40px; transition: all 150ms ease-in-out 0s; -webkit-box-pack: start; justify-content: flex-start;"><span style="box-sizing: border-box;">Joins query clauses with a logical<span> </span><code class="css-rjswxq e1wawog0 leafygreen-ui-1vat6ol" style="box-sizing: border-box; background-color: rgb(249, 251, 250); border: 1px solid rgb(184, 196, 194); border-radius: 3px; font-family: &quot;Source Code Pro&quot;, Menlo, monospace; font-size: unset; line-height: 24px; letter-spacing: 0px; white-space: nowrap; margin: 0px;">OR`<span> </span>returns all documents that match the conditions of either clause.</span></div></td>
	</tr>
</tbody>

</table>

<table>
<thead>
	<tr>
		<th style="text-align:center">Operation</th>
		<th style="text-align:center">Syntax</th>
		<th style="text-align:center">Example</th>
		<th style="text-align:center">RDBMS Equivalent</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td style="text-align: center">Equality</td>
		<td style="text-align: center">{&lt;key&gt;:{$eg;&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;by&quot;:&quot;tutorials point&quot;}).pretty()</td>
		<td style="text-align: center">where by = 'tutorials point'</td>
	</tr>
	<tr>
		<td style="text-align: center">Less Than</td>
		<td style="text-align: center">{&lt;key&gt;:{$lt:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;likes&quot;:{$lt:50}}).pretty()</td>
		<td style="text-align: center">where likes &lt; 50</td>
	</tr>
	<tr>
		<td style="text-align: center">Less Than Equals</td>
		<td style="text-align: center">{&lt;key&gt;:{$lte:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;likes&quot;:{$lte:50}}).pretty()</td>
		<td style="text-align: center">where likes &lt;= 50</td>
	</tr>
	<tr>
		<td style="text-align: center">Greater Than</td>
		<td style="text-align: center">{&lt;key&gt;:{$gt:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;likes&quot;:{$gt:50}}).pretty()</td>
		<td style="text-align: center">where likes &gt; 50</td>
	</tr>
	<tr>
		<td style="text-align: center">Greater Than Equals</td>
		<td style="text-align: center">{&lt;key&gt;:{$gte:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;likes&quot;:{$gte:50}}).pretty()</td>
		<td style="text-align: center">where likes &gt;= 50</td>
	</tr>
	<tr>
		<td style="text-align: center">Not Equals</td>
		<td style="text-align: center">{&lt;key&gt;:{$ne:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;likes&quot;:{$ne:50}}).pretty()</td>
		<td style="text-align: center">where likes != 50</td>
	</tr>
	<tr>
		<td style="text-align: center">Values in an array</td>
		<td style="text-align: center">{&lt;key&gt;:{$in:[&lt;value1&gt;, &lt;value2&gt;,……&lt;valueN&gt;]}}</td>
		<td style="text-align: center">db.mycol.find({&quot;name&quot;:{$in:[&quot;Raj&quot;, &quot;Ram&quot;, &quot;Raghu&quot;]}}).pretty()</td>
		<td style="text-align: center">Where name matches any of the value in :[&quot;Raj&quot;, &quot;Ram&quot;, &quot;Raghu&quot;]</td>
	</tr>
	<tr>
		<td style="text-align: center">Values not in an array</td>
		<td style="text-align: center">{&lt;key&gt;:{$nin:&lt;value&gt;}}</td>
		<td style="text-align: center">db.mycol.find({&quot;name&quot;:{$nin:[&quot;Ramu&quot;, &quot;Raghav&quot;]}}).pretty()</td>
		<td style="text-align: center">Where name values is not in the array :[&quot;Ramu&quot;, &quot;Raghav&quot;] or, doesn’t exist at all</td>
	</tr>
</tbody>
</table>

**AND in MongoDB**
```javascript
Example
Following example will show all the tutorials written by 'github' and whose title is 'MongoDB Overview'.

> db.mycol.find({$and:[{"by":"github"},{"title": "MongoDB Overview"}]}).pretty()
{
	"_id" : ObjectId("5dd4e2cc0821d3b44607534c"),
	"title" : "MongoDB Overview",
	"description" : "MongoDB is no SQL database",
	"by" : "github",
	"url" : "http://www.tutorialspoint.com",
	"tags" : [
		"mongodb",
		"database",
		"NoSQL"
	],
	"likes" : 100
}
```

**OR in MongoDB**
```javascript
Example
Following example will show all the tutorials written by 'github' or whose title is 'MongoDB Overview'.

>db.mycol.find({$or:[{"by":"github"},{"title": "MongoDB Overview"}]}).pretty()
{
   "_id": ObjectId(7df78ad8902c),
   "title": "MongoDB Overview", 
   "description": "MongoDB is no sql database",
   "by": "github",
   "tags": ["mongodb", "database", "NoSQL"],
   "likes": "100"
}
```

```javascript
Using AND and OR Together
Example
The following example will show the documents that have likes greater than 10 and whose title is either 'MongoDB Overview' or by is 'github'. Equivalent SQL where clause is 'where likes>10 AND (by = 'tutorials point' OR title = 'MongoDB Overview')'

>db.mycol.find({"likes": {$gt:10}, $or: [{"by": "github"},
   {"title": "MongoDB Overview"}]}).pretty()
{
   "_id": ObjectId(7df78ad8902c),
   "title": "MongoDB Overview", 
   "description": "MongoDB is no sql database",
   "by": "github",
   "tags": ["mongodb", "database", "NoSQL"],
   "likes": "100"
}
```

`NOR in MongoDB`
Syntax
To query documents based on the NOT condition, you need to use $not keyword. Following is the basic syntax of NOT −
```javascript
Following example will retrieve the document(s) whose first name is not "Radhika" and last name is not "Christopher"

> db.empDetails.find(
	{
		$nor:[
			40
			{"First_Name": "Radhika"},
			{"Last_Name": "Christopher"}
		]
	}
)
```
```javascript
Following example will retrieve the document(s) whose age is not greater than 25

> db.empDetails.find( { "Age": { $not: { $gt: "25" } } } )
{
	"_id" : ObjectId("5dd6636870fb13eec3963bf7"),
	"First_Name" : "Fathima",
	"Last_Name" : "Sheik",
	"Age" : "24",
	"e_mail" : "Fathima_Sheik.123@gmail.com",
	"phone" : "9000054321"
}
```

# **MongoDB Update Methods**
1. update
2. save
3. findOneAndUpdate()
4. updateOne() 
5. updateMany() 
```javascript
MongoDB Update() Method
The update() method updates the values in the existing document
>db.mycol.update({'title':'MongoDB Overview'},{$set:{'title':'New MongoDB Tutorial'}})
By default, MongoDB will update only a single document. To update multiple documents, you need to set a parameter 'multi' to true.

>db.mycol.update({'title':'MongoDB Overview'},
   {$set:{'title':'New MongoDB Tutorial'}},{multi:true})

```
```javascript
MongoDB updateOne() method
This methods updates a single document which matches the given filter.

Syntax
The basic syntax of updateOne() method is as follows −

>db.COLLECTION_NAME.updateOne(<filter>, <update>)
Example
> db.empDetails.updateOne(
	{First_Name: 'Radhika'},
	{ $set: { Age: '30',e_mail: 'radhika_newemail@gmail.com'}}
)
{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 0 }
>
```

```javascript
MongoDB updateMany() method
The updateMany() method updates all the documents that matches the given filter.
Syntax
The basic syntax of updateMany() method is as follows −

>db.COLLECTION_NAME.update(<filter>, <update>)
Example
> db.empDetails.updateMany(
	{Age:{ $gt: "25" }},
	{ $set: { Age: '00'}}
)
{ "acknowledged" : true, "matchedCount" : 2, "modifiedCount" : 2 }
```
# The remove() Method
MongoDB's remove() method is used to remove a document from the collection. remove() method accepts two parameters. One is deletion criteria and second is justOne flag.

deletion criteria − (Optional) deletion criteria according to documents will be removed.

justOne − (Optional) if set to true or 1, then remove only one document.
```javascript
Following example will remove all the documents whose title is 'MongoDB Overview'.

>db.mycol.remove({'title':'MongoDB Overview'})
```
```javascript
Remove Only One
If there are multiple records and you want to delete only the first record, then set justOne parameter in remove() method.

>db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)
```
```javascript
Remove All Documents
If you don't specify deletion criteria, then MongoDB will delete whole documents from the collection. This is equivalent of SQL's truncate command.

> db.mycol.remove({})
```

