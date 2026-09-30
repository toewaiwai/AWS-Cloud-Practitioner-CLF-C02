<img width="404" height="128" alt="image" src="https://github.com/user-attachments/assets/81d03430-1ebe-42f5-afa0-f030a6eb46ec" />

1. Create Subnet group
<img width="1918" height="616" alt="image" src="https://github.com/user-attachments/assets/1630a345-d199-4d15-b6c6-69834dd1b13d" />
2. Create a DocumentDB cluster 
3. Create an additional replica instance on the mydocdb cluster (For redudancy and performance)
<img width="1893" height="792" alt="image" src="https://github.com/user-attachments/assets/b41452e8-7ca5-48b1-96f3-869a0b3228c6" />
4. Adjust the VPC security group containing the EC2 instance to allow port 27017 traffic
<img width="1918" height="706" alt="image" src="https://github.com/user-attachments/assets/5edf7f1f-9cf7-46da-a8bf-23530e5e1a7c" />
5. Connect to the mydocdb cluster from the IDE using Mongo shell

```
[ec2-user@ip-10-10-0-9 environment]$ wget https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem
--2026-09-20 15:11:37--  https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem
Resolving truststore.pki.rds.amazonaws.com (truststore.pki.rds.amazonaws.com)... 143.204.1.76, 143.204.1.55, 143.204.1.94, ...
Connecting to truststore.pki.rds.amazonaws.com (truststore.pki.rds.amazonaws.com)|143.204.1.76|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 165408 (162K) [binary/octet-stream]
Saving to: ‘global-bundle.pem’

global-bundle.pem              100%[==================================================>] 161.53K  --.-KB/s    in 0.01s

2026-09-20 15:11:37 (11.6 MB/s) - ‘global-bundle.pem’ saved [165408/165408]

[ec2-user@ip-10-10-0-9 environment]$ mongosh mydocdb.cluster-c7bwv1ougwie.us-west-2.docdb.amazonaws.com:27017 --tls --tlsCAFile global-bundle.pem --retryWrites=false --username dbadmin --password 6zJetJRSIC66
Current Mongosh Log ID: 6aaff7c6622ebfbbc49790c8
Connecting to:          mongodb://<credentials>@mydocdb.cluster-c7bwv1ougwie.us-west-2.docdb.amazonaws.com:27017/?directConnection=true&tls=true&tlsCAFile=global-bundle.pem&retryWrites=false&appName=mongosh+2.12.0
Using MongoDB:          5.0.0
Using Mongosh:          2.12.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

To help improve our products, pseudo-anonymous usage data is collected from interactive and agentic sessions only, and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

---

## Warning: Non-Genuine MongoDB Detected
This server or service appears to be an emulation of MongoDB rather than an official MongoDB product.
Some documented MongoDB features may work differently, be entirely missing or incomplete, or have unexpected performance characteristics.
To learn more please visit: https://dochub.mongodb.org/core/non-genuine-mongodb-server-warning.

rs0 [direct: primary] test>
```

6. Perform CRUD operations on a DocumentDB database using the Mongo shell
<img width="1030" height="247" alt="image" src="https://github.com/user-attachments/assets/2b1f848b-1eb4-432d-8695-15bc2d75728e" />

Insert a single document

```
db.collection.insertOne({"hello":"DocumentDB"})
```
insert a few entries into a collection
```
db.profiles.insertMany([
                    { "_id" : 1, "name" : "Matt", "status": "active", "level": 12, "score":202},
                    { "_id" : 2, "name" : "Frank", "status": "inactive", "level": 2, "score":9},
                    { "_id" : 3, "name" : "Karen", "status": "active", "level": 7, "score":87},
                    { "_id" : 4, "name" : "Katie", "status": "active", "level": 3, "score":27}
                    ])
```

<img width="1093" height="345" alt="image" src="https://github.com/user-attachments/assets/d7951a5e-6e81-470f-92c3-f4222e6deb07" />
Find a profile and modify it using the findAndModify command

```
db.profiles.findAndModify({
                query: { name: "Matt", status: "active"},
                update: { $inc: { score: 10 } }
            })
```

7. Perform database operations using the SDK
```
import pymongo
import sys
import time

##Create a MongoDB client, open a connection to Amazon DocumentDB as a replica set and specify the read preference as secondary preferred
client = pymongo.MongoClient('<EDITED THIRD CONNECT COMMAND>') 

##Specify the database to be used
db = client.mydb

##Specify the collection to be used
col = db.profiles

##Find a profile that was previously entered using the shell
x = col.find_one({"name": "Matt"})

##Print the result to the screen
print(x)

##Add an additional player record
col.insert_one({ "_id" : 5, "name" : "Ahmed", "status": "active", "level": 8, "score": 93})
time.sleep(2)

##Print the new full list
print("The full list of players is now")
for player in col.find():
    print(player)

##Close the connection
client.close()
```

<img width="1917" height="778" alt="image" src="https://github.com/user-attachments/assets/a1619235-c0cf-4e2c-94a8-0594ad75a1cc" />
<img width="1219" height="435" alt="image" src="https://github.com/user-attachments/assets/cbb56edf-bc51-4301-9d3e-2bb1c5b44fb1" />

