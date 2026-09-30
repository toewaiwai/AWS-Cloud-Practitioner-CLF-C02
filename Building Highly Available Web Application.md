Main goal: Build a highly available web application architecture using networking, database, caching, shared storage, load balancing, Auto Scaling, CloudFormation, and chaos testing.

<img width="458" height="380" alt="image" src="https://github.com/user-attachments/assets/b032971b-489c-485d-a2d4-0924f1ab70cb" />

<img width="233" height="200" alt="image" src="https://github.com/user-attachments/assets/a31c9ee5-a633-4750-a9d3-06322f862927" />

Task 1: Configure the Network
Create the CloudFormation stack
<img width="1546" height="244" alt="image" src="https://github.com/user-attachments/assets/64d5666a-f43f-4915-9aa8-3999f81066e2" />

<img width="784" height="302" alt="image" src="https://github.com/user-attachments/assets/6971b7a5-588e-49a7-ba71-381078b531cf" />

<img width="772" height="136" alt="image" src="https://github.com/user-attachments/assets/adf64d4c-d958-49dd-a8bf-6fe3b612c5df" />

<img width="1183" height="319" alt="image" src="https://github.com/user-attachments/assets/0f723252-af24-4702-b193-7c5e8dff0261" />

Task 2: Create an Amazon RDS database
The application needs somewhere to store persistent data

<img width="768" height="415" alt="image" src="https://github.com/user-attachments/assets/5ed28edb-2661-4749-82f3-3cab17611f50" />

<img width="608" height="316" alt="image" src="https://github.com/user-attachments/assets/5854d48d-af0c-42a1-8fe0-a12cc08419f8" />

<img width="619" height="146" alt="image" src="https://github.com/user-attachments/assets/02f16e0a-b3c1-4e4d-9c12-5be017ce18a6" />

<img width="628" height="74" alt="image" src="https://github.com/user-attachments/assets/a97c7c6d-a7c6-4293-8301-37450e49b6dc" />

<img width="1227" height="775" alt="image" src="https://github.com/user-attachments/assets/82829eb8-b6b2-4990-ad12-e7e36852bf33" />

<img width="431" height="67" alt="image" src="https://github.com/user-attachments/assets/68fdf5b8-ee43-453d-9140-7a32a48c3eb3" />

<img width="1257" height="745" alt="image" src="https://github.com/user-attachments/assets/64eed08d-d785-437e-b828-1240a774ef1a" />

<img width="930" height="777" alt="image" src="https://github.com/user-attachments/assets/40e4c9be-28f3-4aa5-ba44-d39194fdb89c" />

In the Maintenance section, deselect Enable auto minor version upgrade.
Deselect Enable deletion protectio

Copy database metadata
1. In the left navigation pane, choose **Databases**.
2. Choose the **mydbcluster** link.
3. Choose the **Connectivity & security** tab.
4. Choose the **Endpoints** tab.
5. Copy the **endpoint** value for the **Writer** instance to a text editor.
6. Choose the **Configuration** tab.
7. Copy the **Master username** value to a text editor (admin)
8. For **Master password**, use the **LabPassword** value from the left side of these lab instructions (7XGeAjCf10jz)
9. In the left navigation pane, choose **Databases**.
10. Choose the **mydbcluster-instance-x** writer instance link.
11. Choose the **Configuration** tab.
12. Copy the **DB name** value to a text editor (WPDatabase)

Task 3: Create an Amazon ElastiCache for Memcached
Create the Amazon ElastiCache cluster

<img width="782" height="211" alt="image" src="https://github.com/user-attachments/assets/dfadffc9-9027-4bb7-9a8e-8e770f8d7327" />

<img width="1405" height="841" alt="image" src="https://github.com/user-attachments/assets/148f0198-a81c-47f4-bc8c-b30bb5abc2ca" />

<img width="1017" height="447" alt="image" src="https://github.com/user-attachments/assets/d3d1d69d-edfa-4194-af03-cdcfc23d0588" />

<img width="523" height="209" alt="image" src="https://github.com/user-attachments/assets/3a3e4670-aabd-4345-be8c-f2ff60cacd45" />

