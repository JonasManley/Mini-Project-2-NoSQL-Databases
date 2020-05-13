# Mini-Project-2-NoSQL-Databases


## 1.preparing a large data source and loading it into both databases

We have found a datasheet containing 36634 insurence samples of growth.
[Datasheet Download, click here...](https://support.spatialkey.com/spatialkey-sample-csv-data/)
### Neo4j populations code 
```
LOAD CSV WITH HEADERS FROM "file:///FL_insurance_sample.csv" 
AS row MERGE (Insurance:Insurance {id:row.policyID}) 
SET 
Insurance.statecode = row.statecode, 
Insurance.county = row.county, 
Insurance.row.eq_site_limit = toFloat(row.eq_site_limit), 
Insurance.hu_site_limit = toFloat(row.hu_site_limit), 
Insurance.fl_site_limit = toFloat(row.fl_site_limit), 
Insurance.fr_site_limit = toFloat(row.fr_site_limit), 
Insurance.tiv_2011 = toFloat(row.tiv_2011), 
Insurance.tiv_2012 = toFloat(row.tiv_2012), 
Insurance.eq_site_deductible = toFloat(row.eq_site_deductible), 
Insurance.hu_site_deductible = toFloat(row.hu_site_deductible), 
Insurance.fl_site_deductible = toFloat(row.fl_site_deductible), 
Insurance.fr_site_deductible = toFloat(row.fr_site_deductible), 
Insurance.point_latitude = toFloat(row.point_latitude), 
Insurance.point_longitude = toFloat(row.point_longitude), 
Insurance.line = row.line, 
Insurance.construction = row.construction,
Insurance.point_granularity= toInteger(row.point_granularity),
```

### MongoDB 

1. Cd path to mongofile
2. whrite "mongod" 
3. whrite "mongo" 

*Now the server is startet and ready to use*
Test by running the command in MongoDB terminal

 ```
 show dbs
 ```

**now load csv file to mongodb (only posibble from cmd)** 
5. cd mongo path folder and drop the csv-file in here
6. run the command below:
	
	```
	mongoimport -d insurence -c insurence --type csv --file recordsinsurence.csv --headerline
	```	

7. check in the mongo terminal: "show dbs" there shoould now be a now database named "insurence"

## 2. selecting relevant database operations, which can be used to compare the databases

**1.Population time**
- MongoDB population time
![alt text](https://github.com/DunkRing/Mini-Project-2-NoSQL-Databases/blob/master/img/MongoDB%20populate%20time.JPG "Logo Title Text 1")
- Neo4j population time 
![alt text](https://github.com/DunkRing/Mini-Project-2-NoSQL-Databases/blob/master/img/Neo4j%20UploadTime.JPG "Logo Title Text 1")

**2. How much space does the two database consume**

**Neo4j**
- Before = 2.12 GB (2.278.607.182 bytes)
- After =  2.37 GB (2.547.756.160 bytes)
- Storage taken = 0.25 GB (269.148.978 bytes)

**MongoDB**

 - ![List item](https://github.com/DunkRing/Mini-Project-2-NoSQL-Databases/blob/master/img/Mongodb%20storage%20taken%20by%20csv%20file.JPG)

**3. Selecet all elements from db**

**Neo4j** 
```
Match(n) RETURN n limit(36634) 
```
Result was 0.798 Seconds

**MongoDB** 
```
DBQuery.shellBatchSize = 36634
db.insurence.find() - query all elments Result 10.00 sec
```
DBQuery.shellBatchSize - makes mongoDB retunring 36634 element instead of its standard
db.insurence.find() - quries all elements in the insurence collection

Result was 10.00 seconds

**4. How easy is it to setup**

**Neo4j**
very intuitive and easy to use GUI with alot of help, with error syntax and error handling.

**MongoDB**
Experience with a command prompt needed, no GUI to visualize data.
## 3. reporting the results and conclusions
Based on our experiments with Neo4j and MongoDB can we conclude that if you have a very large data collection you will have to have alot space available since Neo4j takes up approximately 83 times as much space.
But on the other hand its more intuitive to use Neo4j since you get alot of help with errors and syntax.
personally we found it easier to import data into Neo4j contra MongoDB.
