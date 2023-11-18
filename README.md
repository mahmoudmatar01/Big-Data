# Big Data, NoSQL, MongoDB, and Hadoop Overview

### Big Data Definition:
- is a collection of data that is huge in volume, yet growing exponentially with time.
- it is a data with so large size and complexity that none of traditional data mangement tools can 
  store it or process it efficiently .
- Bigdata is also a data but with huge size .


### Characteristics Of Data :  
- **Velocity :-** Data velocity refers to the speed in which data is generated distributed and collected .
- **Variety  :-** refers to the different sources in which data is collected from .
- **Volume   :-** refers to the size of data sets that an organization has collected to be analyzed and proccessed 
- **Veracity :-** the truth or occuracy of data and information assets, which often determines executive-level confidence 


### Types Of Big Data :
- **Structured**                          - **UnStructured**


### Structured Data :
- is usually text files, with defined column titles and data in rows. such data can easily be visualized in form of charts  and can be processed using data mining tools .


### Unstructured :
- Unstructured data can be anything like video file, image file, Pdf, emails etc. what does these files have in common, nothing.
- Structured information can be extracted from unstructured data, but the process is time consuming. And as more and more modern data is unstructured, there was a need to have somthing to store such data for growing applications, hence setting path for NoSQL


### NoSQL Database :
- is a non-relational data mangement system, that doesn't requie a fixed schema, easy to scale.
- The major purpose of using a NoSQL database is for distributed data stores with humomgous data storage needs.
- NoSQL is used for Big data and real-time Web apps .
- For example, Companies like Twitter, Facebook and Google Collect terabytes of user data every single day.


Why need to NoSQL :
* Handle large volumes of data (big data)
* Scalable by partitioning (Sharding) and (replication)
* Distributed, fault-tolerant architecture
* Flexible schema -- no fixed schema or structure 


### Scalability :
NoSQL database offer an efficient architexture that scales out **horizontally**. This means that increasing storage and compute capacity merely a metter of adding more commodity servers or cloud instances. in addition, the open-source nature of NoSQL makes it much more cost-effective that a traditional relational database .


### Type Of NoSQL :
- Document stores
- Key-value stores
- Column-based 
- Graph database


### NoSQL Document Type :
- Store data in document similar to JSON object.
- Document contains pairs of fields and values.
- The values can typically be a variety of type including things like string, number, booleans, array, or objects .
- Main application based on this store :   - **MongoDB**              - **CouchDB**


### Mongo DB :
- Is a NoSQL database .
- Store the data in form of document.
- MongoDB is a document oriented database where it stores data in collections instead of tables .
- The best part of MongoDB is That the drivers are available for almost all the popular programming languages .


### MongoDB Data Model :
- **Database → Collection → Document → Fields**


### Collection : 
- Organization of documents 
- A Collection includes documents 


### Documents & Fields :
- Structure of Json-like document 
- The value of field => Native data type - Arrays - Other documents 


#### SQL vs NoSQL (MongoDB) Terms/Concepts:
| SQL Terms/Concepts | MongoDB Terms/Concepts   |
|--------------------|--------------------------|
| Database           | Database                 |
| Table              | Collection               |
| Rows               | Document                 |
| Columns            | Fields                   |

### Install MongoDB :
- Download and install suitable package for each platform [Windows, Linux, Mac OSX, Solaries]
- Folder created e.g. C:\mongodb
- Go to bin of installation folder
- Run mongod.exe then mongo.exe
- Make sure that mongo.exe (MongoDB Server) is running without any problems before running mongo.exe



### Commands :
- To check your currently selected database use the command db
```javascript
db
```
```bash 
output=> mydb
```


* if you want to check your database list, then use the command show dbs.
```javascript
 shows dbs
```
```bash 
output=> admin  0.000GB
         config 0.000GB
         local  0.000GB
         mydb   0.000GB
```


* if you want to create a database with name <mydb>, then use DATABASE
```javascript
 use mydb
```
```bash
output=> switched to db mydb
```


* if you want to delete database, then db.dropDatabase() command 
```javascript
 db.dropDatabase()
```
```bash
output=> { "ok" : 1 }
```


Create Collection :
* Basic syntax of createCollection() command is 
```javascript
 db.createCollection("collection_name")
```
```bash
output=> { "ok" : 1 }
```


Create Collection Attributes :
* Capped Attribute  :- Optional if true ,enables a capped collection. Capped collection is a fixed size collection 
                      that automatically overwrites its oldest entries when it reachers its maximum size .if you specify true, you need to specify size parameter also.
* Size Attribute    :- Optional Specifies a maximum size in bytes for a capped collection . if capped is 
                       true ,then you need to specify this fields also