<img width="740" height="416" alt="image" src="https://github.com/user-attachments/assets/d3aa4d76-337e-4c78-aa77-ec9092894b52" />

<img width="783" height="201" alt="image" src="https://github.com/user-attachments/assets/e5289837-e91a-4726-8ee0-0789679a460f" />

Task 4: Create an Amazon EFS file system
Create new Amazon Elastic File System

<img width="1009" height="700" alt="image" src="https://github.com/user-attachments/assets/1b2ec250-9d7f-40c8-87e9-d66fac5aaa89" />

<img width="1321" height="738" alt="image" src="https://github.com/user-attachments/assets/fb205d16-46e8-44ea-8cea-fb01b4eac243" />

<img width="533" height="127" alt="image" src="https://github.com/user-attachments/assets/718220f3-b2ba-496e-ba6f-a4005c9f703f" />

<img width="784" height="134" alt="image" src="https://github.com/user-attachments/assets/9f997964-8213-40fa-bcef-48975fbe5246" />

On the **Mount targets** page:

- For **Availability Zone**, select the **Availability Zone ending in “a”**.
- For **Subnet ID**, select **AppSubnet1**.
- For **Security group**, select **xxxxx-EFSMountTargetSecurityGroup-xxxxx**
- To remove the **default** Security group, choose the **X**.
- For **Availability Zone**, select **Availability Zone ending in “b”**.
- For **Subnet ID**, select **AppSubnet2**.
- For **Security group**, select **xxxxx-EFSMountTargetSecurityGroup-xxxxx**.
- To remove the **default** Security group, choose the **X**.

<img width="516" height="223" alt="image" src="https://github.com/user-attachments/assets/993d5767-ca41-481f-90ed-2e29e1fc692e" />

<img width="783" height="210" alt="image" src="https://github.com/user-attachments/assets/e4b8dcb5-bcd9-4ea3-b7e3-e0131d1adf45" />

Task 5: Create an Application Load Balancer
Create a Target group

<img width="1395" height="843" alt="image" src="https://github.com/user-attachments/assets/980b5df5-a241-44b2-8357-cfb0cf66b629" />

In the **Health checks** section:

For **Health check path**, enter /wp-login.php
- Expand the  **Advanced health check settings** section and configure the following:
    - For **Healthy threshold**, enter 2.
    - For **Unhealthy threshold**, enter 10.
    - For **Timeout**, enter 50.
    - For **Interval**, enter 60.
 
<img width="507" height="283" alt="image" src="https://github.com/user-attachments/assets/3f3b0ab8-1585-48c1-b330-59fb97e46b8d" />

<img width="773" height="356" alt="image" src="https://github.com/user-attachments/assets/9cd90bb8-61af-4a21-8eda-c4bdc598a0f1" />

Create an Application Load Balancer
1. Choose **Create load balancer**.
2. In the Application Load Balancer section, choose **Create**.
3. On the **Create Application Load Balancer** page, in the **Basic Configuration** section:

<img width="1212" height="778" alt="image" src="https://github.com/user-attachments/assets/595b1759-019e-4089-8958-4d7bb65139b6" />

<img width="607" height="146" alt="image" src="https://github.com/user-attachments/assets/9bfa8013-f112-42d4-aa01-64ced184a362" />

<img width="608" height="92" alt="image" src="https://github.com/user-attachments/assets/9eb9eab6-246b-48a6-8a79-9de9187035aa" />

<img width="608" height="211" alt="image" src="https://github.com/user-attachments/assets/60837ffb-e368-4886-8475-e99a6494346c" />

<img width="784" height="359" alt="image" src="https://github.com/user-attachments/assets/21e360e8-78ec-47fb-8b67-ed5b7f435a61" />

Task 6: Create a launch template using CloudFormation
Create the CloudFormation stack

<img width="781" height="307" alt="image" src="https://github.com/user-attachments/assets/fc507af3-0680-4b44-994c-363067bdac40" />

