Lab Concept

Amazon Data Firehose is a fully managed service that collects streaming data, optionally transforms it, and delivers it to a destination such as Amazon S3.

In this lab, Firehose receives demo data through Direct PUT, uses AWS Glue to help convert the record format to Apache Parquet, and delivers the transformed data to Amazon S3.

<img width="404" height="110" alt="image" src="https://github.com/user-attachments/assets/bf2fb432-0782-43ed-b52a-bd0b4b9e1ea0" />



<img width="407" height="124" alt="image" src="https://github.com/user-attachments/assets/1ce68acd-d6f8-4d02-8ae6-2753e08361fd" />

AWS Glue provides the metadata/schema that Firehose uses during record format conversion.
Parquet is a columnar data format. Instead of storing data primarily row-by-row, it organizes data by columns.

<img width="125" height="370" alt="image" src="https://github.com/user-attachments/assets/84d1db47-2e4a-4f05-80ee-ef0e08c1f837" />



Task 1: Create an Amazon Data Firehose delivery stream
1. At the top of the AWS Management Console, in the search bar, search for and choose Amazon Data Firehose.
2. Choose **Create Firehose stream**.
3. On the **Create Firehose stream** page, in the **Choose source and destination** section:
    - For **Source**, choose **Direct PUT**.
    - For **Destination**, choose **Amazon S3**.
  
<img width="929" height="281" alt="image" src="https://github.com/user-attachments/assets/bfe68c62-9776-4a4e-b61f-59ac57d539ef" />

On the **Create Firehose stream** page, in the **Transform and convert records - *optional*** section:

- For **Convert record format**, enable **Enable record format conversion**.
- For **Output format**, choose **Apache Parquet**.
- For **AWS Glue region**, choose the value corresponding to the **Region** value that is listed to the left of these instructions.
- For **AWS Glue database**, choose **firehose_demo_db**.
- For **AWS Glue table**, choose **Browse**, select **stock_data** and **Choose**.

<img width="620" height="343" alt="image" src="https://github.com/user-attachments/assets/c1ab1c18-1b73-40c6-af14-3fa6a7499aa9" />


1. On the **Create Firehose stream** page, in the **Destination settings**:
    - Choose **Browse**.
    - Select the bucket that starts with **firehose-destination-**.
    - Choose **Choose**.
2. Expand the **Advanced settings** section, and then:
    - For **service access**, select **Choose existing IAM role**.
    - For **Existing IAM roles**, choose **firehose-service-role-**.
3. Choose **Create Firehose stream**

<img width="645" height="105" alt="image" src="https://github.com/user-attachments/assets/22d28fe7-868c-485b-9d07-3ae6b0dcc9cd" />

<img width="625" height="259" alt="image" src="https://github.com/user-attachments/assets/0fbfbd07-8dbe-4bbb-9b3a-7a970aa60480" />

Task 2: Test the Amazon Data Firehose stream
1. Once the stream is created, expand the **Test with demo data** section.
2. Choose **Start sending demo data**.
3. Navigate to the Monitoring section at the bottom of the page.
4. In the **Firehose stream metrics** section, adjust the time frame to 15 minutes:
    - Select the calendar icon
    - Choose **15** from the **Minutes** row.
5. Choose the  drop-down menu on the right side of the  icon and select **10 seconds**. This sets the charts to refresh every 10 seconds.
6. Verify that sample data appears in the monitoring charts.

<img width="871" height="421" alt="image" src="https://github.com/user-attachments/assets/161271bf-56f1-47a9-85ca-98c026991ec6" />


Task 3: Navigate S3 bucket and locate transformed data
1. At the top of the AWS Management Console, in the search bar, search for and choose S3. Right-click on S3 and choose **Open link in new tab** to keep the Firehose console accessible.
2. Select the bucket that starts with **firehose-destination-**.
3. Navigate through the timestamp-based partition hierarchy:
- Year folder (shown as YYYY, like 2025/)
- Month folder (shown as MM, like 02/)
- Day folder (shown as DD, like 18/)
- Hour folder (shown as HH, like 14/)
1. Locate multiple transformed data files with **.parquet** extensions.
2. Review the folder structure to understand how your data is automatically organized by time intervals.
3. Return to the Firehose console by switching back to its browser tab.
4. On the **Firehose delivery stream** details page, expand the **Test with demo** data section if not already open.
5. Choose **Stop sending demo data** to conclude the test.

<img width="941" height="389" alt="image" src="https://github.com/user-attachments/assets/ca2306d4-5ca9-4a1d-9788-4585f2454ed0" />

<img width="944" height="407" alt="image" src="https://github.com/user-attachments/assets/fa06ba87-bb72-46d4-860a-f53f51fb1e81" />