* AutoIndexId       :- Optional. Specify false to disable the automatic creation of an index on the _id field 
* Max Attribute     :- Optional. Specifies the maximum number of documents allowed in the capped collection .
```javascript
 db.createCollection("mydb",{
    capped:true,
    autoIndexID:true,
    size:6142800,
    max:10000
    }
)
```


* in MongoDB you don't need to create collection. MongoDB creates collection automatically when you insert in new collection 
```javascript
db.col.insert(
    {
        "name":"mahmoud",
        _id:1
    }
)
```
```bash
output=> WriteResult({"nInserted":1})
```
```javascript
show collections
```
```bash 
output=> col
         movie
         persons
         test
```


* To Insert data into MongoDB collection, You need to use MongoDB's Insert()Method. 
```javascript
db.myCol.insert(
    {
        _id:3,
        name:"mahmoud",
        arr:[1,2,3,4]
    }
)
```
```bash
output=> WriteResult({"nInserted":1})
```

* To insert multiple documents in single quary
```javascript
db.myCol.insert(
    [
        {
            _id:4,
            name:"ahmed",
            arr:[1,2,3,4]
        },
        {
            _id:5,
            name:"Ziad",
            arr:[1,2,3]
        }
    ]
)
```
```bash
output=> WriteResult({"nInserted":1})
```

* To insert the document you can db.myCol.save(document) also - if you don't specify _id in the document then save() Method will work same as insert() Method. if you specify _id then it will replace whole data of document containing _id as specified in save() Method .
```javascript
 db.myCol.find()
```
```bash
output=> {"_id":9, "name":"mahmoud", "arr":[1,2,3,4]}
         {"_id":8, "name":"ahmed", "arr":[1,2,3,4]}
```


```javascript
db.myCol.save(
    {
        _id:2,
        name:"Ziad"
    }
)
```
```bash
output=> WriteResult({"nInserted":1})
```


```javascript
db.myCol.find()
```
```bash
output=> {"_id":9, "name":"mahmoud", "arr":[1,2,3,4]}
         {"_id":8, "name":"ahmed", "arr":[1,2,3,4]}
         {"_id":2, "name":"Ziad"}
```


```javascript
db.myCol.save(
    {
        _id:9,
        name:"Mostafa",
        arr:[1,2,3,4]
    }
)
```
```bash
output=> WriteResult({"nInserted":1})
```

```javascript
db.myCol.find()
```
```bash
output=> {"_id":9, "name":"Mostafa", "arr":[1,2,3,4]}
         {"_id":8, "name":"ahmed", "arr":[1,2,3,4]}
         {"_id":2, "name":"Ziad"}
```


* To quary data from MongoDB collection, You need to use MongoDB's find() method.
```javascript
 db.COLLECTION_NAME.find()
```

* To display the result in a formatted way, you can use pretty() method.
```javascript
 db.myCol.find().pretty()
```

* Apart from find() method, there is findOne() method, that returns only one document 
```javascript
 db.myCol.findOne()
```


Operations : 
* Equality => 
```javascript
db.myCol.find(
    {"name":"mahmoud"}
)  ==  find where name == mahmoud
```

* Less than =>
```javascript
db.myCol.find({
    "like":{ $lt:50 }
}).pertty()
```

* Less than Equals => 
```javascript
db.myCol.find( 
    {
        "like":{ $lte:50 }
    }
 ).pretty()
```

* Greater than => 
```javascript
db.myCol.find({
    "like":{ $gt:50 }
}).pertty()
```

* Greater than Equals => 
```javascript
db.myCol.find( 
    {
        "like":{ $gte:50 }
    }
 ).pretty()
```

* Not Equality => 
```javascript
db.myCol.find({"name":{$ne:"mahmoud"}}).perrty()  ==  find where name != mahmoud
```

* In find() method , if you pass multiple keys by separating them by ';' then MongoDB treats it as AND condition.          Following is the basic syntax of AND :
```javascript
db.myCol.find(
    { 
        $and : [{name:"mahmoud"},{id:2}]
    }
).perrty()
```

* To query documents based on the OR condition, you need to use $OR keyword. Following is the basic syntax of OR
```javascript
db.myCol.find(
    {
        $Or : [{name:"mahmoud"},{id:2}]
    }
).perrty()
```

* MongoDB's update() and save() methods are used to update document into a collection. the update() method updates the values in the existing document 
```javascript
db.myCol.update(
    {name:"mahmoud"},{ $set: {name:"ahmed"}}
)  By default mongodb will update only single document, to update multiple you need to set a paramter 'multi' to true 
```

```javascript
db.myCol.update(
    {name:"mahmoud"},{ $set : {name:"ahmed"} },
    {multi:true}
)
```