For Database endpoint, paste the writer endpoint you copied in Task 2.
For Database User Name, paste the Master username you copied in Task 2.
For Database Password, paste the LabPassword value from the left side of these lab instructions.
For WordPress admin username, defaults to wpadmin.
For WordPress admin password, paste the LabPassword value from the left side of these lab instructions.
For WordPress admin email address, input a valid email address.
For Instance Type, leave the default value of t3.medium.
For ALBDnsName, paste the DNS name value you copied in Task 5.
For LatestAL2AmiId, leave the default value.
For WPElasticFileSystemID, paste the File system ID value you copied in Task 4.

<img width="515" height="386" alt="image" src="https://github.com/user-attachments/assets/77799468-704e-42c4-9be2-8d9e360ac286" />

<img width="782" height="293" alt="image" src="https://github.com/user-attachments/assets/0b780856-f497-4def-a467-55693e7ac7c3" />

Task 7: Create the application servers by configuring an Auto Scaling group and a scaling policy

Creating an Auto Scaling group

<img width="778" height="281" alt="image" src="https://github.com/user-attachments/assets/4168748d-cf6f-415b-8d03-38188733aee1" />

<img width="746" height="416" alt="image" src="https://github.com/user-attachments/assets/77f766cd-7a0e-49e2-8b8e-e055c0edf662" />

<img width="756" height="362" alt="image" src="https://github.com/user-attachments/assets/0f3bc841-9a8c-48fe-8b29-37da6c4b2900" />

<img width="746" height="311" alt="image" src="https://github.com/user-attachments/assets/1fa709d1-4672-4311-a639-2700a0528891" />

For Load balancing, select Attach to an existing load balancer.
For Attach to an existing load balancer, select Choose from your load balancer target groups.
For Existing load balancer target groups, select myWPTargetGroup | HTTP.
For Health checks, select Turn on Elastic Load Balancing health checks.
For Health check grace period, leave at the default value of 300 or more.

<img width="520" height="230" alt="image" src="https://github.com/user-attachments/assets/6042fb4f-8373-4ba5-aa43-92cd8d9ca052" />

<img width="490" height="206" alt="image" src="https://github.com/user-attachments/assets/f4a457c3-9648-4712-a122-717502d45c3f" />

<img width="506" height="280" alt="image" src="https://github.com/user-attachments/assets/a1c7dda2-ec77-4060-90b3-6d93dd7299a0" />

<img width="498" height="389" alt="image" src="https://github.com/user-attachments/assets/37e39605-f33d-4c89-ba78-7b307096412d" />

Verify the target groups are healthy

<img width="773" height="365" alt="image" src="https://github.com/user-attachments/assets/6158864a-43eb-48ab-887d-e7a2882775d4" />

1. Choose **Load Balancers**.
2. Copy the **DNS name** to a text editor and append the value /wp-login.php to the end of the DNS name to complete your WordPress application URL.

```
myWPAppALB-546058345.us-west-2.elb.amazonaws.com/wp-login.php
```

Paste the WordPress application URL value into a new browser tab

Task 8: Chaos testing with AWS Fault Injection Simulator
Test scenario and assumptions

<img width="752" height="265" alt="image" src="https://github.com/user-attachments/assets/8b818ecc-08e3-4f2c-b38a-69eba3dddd79" />

<img width="710" height="400" alt="image" src="https://github.com/user-attachments/assets/6f6d10d0-8f39-4cab-ab3e-416a56b4ca12" />

<img width="537" height="425" alt="image" src="https://github.com/user-attachments/assets/8deb1c31-3183-4206-8b1b-f5a555cf1307" />

<img width="544" height="443" alt="image" src="https://github.com/user-attachments/assets/d2a70fa2-02c7-415f-b41d-0d638860ecb1" />

<img width="774" height="211" alt="image" src="https://github.com/user-attachments/assets/4b6b4e5c-5fbb-4ab0-ae42-3b998afb6b94" />

<img width="778" height="302" alt="image" src="https://github.com/user-attachments/assets/d87ab743-e8dc-4cee-8138-97bcd52ff93f" />

Start the experiment

<img width="760" height="413" alt="image" src="https://github.com/user-attachments/assets/9dd4ea61-ea27-4275-85a9-125f1e53cc48" />

Observe the experiment
Return to the WordPress website browser tab and refresh  the page every few seconds.
