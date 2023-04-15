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
   
☑️ **Exercise 2.** Deploy an application across multiple availability zones in a specific region. Use Amazon Route 53 to create a failover routing policy that redirects traffic to a healthy availability zone in the event of an outage in one of the zones.

   **ToDo:**
   - Launch EC2 instances in multiple availability zones in the region. ☑️
   - Configure a load balancer to distribute traffic across the instances. ☑️
   - Create an Amazon Route 53 record set that points to the load balancer's DNS name. ☑️
   - Configure a failover routing policy by creating a second record set that points to a secondary load balancer in another region or availability zone. ☑️
   - Configure health checks for the primary and secondary load balancers so that Route 53 can detect when an availability zone or region becomes unavailable. **_This step is chargeable._ <a href="https://www.youtube.com/watch?v=cTrVCykJ-aU"> Check this for testing</a>** ☑️
   - Set the failover routing policy to fail over to the secondary load balancer in the event of an outage in the primary region or availability zone. ☑️
   - Once you have set up this configuration, traffic will automatically be redirected to the secondary load balancer if the primary load balancer becomes unavailable due to an outage in one of the availability zones. ☑️

 --------------------------------------------
 **Exercise 3.** Create an AWS CloudFront distribution that uses multiple edge locations in different regions to deliver content to end-users. Configure the distribution to automatically route traffic to the nearest edge location, reducing latency and improving performance for end-users.
   
   **ToDo:**
   - Click the "Create Distribution" button and choose the type of distribution you want to create. For this exercise, choose the "Web" distribution type.
   - In the "Origin Settings" section, specify the origin where CloudFront should fetch content from. You can specify an S3 bucket or a custom origin, such as an EC2 instance or an Elastic Load Balancer. For example, you can specify an S3 bucket that contains your static website files as the origin.
   - In the "Default Cache Behavior Settings" section, specify how CloudFront should handle requests for content. You can configure caching behavior, specify which HTTP methods to forward to your origin, and set up security and origin access identity settings. For example, you can set the "Minimum TTL" to 0 to disable caching, and choose "HTTP and HTTPS" for the "Allowed HTTP Methods".
   - In the "Distribution Settings" section, specify the following:
      - Alternate Domain Names (CNAMEs): Optionally, specify custom domain names that you want to associate with your CloudFront distribution.
      - Price Class: Choose the price class that best suits your needs. A higher price class will give you access to more edge locations, but will be more expensive. For this exercise, choose the "Price Class 100" to have access to all edge locations.
      - SSL Certificate: Choose the SSL certificate that you want to use to secure connections to your distribution. You can either use the default CloudFront certificate or specify your own certificate.
      - Supported HTTP Versions: Choose the supported HTTP versions for your distribution. For example, you can choose "HTTP/2, HTTP/1.1, HTTP/1.0".
   - In the "Enabled Protocols and Cipher Suites" section, specify the protocols and cipher suites that you want to use for your distribution. For example, you can choose "TLSv1.2" for the protocols and "AES128-SHA256" for the cipher suites.
   - In the "Distribution State" section, choose "Enabled" to enable your distribution.
   - In the "Distribution Settings" section, under "Geolocation", select "Yes" for "Enable geolocation" and leave the default settings.
   - Under "Origins and Origin Groups", add additional origins if needed, specifying a different region for each origin. For example, you can add an S3 bucket in a different region as an additional origin.
   - Under "Behaviors", create a new behavior and specify a path pattern that should use this behavior, then choose the origin or origin group to associate with this behavior. Repeat this step for each additional behavior you need. For example, you can create a behavior for your S3 bucket origin, and another behavior for your additional S3 bucket origin in a different region.
   - Save and deploy your distribution changes.
   
   
   
   
  
   
    
    

