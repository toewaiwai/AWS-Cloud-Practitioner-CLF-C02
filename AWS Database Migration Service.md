<img width="403" height="164" alt="image" src="https://github.com/user-attachments/assets/8e5ddf42-bbb8-457d-beca-6840415cecaa" />

```
                    AWS Cloud
┌───────────────────────────────────────────────────┐
│                                                   │
│   ┌───────────────┐                               │
│   │ EC2 Instance  │                               │
│   │               │                               │
│   │ MySQL         │                               │
│   │ Workbench     │                               │
│   └───────┬───────┘                               │
│           │                                       │
│           │                                       │
│           ↓                                       │
│   ┌─────────────────┐                             │
│   │ Source MySQL    │                             │
│   │ Database        │                             │
│   └────────┬────────┘                             │
│            │                                      │
│            │                                      │
│            │ AWS DMS                              │
│            ↓                                      │
│   ┌─────────────────┐                             │
│   │ Aurora MySQL    │                             │
│   │ Target Database │                             │
│   └─────────────────┘                             │
│                                                   │
└───────────────────────────────────────────────────┘
```
Task 1. Connect to Amazon EC2 instance

Task 2. Configure and connect to source MySQL database

Install MySQL and workbench on instance
<img width="894" height="640" alt="image" src="https://github.com/user-attachments/assets/58197b1c-0115-4e22-8b1b-adee0eef5ff2" />
<img width="867" height="643" alt="image" src="https://github.com/user-attachments/assets/29c55ace-f503-4f6f-94e8-af70199626a5" />
<img width="829" height="652" alt="image" src="https://github.com/user-attachments/assets/ec912983-6f35-4b8b-bb35-4a35221131e0" />
Connect and configure your source MySQL server
<img width="1180" height="703" alt="image" src="https://github.com/user-attachments/assets/efb0e484-191f-43d3-833c-c605d257a128" />

```
CREATE DATABASE mydb;
```

<img width="1192" height="660" alt="image" src="https://github.com/user-attachments/assets/b7ff65dc-5b3d-4492-95de-4001358c9f71" />
Import data into database
<img width="952" height="582" alt="image" src="https://github.com/user-attachments/assets/a2a53595-3433-44ff-9bdf-f088c73ce962" />
Verify data was imported
<img width="952" height="532" alt="image" src="https://github.com/user-attachments/assets/7b1813a0-fe5b-474a-833b-49d767791c5f" />

```
Select * from mydb.employee;
```

<img width="952" height="565" alt="image" src="https://github.com/user-attachments/assets/398ad336-0a7a-4392-aafe-82a0303fdc6f" />
Task 3. Use MySQL Workbench to connect to your RDS instance
<img width="1473" height="139" alt="image" src="https://github.com/user-attachments/assets/aa25a9c8-eeb6-4ffc-ad41-75c8dfa7bf06" />
Return to the Fleet Manager - **ClusterEndpoint.txt** file should be on desktop that created in the previous step.
Create a new MySQL connection by choosing the plus  button
<img width="1249" height="652" alt="image" src="https://github.com/user-attachments/assets/1f4f5998-6303-412b-a345-ff2198eb28b1" />
<img width="766" height="373" alt="image" src="https://github.com/user-attachments/assets/88d1ecba-2a38-4fc8-95a8-9b05e340dab6" />
<img width="1182" height="699" alt="image" src="https://github.com/user-attachments/assets/405ab32f-e0f0-41e3-aea3-2d834d8d9707" />
Task 4. Migrate source MySQL database to Aurora instance using AWS Database Migration Service

The first step in migrating data using AWS Database Migration Service is to create a replication instance. An AWS DMS replication instance runs on an Amazon Elastic Compute Cloud (Amazon EC2) instance.

Create replication instance (A replication instance provides high availability and failover support using a Multi-AZ deployment)

AWS DMS uses a replication instance that connects to the source data store, reads the source data, and formats the data for consumption by the target data store. A replication instance also loads the data into the target data store.
<img width="963" height="723" alt="image" src="https://github.com/user-attachments/assets/fe0dc1aa-e0a7-4b54-9493-96ae904d3c2b" />
<img width="880" height="346" alt="image" src="https://github.com/user-attachments/assets/e1cae184-eb70-405a-98f8-6a61231b7b0c" />
<img width="1569" height="430" alt="image" src="https://github.com/user-attachments/assets/2eea1abd-488b-44f2-abbc-029dc22712fd" />
Create source endpoint
<img width="670" height="817" alt="image" src="https://github.com/user-attachments/assets/5ee7fb9a-178b-492a-a263-2c1893c32d39" />
<img width="613" height="162" alt="image" src="https://github.com/user-attachments/assets/83a80acf-c581-48d7-9876-21f2c88f899e" />
<img width="1599" height="372" alt="image" src="https://github.com/user-attachments/assets/38b728ca-4cc0-4862-b45b-ecf884dfa94f" />
Create target endpoint to Aurora instance
<img width="703" height="844" alt="image" src="https://github.com/user-attachments/assets/d3d1b4ac-6872-4cbe-9f97-8b41fd50b791" />
<img width="631" height="345" alt="image" src="https://github.com/user-attachments/assets/2c91367a-da26-449d-93ce-6af0f4b0e57a" />
Create a database migration task
<img width="1257" height="730" alt="image" src="https://github.com/user-attachments/assets/b786511c-f089-4cee-84f1-d4811437e189" />
<img width="1285" height="595" alt="image" src="https://github.com/user-attachments/assets/9096e12e-a93f-429e-be75-3c15ab9030f6" />
<img width="1264" height="135" alt="image" src="https://github.com/user-attachments/assets/f201fffc-0549-4b8c-9d54-a74794ba5f16" />
<img width="1611" height="424" alt="image" src="https://github.com/user-attachments/assets/348972f1-4d75-48ef-b131-0ace766f2989" />
<img width="1566" height="811" alt="image" src="https://github.com/user-attachments/assets/250d74f8-4dbe-4b61-a757-48a7abe26faa" />
Return to the Fleet Manager - Remote Desktop browser tab. In MySQL Workbench, on the Aurora connection tab, Execute
<img width="1194" height="899" alt="image" src="https://github.com/user-attachments/assets/bc4634f8-f901-4bd0-a7e6-8a628d404020" />