* MongoDB's remove() method is used to remove a document from the collection . remove method accept two parameters. One is deletion criteria and second is justOne flag
- deletion critia - (Optional) deletion criteria according to documents will be removed 
- justOne - (Optional) if set to true or 1,then remove only one
```javascript
db.myCol.remove(
    {age:8},
    1
)
```

Projection : 
* in MongoDB, projection means selecting only the necessary data rather than selectong whole of the data of a document.
if document has 5 fields and you need to show only 3, then select only 3 fields from them .
* in MongoDB, when you execute find() method, then it displays all fields of a document. To limit this you need to set a list of fields with value 1 or 0 . 1 is used to show the field while 0 is used to hide the fields
```javascript
 db.myCol.find(
    {},
    {name:1 , _id:0} // to show name and hide _id 
) 
```

* To limit the records in MongoDB, you need to use limit() method. the method accepts one number type argument,which is the number of documents that you want to be displayed.
```javascript
 db.myCol.find().limit(5)
```

* Skip() method you just need to pass the number of records to be skipped. it basically removes the first n documents from the result set.
```javascript
 db.myCol.find().skip(2)
```

* To sort documents in MongoDb, you need to use sort() method . the method accepts a document containing a list of fields along with their sorting order. To specify sorting order 1 and -1 are used. i is used for asc order while -1 is used for desc order
```javascript
 db.myCol.find().sort(
    {name:-1}   // to sort documents desc with name field
)
```

* distinct method finds the distinct values for a given field across a single collection and returns the results in an array.it takes three parameters first one is the field for which to return distinct values and the others are optional.
```javascript
 db.myCol.find().distinct("name")
```

* The count method counts the number of documents that match the selection criteria. it returns the number of documents that match the selection criteria
```javascript
 db.myCol.count()
```
```javascript
 db.myCol.find().count()
```

* This operator is used to select those documents where the value of the field is equal to any of thr given value in the array 
```javascript
 db.myCol.find(
    {
        name: {$in : ["ahmed","mahmoud"] }
    }
)
```

* $regex This operator is used to search for the given string in the specified collection. it is helpful when we don't know the exact field value that we are looking in the document.
```javascript
 db.myCol.find(
    {
        name:{$regex : /ed/ }
    }
)
```

                  .....................  We will continue soon  ........................


----------------------------------------------------------

### What is Hadoop :
- Hadoop is an open-source framework that allows to store and process big data in a distributed environment across 
clusters of computers using simple programming models .
- Hadoop provides fast and reliable analysis of both structured data and unstructured data
- Hadoop can scale up from single servers to thousands of machines, each offering local computation and storage


### Why Hadoop :
- Efficient: Data stored in any node is also replicated in other nodes of the cluster. This ensures fault tolerance. If one node goes down, there is always a backup of the data available in the cluster.
- Scalability :Unlike traditional systems that have a limitation on data storage, Hadoop is scalable because it operates in a distributed environment .
- Low cost :As Hadoop is an open-source framework, with no license to be procured, the costs are significantly lower compared to relational database systems .
- Speed :Hadoop's distributed file system, concurrent processing, and the MapReduce model enable running complex queries in a matter of seconds


### Hadoop Architecture :
components of Hadoop:
1.Hadoop HDFS - Hadoop Distributed File System (HDFS) is the storage unit.
2.Hadoop MapReduce - Hadoop MapReduce is the processing unit.
3.Hadoop YARN - Hadoop YARN is a resource management unit of Hadoop.


### Hadoop Distributed File System (HDFS) :
- The Hadoop Distributed File System (HDFS) is a distributed file system for Hadoop which provides storage in Hadoop in a
distributed fashion .
- It contains a master/slave architecture. This architecture consist of a single NameNode performs the role of master, and multiple DataNodes performs the role of a slav .
- Both NameNode and DataNode are capable enough to run on commodity machines. The Java language is used to develop HDFS. So any machine that supports Java language can easily run the NameNode and DataNode software.
- data is actually saved in HDFS where in it can automatically be duplicated at three different locations. Therefore, even if two of the systems get collapse, the file will still be present on the third system .


• NameNode :
⮚ Initially, data is broken into abstract data blocks. 
⮚ The file metadata for these blocks, which include the file name, file permissions, IDs, locations, and the number of replicas, are stored in a fsimage, on the NameNode local memory .
• Secondary NameNode:
⮚plays a vital role in case there is some technical issue in the NameNode.
⮚The Secondary NameNode served as the primary backup solution in early Hadoop versions.
• DataNode:
⮚ Each DataNode in a cluster uses a background process to store the individual blocks of data on slave servers.

❑ Block is a small unit where in the files are split. It has a default size of 64 MB or 128 MB and can be increased as needed.
❑ In general replication factor is 3.x and block size is 128 MB
