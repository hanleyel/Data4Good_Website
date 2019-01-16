## Overview

DynamoDB or RDS

* RDS is MySQL
* DynamoDB is NoSQL

leaning more with RDS for the larger data sets, but the DynamoDB is set up to jsut take tables. If we only need two tables then this will be more flexible.


## Creating a Database - Steps to follow in order to replicate the DEV/TEST SErver instances created currently.

#### Selecting the tier
<img width="1280" alt="screen shot 2019-01-16 at 2 33 37 pm" src="https://user-images.githubusercontent.com/20977403/51273911-d70ba280-199b-11e9-8e24-8777da820fd2.png">

For testing purposes the database is currently not in production. Once we have everything is order ont he database side, we can move it out of production and replicate these procedures.

#### Settings
For this demo I went with the base AWS Free Tier RDS for a base understanding of how to create the database and what each setting does.

**IMPORTANT**
In order to connect to the database remotely through the MySQL Workbench you MUST have `Public Access` checked to YES. I am still working on a way to internally configure the database with encryption as well as having the public access not be mandatory. At this stage in development I believe we must use the workbench to create our database unless we import MySQL code.

#### Connecting to the MySQL Workbench after creation

Step-by-step instructions can be found at https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToInstance.html. 

Currently we can just use a standard port number and host name connection, however in the future we might want to consider a IAM User for the dbinstance. This will require us to coneect using SSL. Directiosn for that type of connection is also provided in the webpage above.