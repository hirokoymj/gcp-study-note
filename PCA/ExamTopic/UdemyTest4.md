# Practice Test 4

**Question 1**

- D. 1. Create a managed instance group with Compute Engine instances. 2. Create a global load balancer and configure it with two backends: ג—‹ Managed instance group ג—‹ Cloud Storage bucket 3. Enable Cloud CDN on the bucket backend. M

**Explanation**

- This solution will improve the performance of the application by: Automatically scaling the number of Compute Engine instances to meet demand.
- Distributing traffic across multiple instances to reduce load on each instance. Caching popular songs in memory to reduce the number of times that they need to be loaded from Cloud Storage.

- Using a global load balancer to distribute traffic evenly across all regions. Using Cloud CDN to deliver files to users from a location that is closer to them. This solution is the most efficient and cost-effective way to improve the performance of the application.

- [Set up CDN](https://cloud.google.com/cdn/docs/using-cdn)
  > Cloud CDN works with the global external Application Load Balancer and the classic Application Load Balancer to deliver content to your users
- [Cloud CDN overview](https://cloud.google.com/cdn/docs/overview)
  > Cloud CDN (Content Delivery Network) uses Google's global edge network to serve content closer to users,

![](images4/1.png)

<hr />

**Question 2**

- D. 1. Append metadata to file body 2. Compress individual files 3. Name files with a random prefix pattern 4. Save files to one bucket Most Voted
- https://cloud.google.com/storage/docs/request-rate#naming-convention

> Auto-scaling of an index range can be slowed when using sequential names, such as object keys based on a sequence of numbers or timestamp. This occurs because requests are constantly shifting to a new index range, making redistributing the load harder and less effective.

> In order to maintain a high request rate, avoid using sequential names. Using completely random object names gives you the best load distribution

```
my-bucket/2016-05-10-12-00-00/file1
my-bucket/2016-05-10-12-00-00/file2
my-bucket/2016-05-10-12-00-01/file3
```

```
my-bucket/2fa764-2016-05-10-12-00-00/file1
my-bucket/5ca42c-2016-05-10-12-00-00/file2
my-bucket/6e9b84-2016-05-10-12-00-01/file3
```

<hr />

**Question 3**

- B. Use source code security analyzers as part of the CI/CD pipeline Most Voted
- E. Run a vulnerability security scanner as part of your continuous-integration /continuous-delivery (CI/CD) pipeline Most VotedMost Voted
- https://cloud.google.com/kubernetes-engine/docs/concepts/best-practices-continuous-integration-delivery-kubernetes
- continuous integration and continuous delivery (CI/CD)
- Continuous integration (CI) is a practice in which developers integrate all their code changes back into a main branch as often as possible.
- Continuous delivery (CD) lets you release code at any time.

<hr />

**Question 4**

- D. 1. Use gsutil -m to upload the files to Cloud Storage. 2. Use gsutil hash -c FILE_NAME to generate CRC32C hashes of all on-premises files. 3. Use gsutil ls -L gs://[YOUR_BUCKET_NAME] to collect CRC32C hashes of the uploaded files. 4. Compare the hashes. Most Voted

- Explanation
  Calculate hashes on local files, which can be used to compare with gsutil ls -L output. If a specific hash option is not provided, this command calculates all gsutil-supported hashes for the files. Note that gsutil automatically performs hash validation when uploading or downloading files, so this command is only needed if you want to write a script that separately checks the hash. If you calculate a CRC32c hash for files without a precompiled crcmod installation, hashing will be very slow. See gsutil help crcmod for details.

- https://cloud.google.com/storage/docs/gsutil/commands/hash
- https://cloud.google.com/storage/docs/uploading-objects#gsutil
- https://cloud.google.com/storage/docs/gsutil/commands/cp

- If you have a large number of files to transfer, you can perform a parallel multi-threaded/multi-processing copy using the top-level gsutil -m option (see gsutil help options):

```
gsutil -m
gsutil hash -c FILE_NAME
```

<hr />

**Question 5**

- A. Use Google Cloud Shell in the Google Cloud Console to interact with Google Cloud. Most Voted
- https://cloud.google.com/sdk/gcloud

<hr />

**Question 6**

- C. Digitally sign each timestamp and log entry and store the signature
- https://stackoverflow.com/questions/3829546/how-can-i-digitally-sign-logs-to-ensure-that-they-have-not-been-modified

**Explanation**

C (Correct answer) - Digitally sign each timestamp and log entry and store the signature. Answer A, B, and D don’t have any added value to verify the authenticity of your logs. Besides, Logs are mostly suitable for exporting to Cloud storage, BigQuery, and PubSub. SQL database is not the best way to be exported to nor store log data.

More Explanation: To verify the authenticity of your logs if they are tampered with or forged, you can use a certain algorithm to generate digest by hashing each timestamp or log entry and then digitally sign the digest with a private key to generate a signature. Anybody with your public key can verify that signature to confirm that it was made with your private key and they can tell if the timestamp or log entry was modified. You can put the signature files into a folder separate from the log files. This separation enables you to enforce granular security policies.

<hr />

**Question 7**

- B. Use the Data Transfer appliance to perform an offline migration. 48%
- D. Compress the data and upload it with gsutil -m to enable multi-threaded copy 43%
- Answer is B. Transfer appliance
- According to https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets
  > The expected turnaround time for a network appliance to be shipped, loaded with your data, shipped back, and rehydrated on Google Cloud is 20 days. If your online transfer timeframe is calculated to be substantially more than this timeframe, consider Transfer Appliance.
- [Transfer Appliance for larger transfers](https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets#transfer_appliance_for_larger_transfers)
- For large-scale transfers (especially transfers with limited network bandwidth), Transfer Appliance is an excellent option

<hr />

**Question 8**

- C. Set up a Cloud VPN gateway in each Shared VPC and peer Cloud VPNs.79%
- looks like the following best practice: https://cloud.google.com/architecture/best-practices-vpc-design#shared-service

  Cloud VPN is another alternative. Because Cloud VPN establishes reachability through managed IPsec tunnels, it doesn't have the aggregate limits of VPC Network Peering. Cloud VPN uses a VPN Gateway for connectivity and doesn't consider the aggregate resource use of the IPsec peer. The drawbacks of Cloud VPN include increased costs (VPN tunnels and traffic egress), management overhead required to maintain tunnels, and the performance overhead of IPsec.

![](images4/8.png)

<hr />

**Question 9**

- C. Configure VPC Service Controls and configure Private Google Access. 100%
- C is the recommended one https://cloud.google.com/vpc-service-controls/docs/overview

**Explanation**

To secure data from exfiltration by malicious insiders, compromised code or accidental oversharing, we use VPC Service controls

https://cloud.google.com/vpc-service-controls/docs/overview

For private access options, connect to services in VPC networks we use private service endpoints or VPC network peering.

https://cloud.google.com/vpc/docs/private-access-options#connect-services

<hr />

**Question 10**

- B. Develop the application for App Engine standard environment. 100%
- https://cloud.google.com/appengine/docs/the-appengine-environments#compare_high-level_features
- Standard environment, Scale to zero, YES
- Flexible environment, Scale to zero, NO

<hr />

**Question 11**

- C. Create a second GKE cluster in asia-southeast1, and use kubemci to create a global HTTP(s) load balancer. 76%
- https://cloud.google.com/blog/products/gcp/how-to-deploy-geographically-distributed-services-on-kubernetes-engine-with-kubemci
- used kubemci to create a single GCLB instance to stitch the services together.
- Multi cluster Ingress(MCI)
  ![](images4/11.png)

<hr />

**Question 12**

- D. Create a snapshot of the root disk, create an image file in Google Cloud Storage from the snapshot, and create a new virtual machine instance in the US-East region using the image file the root disk. 67%
- https://cloud.google.com/compute/docs/instances/copy-vm-between-projects
- snapshot -> image

```
gcloud compute snapshots create SNAPSHOT_NAME \
    --source-disk SOURCE_DISK \
    --snapshot-type SNAPSHOT_TYPE \
    --source-disk-zone SOURCE_DISK_ZONE
```

```
gcloud compute images create IMAGE_NAME \
    --source-snapshot=SOURCE_SNAPSHOT \
    [--storage-location=LOCATION]
```

<hr />

**Question 13**

- B. Mount a Local SSD volume as the backup location. After the backup is complete, use gsutil to move the backup to Google Cloud Storage. 76%

**Ans: B**

Persistent Disk snapshot not required: "They need to take backups of a specific database at regular intervals."

"The backup activity needs to complete as quickly as possible and cannot be allowed to impact disk performance."

This can be achieved by using both Local SSD & GCS Fuse (mounting GCS as directory), but as the question stats needs to complete as quickly as possible.

General Rule: Any addition of components introduce a latency. I could not get write throughput of GCS & Local SSD, even if we consider both provides same throughput, streaming data through network to GCS Bucket introduce latency. Attached Local SSD has advantage in this case, since there is no network involved.

From **Local SSD to GCS bucket** - copy job does not impact the mysql data disk.

<hr />

**Question 14**

- B. Google Kubernetes Engine with containers 65%
- C. Google App Engine Standard Environment
- I would go with B&C - Cloud-native, less-ops and auto-scaling all get addressed

**BC :**
No-ops means you cannot use Compute Engines as they are simple VMs.

Kubernetes is nearly no-ops (remains some operations like nodes updates, but all-in-all Google manages nearly all the operations)
App Engine is truely no-ops

<hr />

**Question 15**

- B. Create a key with Cloud Key Management Service (KMS). Set the encryption key on the bucket to the Cloud KMS key. 83%

- [Key rotation](https://cloud.google.com/storage/docs/encryption/customer-managed-keys#key-rotation)

- Cloud KMS supports both automatic and manual key rotation to a new version.

<hr />

**Question 16**

- B. Use the Storage Transfer Service to move the data. 100%(my answer too)
- 10 TB of data in an object storage service from a third-party provider -> source might be AWS/Azur -> so B.

![](images4/16.png)

<hr />

**Question 17**

- B. Google Compute Engine managed instance groups with auto-scaling. 100%
- B, https://cloud.google.com/compute/docs/autoscaler/
- Changing the tests as little as possible rules out C & D. Test takes several hours and you need to improve perfromace. Autocaling with MIG will do it, Unmanaged group cannot autosacle. Load balancer will not improve perfromance

<hr />

**Question 18**

- C. Review your RowKey strategy and ensure that keys are evenly spread across the alphabet. 100%
- [Schema design best practices - Rowkey](https://cloud.google.com/bigtable/docs/schema-design#row-keys)

  > Design your row key based on the queries you will use to retrieve the data. Well-designed row keys get the best performance out of Bigtable. The most efficient Bigtable queries retrieve data using one of the following:

- The RowKey is used to sort data within a Cloud Bigtable cluster.

<hr />

**Question 19**

- C. 1. Create folders under the Organization resource named Development and Production. 2. Grant all developers the Project Creator IAM role on the Development folder. 3. Move the developer projects into the Development folder. 4. Set the policies for all projects on the Organization. 5. Additionally, set the production policies on the Production folder. 97%

- C, because managing multiple organizations is not a Google best practice.

<hr />

**Question 20**

- C. Update the existing Kubernetes Engine cluster with the following command: gcloud alpha container clusters update mycluster - -enable- autoscaling - -min-nodes=1 - -max-nodes=10. 100%

- [Enabling autoscaling for an existing node pool](https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-autoscaler#enable_autoscaling)

```
gcloud container clusters update cluster-name --enable-autoscaling \
--min-nodes 1 --max-nodes 10 --zone compute-zone --node-pool default-pool
```

- Cluster is already running so use update instead of create new cluster.

<hr />

**Question 21**

- A. Use a load testing tool to simulate the expected number of concurrent users and total requests to your application, and inspect the results. 84%
- It is A. You want to TEST the deployment, not changing anything (yet).
- A load testing tool can be used to simulate the expected number of concurrent users and total requests to your application. This will allow you to test how your application handles the expected load and to identify any potential problems.

- Enabling autoscaling on the GKE cluster and enabling horizontal pod autoscaling on your application deployments will not help you to test the latency of your application. This will only help to ensure that your application can handle the expected load.

<hr />

**Question 22**
C. 1. Attach a regional SSD persistent disk to the first instance. 2. In case of a zone outage, force-attach the disk to the other instance. 90%

- [Manage failures for regional Persistent Disk](https://cloud.google.com/compute/docs/disks/repd-failover)
  Regional Persistent Disk is a storage option that provides synchronous replication of data between two zones in a region. You can use regional Persistent Disk as a building block when you implement high availability (HA) services in Compute Engine.

<hr />

**Question 23**

- A. Set up a filter in Cloud Logging and a Cloud Storage bucket as an export target for the logs you want to save. 100%

- [Create a sink](https://cloud.google.com/logging/docs/export/configure_export_v2#creating_sink)
  - **Cloud Logging bucket**: Select or create a Logging bucket.
  - **BigQuery table**: Select or create the particular dataset to receive the routed logs. You also have the option to use partitioned tables.
  - **Cloud Storage bucket**: Select or create the particular Cloud Storage bucket to receive the routed logs.
  - **Pub/Sub topic**: Select or create the particular topic to receive the routed logs.
  - **Splunk**: Select the Pub/Sub topic for your Splunk service.
  - **Other project**: Populate the Sink destination field as described in Destination path formats.

<hr />

**Question 24**

- B. Org viewer, project viewer. 100%
- A is not correct because Project owner is too broad. The security team does not need to be able to make changes to projects.
- B is correct because: Org viewer grants the security team permissions to view the organization's display name.
  Project viewer grants the security team permissions to see the resources within projects.
- C is not correct because Org admin is too broad. The security team does not need to be able to make changes to the organization.
- D is not correct because Project owner is too broad. The security team does not need to be able to make changes to projects.

<hr />

**Question 25**

- C. Meet with the cloud operations team and the engineer to discuss load balancer options. 100%
- [LB - WebSocket support](https://cloud.google.com/load-balancing/docs/https#websocket_support)
- Google Cloud HTTP(S)-based load balancers have native support for the WebSocket protocol when you use HTTP or HTTPS as the protocol to the backend.

<hr />

**Question 26**

- D. Store the data in a Cloud Storage bucket. Design the processing pipelines to retrieve the data from the bucket. 100%
- D, store RAW unstructured data as-is in Cloud Storage, and then define how to process it.
  Classical Data Lake ELT (Extract -> Load -> Transform )
- https://cloud.google.com/architecture/big-data-analytics/analytics-lakehouse

<hr />

**Question 27**

- C. Set up a Cloud Monitoring sink that triggers the Cloud Function after an instance removal log message arrives in Cloud Logging. 79%
- https://cloud.google.com/compute/docs/shutdownscript#limitations
  Compute Engine executes shutdown scripts only on a best-effort basis.

- In this scenario, you want to ensure that the commands in the shutdown script are run reliably every time an instance is shut down. One way to do this is by setting up a Cloud Monitoring sink that triggers a Cloud Function after an instance removal log message arrives in Cloud Logging. This will allow you to use the Cloud Function to perform the necessary tasks (such as removing database entries) when an instance is shut down, and it will ensure that these tasks are performed reliably and consistently.

- Option A: Modifying the shutdown script to wait for 30 seconds before triggering the Cloud Function is not a reliable solution, as it relies on the shutdown script being able to run for at least 30 seconds before the instance is shut down.

<hr />

**Question 28**

- D. Import a key in Cloud KMS. Create a dataset in BigQuery using the customer-supplied key option and select the created key. 100%
- The answer is easy. It says keys must be left outside of Google Cloud.
  This automatically eliminates A / B.
  Now the C option says decrypts before storing it in BigQuery which the point is to encrypt the data while been in BigQuery, D is the only possible answer.

<hr />

**Question 29**

- D. Configure a Kubernetes autoscaling deployment based on the subscription/num_undelivered_messages metric. 100%
- [Cloud Pub/Sub - Monitor message backlog](https://cloud.google.com/pubsub/docs/monitoring#monitoring_the_backlog)

  To ensure that your subscribers are keeping up with the flow of messages, create a dashboard. The dashboard can show the following backlog metrics, aggregated by resource, for all your subscriptions:

- subscription/num_undelivered_message

![](images4/29.png)

<hr />

**Question 30**

- D. Create a Compute Engine instance with CPU and memory options similar to your application's current on-premises virtual machine. Install the Cloud Monitoring agent, and deploy the third-party application. Run a load test with normal traffic levels on the application, and follow the Rightsizing Recommendations in the Cloud Console. 70%

- [Cloud instance rightsizing](https://cloud.google.com/migrate/compute-engine/docs/4.9/concepts/planning-a-migration/cloud-instance-rightsizing?hl=en)

**Rightsizing provides two types of recommendations:**

1. Performance-based recommendations: Recommends Compute Engine instances based on the CPU and RAM currently allocated to the on-premises VM. This recommendation is the default.

2. Cost-based recommendations: Recommends Compute Engine instances based on:
   **The current CPU and RAM configuration of the on-premises VM.**

<hr />**Question 31**
<hr />**Question 32**
<hr />**Question 33**
<hr />**Question 34**
<hr />**Question 35**
<hr />**Question 36**
<hr />**Question 37**
<hr />**Question 38**
<hr />**Question 39**
<hr />**Question 40**

<hr />**Question 41**
<hr />**Question 42**
<hr />**Question 43**
<hr />**Question 44**
<hr />**Question 45**
