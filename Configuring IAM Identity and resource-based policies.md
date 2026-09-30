### Lab Objective

Reviewed and evaluated the IAM role attached to an Amazon EC2 instance, identify the AWS actions permitted, and determine which S3 resources the instance is authorized to access. The lab also demonstrates how IAM policies control EC2 access to AWS services using specific permissions and resource-level restrictions.

### Key Learning

Analyzed an IAM policy attached to an EC2 instance profile and identified the allowed S3 actions and resource scope. The policy permits S3 bucket/object listing across available buckets while restricting `s3:PutObject` access to specific files within the designated data and backup buckets.

Identified the **Command Host EC2 instance** and reviewed its security configuration
<img width="1909" height="805" alt="image" src="https://github.com/user-attachments/assets/a24f6f30-d70b-46fe-9cbd-6eb5cd0c6814" />
Reviewed the **S3AccessPolicy** associated with the IAM role.

Examined the IAM policy **Action** and **Resource** permissions.

Verified that the EC2 instance was allowed to:

- List available S3 buckets using `s3:ListAllMyBuckets`.
- List objects within S3 buckets using `s3:ListBucket`.
- Upload specific files using `s3:PutObject`.

Verified that `s3:PutObject` permissions were restricted to specific files in the designated **Data** and **Backup** S3 buckets
<img width="762" height="558" alt="image" src="https://github.com/user-attachments/assets/96c7b636-ec75-46d5-b5c4-fe51a1cbff92" />
<img width="472" height="715" alt="image" src="https://github.com/user-attachments/assets/baed1d7d-7f01-4e91-b55d-a7379839c833" />

Validate and test permissions granted to the EC2 instance
<img width="1918" height="481" alt="image" src="https://github.com/user-attachments/assets/6cd45ef9-6400-4c15-8a8d-ebce08489345" />
