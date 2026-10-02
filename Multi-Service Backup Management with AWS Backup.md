Lab Concept: AWS Backup is a centralized backup service that allows you to manage and protect data across multiple AWS services from a single console.

<img width="332" height="95" alt="image" src="https://github.com/user-attachments/assets/fe016675-c080-4b2e-8d76-b9f254359b78" />

Task 1: Review AWS Backup Service Settings and Create Backup Vaults
Review of AWS Backup settings

<img width="186" height="214" alt="image" src="https://github.com/user-attachments/assets/c814ce26-b493-4246-bdb5-3d50474859a6" />

<img width="929" height="389" alt="image" src="https://github.com/user-attachments/assets/d95563d8-4e8c-47e2-8448-e267e679d39f" />

Create backup vault with encryption settings
1. In the left navigation pane, choose **Vaults** under **My account**.
2. Choose **Create backup vault**.
3. In the **Vault name** field, enter Lab-Backup-Vault.
4. For **Vault type**, choose **Backup vault**.
5. In the **Encryption** section, from the dropdown menu, select **(default) aws/backup**
6. Leave all other settings at their default values.
7. Choose **Create vault**.
8. Wait for the backup vault creation to complete. You should see a green success banner indicating **Backup vault Lab-Backup-Vault has been created successfully**.
9. On the details page, confirm the encryption settings are properly configured.

<img width="227" height="76" alt="image" src="https://github.com/user-attachments/assets/8da1568f-0738-4907-bef4-ba868234ef63" />

<img width="934" height="404" alt="image" src="https://github.com/user-attachments/assets/b913edd2-4e03-41ca-941c-fd5334bfbe63" />

Task 2: Perform On-Demand Backups
Create on-demand backup for EC2 instance
1. In the AWS Backup console, choose **Protected resources** from the left navigation pane.
2. Choose **Create on-demand backup** to initiate the backup creation process.
3. In the **Create on-demand backup** dialog, configure the following settings:
- For **Resource type**, choose **EC2** from drop-down list.
- For **Instance ID**, choose **Lab1-EC2** from drop-down list.
- For **Total retention period**, from drop-down select **Days** and enter 3 for the number of days.
- For **Backup vault**, from the drop-down list select the backup vault you created previously Lab-Backup-Vault.
- For **IAM role**, choose **Choose an IAM role** and select the AWSBackupWorkshopRole role from the drop-down list.

<img width="932" height="398" alt="image" src="https://github.com/user-attachments/assets/dd54dca0-6ec5-4f8a-ac84-0b57fe27cb7d" />

<img width="935" height="398" alt="image" src="https://github.com/user-attachments/assets/60f8d2c0-d7cd-45f4-8b1b-c4f275963194" />

Create on-demand backup for EFS and RDS
1. In the AWS Backup console, choose **Protected resources** from the left navigation pane.
2. Choose **Create on-demand backup** to initiate the backup creation process.
3. In the **Create on-demand backup** dialog, configure the following settings:
- For **Resource type**, choose **EFS** from drop-down list.
- For **File system ID**, choose **Lab1-EFS** from drop-down list.
- For **Total retention period**, from drop-down select **Days** and enter 3 for the number of days.
- For **Backup vault**, from the drop-down list select the backup vault you created previously **Lab-Backup-Vault**.
- For **IAM role**, choose **Choose an IAM role** and select the AWSBackupWorkshopRole role from the drop-down list.

<img width="614" height="355" alt="image" src="https://github.com/user-attachments/assets/49aebf56-33e9-4866-aa3e-6578d6d7024b" />

<img width="612" height="115" alt="image" src="https://github.com/user-attachments/assets/7a08e2c3-ec4a-4d3f-acf9-66aa076ef576" />

1. In the AWS Backup console, choose **Protected resources** from the left navigation pane.
2. Choose **Create on-demand backup** to initiate the backup creation process.
3. In the **Create on-demand backup** dialog, configure the following settings:
- For **Resource type**, choose **RDS** from drop-down list.
- For **Database name**, choose **lab1-rds** from drop-down list.
- For **Total retention period**, from drop-down select **Days** and enter 3 for the number of days.
- For **Backup vault**, from the drop-down list select the backup vault you created previously **Lab-Backup-Vault**.
- For **IAM role**, choose **Choose an IAM role** and select the AWSBackupWorkshopRole role from the drop-down list.

<img width="906" height="397" alt="image" src="https://github.com/user-attachments/assets/d8f405f5-6c57-4abf-a9f1-35eb26e13d1d" />

<img width="944" height="317" alt="image" src="https://github.com/user-attachments/assets/ad98660c-12b5-4997-94e8-54b5488f7b27" />

Task 3: Create and Configure Backup Plans
Create new backup plan “HourlyBackupPlan-Lab1”
1. In the AWS Backup console, choose **Backup plans** from the left navigation pane to view all backup plans available.
2. In the AWS Backup console, choose **Create backup plan** to begin creating your automated backup strategy.
3. On the **Create backup plan** page, select **Build a new plan** to create a custom backup plan from scratch.
4. In the **Backup plan name** field, enter HourlyBackupPlan-Lab1 as the name for your new backup plan.
5. In the **Backup rule configuration** section, configure the first backup rule with the following settings:
- **Backup rule name**: Enter HourlyBackupRule
- **Backup vault**: Select the backup vault you created earlier from the dropdown menu
- **Backup frequency**: Choose **Hourly** from the frequency options

