# mongodb

## Installation 
Download and Install MongoDB Server, Shell and Database Tools from [here](https://www.mongodb.com/try/download/community-edition).

## Installation Verification
To verify mongodb server installation, run the following command in your terminal : 
```
mongod --version
```
It should return version. In case, if it doesn't return anything, then add mongodb bin path to system environment variables path, and then try again.

To verify mongodb shell installation, run the following command in your terminal : 
```
mongosh
```
Shell should be started. You can verify if everything is correct by typing command in mongosh to show databases.
```
show dbs
```

## Databases and Collections Management in MongoDB
Use the mongosh for database management from local host. Type the following commands to do following tasks : 

1. **Show Database** 
```
show dbs;
```
2. **Create Database**
```
use <database-name>;
```
3. **Drop Database**
```
db.dropDatabase();
```
4. **Show Collections**
```
show collections;
```
5. **Create Collection** 
```
db.createCollection('<collection-name>');
```
6. **Drop Collection**
```
db.<collection-name>.drop();
```

## Insert Operations in MongoDB

1. **Insert One Document**
```
db.<collection-name>.insertOne({ field1: value1, field2: value2, ... });
```
2. **Insert Multiple Documents**
```
db.collectionName.insertMany([
    { field1: value1, field2: value2, ... },
    { field1: value1, field2: value2, ... },
    { field1: value1, field2: value2, ... },
]);
```
Always use single or double quotes for fields. 
<br>
Ordered Inserts  : MongoDB stops on first error.
<br>
Unordered Inserts : MongoDB keeps processing after encounting an error.

## Read Operations in MongoDB

1. **Finding Document**
```
db.<collection-name>.find({key:value});
db.<collection-name>.findOne({key:value});
```
2. **Importing JSON**
<br>
To import documents from json file, exit mongosh and type the following commands in your terminal: 
```
mongoimport jsonfile.json -d database_name -c collection_name
mongoimport jsonfile.json -d database_name -c collection_name --jsonArray
```
Forexample: 
```
C:\Users\US593>mongoimport C:\Users\US593\OneDrive\Desktop\import_json\products.json -d shop -c products

# if documents in json file are in array
C:\Users\US593>mongoimport C:\Users\US593\OneDrive\Desktop\import_json\sales.json -d shop -c sales --jsonArray
```
3. **Exporting JSON**
<br>
To export documents to json file, type the following commands in your terminal:
```
mongoexport -d database_name -c collection_name -o file_name
```
Forexample: 
```
mongoexport  -d shop -c sales -o C:\Users\US593\OneDrive\Desktop\import_json\sales1.json
```
4. **Comparison Operators**
```
$eq     $ne     $gt     $gte
$lt     $lte    $in     $nin
```
```
db.<collection-name>.find({'fieldname':{$operator:value}});
```
Forexample: 
```
db.products.find({'price':{$eq:699}});
db.categories.find({'price':{$in:[249,129,39]}});
```
5. **Cursor Methods**
```
db.<collection-name>.find({'fieldname':{$operator:value}})>count();
db.<collection-name>.find({'fieldname':{$operator:value}})>limit(3);
db.<collection-name>.find({'fieldname':{$operator:value}})>limit(3).skip(2);
db.<collection-name>.find({'fieldname':{$operator:value}})>limit(5).sort({'fieldname':1 or -1}); 
```
6. **Logical Operators**
```
$and        $or         $not        $nor
```


