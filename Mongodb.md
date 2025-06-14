# Mongodb
Mongodb is a document base database used for scalability and flexibility.MongoDB stores data records as documents (specifically BSON documents) which are gathered together in collections. A database stores one or more collections of documents.
* By default, a collection does not require its documents to have the same schema.

## Structure of Mongodb
```text
---cluster
    |
    |----database
            |
            |----collections
                    |
                    |----documents
```
A record in MongoDB is a document, which is a data structure composed of field and value pairs. MongoDB documents are similar to JSON objects. The values of fields may include other documents, arrays, and arrays of documents.
* Cluster-A Cluster is the top-level MongoDB deployment. It can be a single server or multiple servers working together (replica sets, sharded clusters).
* Database-A Database is a container for collections. It’s like a folder where you store your data.
* collection-A Collection is like a table in relational databases — it holds multiple documents.
* Document-A Document is a single record stored in a collection — like a row in SQL, but stored as a JSON-like object (BSON)
# View
Views in MongoDB are read-only, and they return a collection in much the same way as a find() or aggregation() would. They are similar to views in relational databases.
## Restrictions
* You must create views in the same database as the source collection.
* A view definition pipeline cannot include the $out or the $merge stage.
* This restriction also applies to embedded pipelines, such as pipelines used in $lookup or $facet stages.
* You cannot rename a view once it is created.
You cannot rename a view once it is created.
# Commands
* show dbs- shows all database's in a cluster
* use db_nam- select particular database from cluster to perform operations


# CRUD operations on Mongodb database
## Create
Select the database using use Commands.To insert single document 
```MongoDB shell
db.inventory.insertOne(
   { item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } }
)
```
* db is the database selected.
* inventory is the collection name in which document is to be created.
* insertOne create's single document.
* if the document does not specify an _id field, MongoDB adds the _id field with an ObjectId value to the new document

To retrieve the document that you just inserted, query the collection
```MongoDB shell
db.inventory.find( { item: "canvas" } )
```

To insert multiple documents.
```MongoDB shell
db.inventory.insertMany([
   { item: "journal", qty: 25, tags: ["blank", "red"], size: { h: 14, w: 21, uom: "cm" } },
   { item: "mat", qty: 85, tags: ["gray"], size: { h: 27.9, w: 35.5, uom: "cm" } },
   { item: "mousepad", qty: 25, tags: ["gel", "blue"], size: { h: 19, w: 22.85, uom: "cm" } }
])
```

* If the collection does not currently exist, insert operations will create the collection.
* All write operations in MongoDB are atomic on the level of a single document.


## Read
To retrieve the document that you just inserted, query the collection
```MongoDB shell
db.inventory.find( { item: "canvas" } )
```
* find retrieve document
* if no paramaters are given find list out all documents in collection

### Specify Equality Condition
The following example selects from the inventory collection all documents where the status equals "D":
```MongoDB shell
db.inventory.find( { status: "D" } )
```

### Specify Conditions Using Query Operators
A query filter document can use the query operators to specify conditions in the following form:
```MongoDB shell
{ <field1>: { <operator1>: <value1> }, ... }
```
The following example retrieves all documents from the inventory collection where status equals either "A" or "D":

```MongoDB shell
db.inventory.find( { status: { $in: [ "A", "D" ] } } )
```
Although you can express this query using the $or operator, use the $in operator rather than the $or operator when performing equality checks on the same field.

### Specify AND Conditions
The following example retrieves all documents in the inventory collection where the status equals "A" and qty is less than ($lt) 30:
```MongoDB shell
db.inventory.find( { status: "A", qty: { $lt: 30 } } )
```
### Specify OR Conditions
The following example retrieves all documents in the collection where the status equals "A" or qty is less than ($lt) 30:
```MongoDB shell
db.inventory.find( { $or: [ { status: "A" }, { qty: { $lt: 30 } } ] } )
```
### Specify AND as well as OR Conditions
In the following example, the compound query document selects all documents in the collection where the status equals "A" and either qty is less than ($lt) 30 or item starts with the character p:
```MongoDB shell
db.inventory.find( {
     status: "A",
     $or: [ { qty: { $lt: 30 } }, { item: /^p/ } ]
} )
```

## Update
To update a document, MongoDB provides update operators, such as $set, to modify field values.

To use the update operators, pass to the update methods an update document of the form:
{
  <update operator>: { <field1>: <value1>, ... },
  <update operator>: { <field2>: <value2>, ... },
  ...
}
*  $set, will create the field if the field does not exist.

To update single document 
The following example uses the db.collection.updateOne() method on the inventory collection to update the first document where item equals "paper":

```MongoDB shell
db.inventory.updateOne(
   { item: "paper" },
   {
     $set: { "size.uom": "cm", status: "P" },
     $currentDate: { lastModified: true }
   }
)
```
* uses the $set operator to update the value of the size.uom field to "cm" and the value of the status field to "P"
* uses the $currentDate operator to update the value of the lastModified field to the current date. If lastModified field does not exist, $currentDate will create the field


## Delete
To delete first occurence of single document
```MongoDB shell
db.inventory.deleteOne( { status: "D" } )
```

To delete multiple document


```MongoDB shell
db.inventory.deleteMany( { status: "D" } )
```

# Aggregation Pipeline
An aggregation pipeline consists of one or more stages that process documents:
* Each stage performs an operation on the input documents. For example, a stage can filter documents, group documents, and calculate values.
* The documents that are output from a stage are passed to the next stage.
* An aggregation pipeline can return results for groups of documents. For example, return the total, average, maximum, and minimum values.