<img width="941" height="394" alt="image" src="https://github.com/user-attachments/assets/c1378aa5-948b-4b97-ba74-4711b58e3dc6" />

<img width="932" height="399" alt="image" src="https://github.com/user-attachments/assets/25d3a7be-d2a6-4d1f-935f-b5a91782d83f" />

<img width="829" height="196" alt="image" src="https://github.com/user-attachments/assets/6f6b9396-3d88-48c4-bec3-77c072d2e081" />

In the Lifecycle section, configure the retention settings:

Transition to cold storage: Leave this option unchecked for this lab
Total retention period: Select 3 Days to match your retention requirements

<img width="821" height="224" alt="image" src="https://github.com/user-attachments/assets/ce0064ce-2859-4198-80a0-385f51f3ac42" />

1. In the **Assign resources** dialogue box, configure the following:
- For **Resource assignment name**, enter HourlyPlanResourceAssignment
- For **IAM role**, choose **Choose an IAM role** and from the dropdown menu, select **AWSBackupWorkshopRole**.
- For **Define resource selection**, choose **Include all resource types**.
- For **Refine selection using tags - optional**, choose **Add tags** and enter backup for **Key**, select **Equals** for **Condition for value** and enter hourly for **Value**
1. Choose **Assign resources**
2. Choose **Continue**

<img width="922" height="400" alt="image" src="https://github.com/user-attachments/assets/a28c015a-2756-4e84-aaa6-3fcd15b51ca9" />

<img width="833" height="131" alt="image" src="https://github.com/user-attachments/assets/8f37652c-d7aa-470b-9915-e74096b80a4c" />

<img width="935" height="407" alt="image" src="https://github.com/user-attachments/assets/3fd5b9b4-40c2-4073-832e-051fc46f6822" />

Task 4: Resource Tagging
Add “backup:hourly” tags to EC2 instance
1. At the top of the AWS Management Console, in the search bar, search for and choose **EC2**.
2. In the EC2 dashboard left navigation pane, choose **Instances** to view all EC2 instances in your account.
3. Locate the instance named **Lab1-EC2** in the instances list and select it by choosing the checkbox next to the instance name.
4. With the Lab1-EC2 instance selected, choose the **Tags** tab in the lower details pane to view the current tags applied to the instance.
5. Choose **Manage tags** to open the tag management interface for the selected instance.
6. In the Manage tags dialog, choose **Add new tag** to create a new tag entry.
7. In the **Key** field, enter backup.
8. In the **Value** field, enter hourly in lowercase letters.
9. Choose **Save** to apply the tag to the Lab1-EC2 instance.

<img width="937" height="281" alt="image" src="https://github.com/user-attachments/assets/71ef7159-6db8-4d9d-b1fa-12faf4687dfe" />

Add tags to EFS resources
1. At the top of the AWS Management Console, in the search bar, search for and choose **EFS**.
2. On the EFS dashboard, locate and choose the **Lab1-EFS** file system from the list of available file systems to open its details page.
3. In the file system details page, choose the **Tags** tab to view and manage the tags associated with this EFS resource.
4. Choose **Manage tags** to modify the tags for the Lab1-EFS file system.
5. In the Edit tags section, choose **Add tag** to create a new tag entry.
6. In the **Key** field for the new tag, enter **backup**.
7. In the **Value** field for the backup tag, enter **hourly**.
8. Choose **Save** to apply the backup tags to your EFS file system.

<img width="941" height="376" alt="image" src="https://github.com/user-attachments/assets/04ce7902-0504-4c9a-aeb3-9af51d9a2d83" />

Add tags to RDS resources

1. At the top of the AWS Management Console, in the search bar, search for and choose **RDS**.
2. In the left navigation pane, choose **Databases** to view all RDS database instances in your account.
3. Locate the database instance named **lab1-rds** in the list and choose the database identifier link to open the database details page.
4. In the tabs list where you see **Connectivity & security** selected, scroll to the right and select the **Tags** tab.
5. In the **Tags** section, choose **Manage tags** to open the tag management interface.
6. Choose **Add new tag** to create the first backup-related tag.
7. In the **Key** field, enter **backup** and in the **Value** field, enter **hourly** to mark this RDS instance as eligible for backup operations.
8. Choose **Save changes** to apply the tags to your RDS database instance.

<img width="958" height="308" alt="image" src="https://github.com/user-attachments/assets/2a75a5d3-f459-473c-875f-d4683957a704" />

Verify backup plan execution

1. At the top of the AWS Management Console, in the search bar, search for and choose **AWS Backup**.
2. Choose **Backup plans** from the left navigation pane.
3. Choose **HourlyBackupPlan-Lab1** link.
4. Expand the **Backup schedule preview** to see the next 10 scheduled runs preview.
5. Choose **Jobs** from the left navigation pane to monitor backup job execution.
6. Verify that backup jobs are listed for your tagged resources, confirming that the backup plan is executing successfully.

<img width="934" height="360" alt="image" src="https://github.com/user-attachments/assets/db398b13-390e-4bd9-8447-cec6f0deec08" />

Choose Jobs from the left navigation pane to monitor backup job execution.

Verify that backup jobs are listed for your tagged resources, confirming that the backup plan is executing successfully.

<img width="941" height="279" alt="image" src="https://github.com/user-attachments/assets/160d87a4-a7bc-470d-aea4-ece93641b472" />


Complete Architecture

<img width="270" height="360" alt="image" src="https://github.com/user-attachments/assets/a369b8ad-e9f1-4841-8814-b4ee0f0fda35" />
