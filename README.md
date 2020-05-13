# Mini-Project-2-NoSQL-Databases



# Neo4j populations code 
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

MongoDB 

1. Cd path to mongofile
2. whrite "mongod" 
3. whrite "mongo" 
now the server is startet and ready to use
- test by "show dbs" 

now load csv file to mongodb (only posibble from cmd) 
1. cd mongo path folder and drop the csv-file in here
2. run the command below: 
mongoimport -d insurence -c insurence --type csv --file recordsinsurence.csv --headerline
3. check in the mongo terminal: "show dbs" there shoould now be a now database named "insurence"


# relevant database operations, which can be used to compare the databases

1.Population time
- MongoDB population time
![alt text](https://github.com/DunkRing/Mini-Project-2-NoSQL-Databases/blob/master/img/MongoDB%20populate%20time.JPG "Logo Title Text 1")
- Neo4j population time 
![alt text](https://github.com/DunkRing/Mini-Project-2-NoSQL-Databases/blob/master/img/Neo4j%20UploadTime.JPG "Logo Title Text 1")
2. How much space does the to database
- to andre bilelde (det ene før og efter = mongo) og neo4j står det i bunden af billedet.

3. selecet all elements from db

Neo4J - Match(n) RETURN n limit(36634)  -- Result: completed after 798 ms
