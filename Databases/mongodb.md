## MonogDB

- **NOSQL** database
- **Collections** - Similar to tables
- **Documents** - Similar to **rows** in SQL (Maximum Size of each **Document** is `16MB`)
- It uses **BSON(Binary JavaScript Object Notation)** data format to store data.
- Data are stored in **key/value pair** similar to JSON.
- **MongoDB** is very flexible which means **Documents** inside the **Collections** can have different fields.

- **db.myCol.find()** - Returns all the documents in the collections.
- **db.myCol.findOne()** - Returns the one document which matches the given condition.
- **db.myCol.insertOne()**
- **db.myCol.insertMany()**
- **db.myCol.updateOne()**
- **db.myCol.updateMany()**
- **db.myCol.replaceOne()**
- **db.myCol.replaceMany()**
- **db.myCol.deleteMany()**
- **db.myCol.deleteOne()**
- **db.version()**
- **Cluster** is like a container in MongoDB, which contains multiple databases.
- **db.dropDatabase()** - To drop current database in use.
- **db.getName()** - To get the name of current database in use.

- There are various query operators used in MongoDB to filter documents:-

  1. `$lte` - It is used to query the documents where value of the field is `<=` of a specified value.
     - **Syntax** - `{field: { $lte: value}}`
  2. `$gte` - Used to query the documents where value of the field is `>=` of a specified value.
     - **Syntax** - `{field: { $gte: value}}`
  3. `$lt` - Used to query the documents where value of the field is `<` of a specified value.
     - **Syntax** - `{field : {$lt : value}}`
  4. `$gt` - Used to query the documents where value of the field is `>` of a specified value.
     - **Syntax** - `{field : {$gt : value}}`
  5. `$or` - Used to query documents based on any of the conditions passed in an array is satisfied.
     - **Syntax** - `{$or : [<condition1>, <condition2>, ...]}`
  6. `$set` - Used to set(replace/update) value of a field in a document or create a new field.
     - **Syntax** - `{$set: { <field1>: <value1>, ... }}`
  7. `$ne` - Used to query documents which are not equal to given value.
     - **Syntax** - `{field : {$ne : value}}`
  8. `$in` - Used to query documents where mentioned field has the any of the values specified in an array using the `in` operator.
     - **Syntax** - `{field : {$in : [<value1>, <value2>]}}`
  9. `$nin` - negation of `in` operator.
     - **Syntax** - `{field : {$nin : [<value1>, <value2>]}}`

- MongoDB's query mechanism doesn't allow to group or transform the returned data. We have _aggregation operations_ for performing such actions(grouping data, sorting data into a specific order, restructuring returned data etc). These operations can be accessed via _aggregation pipelines_(A series of operations that process data documents sequentially).

- To create aggregation pipeline `aggregate()` method is used.
