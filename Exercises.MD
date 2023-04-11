# Exercises related to AWS regions and availability zones:

1. Create an S3 bucket in multiple regions and configure cross-region **replication** between the buckets. 
   Upload a file to the original bucket and verify that the file is automatically replicated to the other buckets.
   
   ToDo:
   - Create an S3 bucket in multiple regions ☑️
   - Upload a file to the original bucket
   - Verify that the file is automatically replicated to the other buckets.
   - Configure cross-region replication between the buckets
   
   > ## When to use S3 Replication
     > **Data redundancy** – If you need to maintain multiple copies of your data in the same, or different AWS Regions, with different encryption types, or across different accounts. S3 Replication powers your global content distribution needs, compliant storage needs, and data sharing across accounts.<br/><br/>
     > **Replicate objects while retaining metadata** — If you need to ensure your replica copies are identical to the source data, you can use S3 Replication to make copies of your objects that retain all metadata, such as the original object creation time, object access control lists (ACLs), and version IDs.<br/><br/>
     > **Replicate objects to more cost-effective storage classes** — You can use S3 Replication to put objects into S3 Glacier, S3 Glacier Deep Archive, or another storage class in the destination buckets. You can also replicate your data to the same storage class and then use S3 Lifecyle policies to move your objects to a more cost-effective storage.<br/><br/>
     > **Maintain object copies under a different account** — Regardless of who owns the source object, you can tell Amazon S3 to change replica ownership to the AWS account that owns the destination bucket to restrict access to object replicas.<br/><br/>
     > **Replicate your objects within 15 minutes** — You can use Amazon S3 Replication Time Control (S3 RTC) to replicate your data in a predictable time frame. S3 RTC replicates 99.99 percent of new objects stored in Amazon S3 within 15 minutes of upload and is backed by a Service Level Agreement (SLA).
  
