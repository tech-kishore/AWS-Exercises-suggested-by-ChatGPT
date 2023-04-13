# Regions & Availability Zones

# Exercises:
☑️ **Exercise 1.** Create an S3 bucket in multiple regions and configure cross-region **replication** between the buckets. Upload a file to the original bucket and verify that the file is automatically replicated to the other buckets.
   
   **ToDo:**
   - Create an S3 bucket in multiple regions ☑️
   - Configure cross-region replication between the buckets ☑️
   - Upload a file to the original bucket ☑️
   - Verify that the file is automatically replicated to the other buckets ☑️
  
   ## When to use S3 Replication 💡
   > **Data redundancy** – If you need to maintain multiple copies of your data in the same, or different AWS Regions, with different encryption types, or across different accounts. S3 Replication powers your global content distribution needs, compliant storage needs, and data sharing across accounts.<br/><br/>
   > **Replicate objects while retaining metadata** — If you need to ensure your replica copies are identical to the source data, you can use S3 Replication to make copies of your objects that retain all metadata, such as the original object creation time, object access control lists (ACLs), and version IDs.<br/><br/>
   > **Replicate objects to more cost-effective storage classes** — You can use S3 Replication to put objects into S3 Glacier, S3 Glacier Deep Archive, or another storage class in the destination buckets. You can also replicate your data to the same storage class and then use S3 Lifecyle policies to move your objects to a more cost-effective storage.<br/><br/>
   > **Maintain object copies under a different account** — Regardless of who owns the source object, you can tell Amazon S3 to change replica ownership to the AWS account that owns the destination bucket to restrict access to object replicas.<br/><br/>
   > **Replicate your objects within 15 minutes** — You can use Amazon S3 Replication Time Control (S3 RTC) to replicate your data in a predictable time frame. S3 RTC replicates 99.99 percent of new objects stored in Amazon S3 within 15 minutes of upload and is backed by a Service Level Agreement (SLA).
    
   ## When to use Cross-Region Replication 💡
   > **Meet compliance requirements** – Although Amazon S3 stores your data across multiple geographically distant Availability Zones by default, compliance requirements might dictate that you store data at even greater distances. To satisfy these requirements, use Cross-Region Replication to replicate data between distant AWS Regions.<br/><br/>
   > **Minimize latency** – If your customers are in two geographic locations, you can minimize latency in accessing objects by maintaining object copies in AWS Regions that are geographically closer to your users.<br/><br/>
   > **Increase operational efficiency** – If you have compute clusters in two different AWS Regions that analyze the same set of objects, you might choose to maintain object copies in those Regions.

   ### Resource: https://www.youtube.com/watch?v=trmicgGpmd4
   
   ### Role-Policy
   ```
   {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetReplicationConfiguration"
            ],
            "Resource": "arn:aws:s3:::cgpt-1-s3-replication-n.virginia"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "s3:GetObjectVersionTagging",
                "s3:GetObjectVersionAcl",
                "s3:GetObjectVersion"
            ],
            "Resource": "arn:aws:s3:::cgpt-1-s3-replication-n.virginia/*"
        },
        {
            "Sid": "VisualEditor2",
            "Effect": "Allow",
            "Action": [
                "s3:ReplicateObject",
                "s3:ReplicateTags",
                "s3:ReplicateDelete"
            ],
            "Resource": "arn:aws:s3:::cgpt-1-s3-replication-mumbai/*"
        }
      ]
   }
   ```
   --------------------------------------------
   
**Exercise 2.** Deploy an application across multiple availability zones in a specific region. Use Amazon Route 53 to create a failover routing policy that redirects traffic to a healthy availability zone in the event of an outage in one of the zones.

   **ToDo:**
   - Launch EC2 instances in multiple availability zones in the region. ☑️
   - Configure a load balancer to distribute traffic across the instances. ☑️
   - Create an Amazon Route 53 record set that points to the load balancer's DNS name. ☑️
   - Configure a failover routing policy by creating a second record set that points to a secondary load balancer in another region or availability zone.
   - Configure health checks for the primary and secondary load balancers so that Route 53 can detect when an availability zone or region becomes unavailable.
   - Set the failover routing policy to fail over to the secondary load balancer in the event of an outage in the primary region or availability zone.
   - Once you have set up this configuration, traffic will automatically be redirected to the secondary load balancer if the primary load balancer becomes unavailable due to an outage in one of the availability zones.
  
   
    
    

