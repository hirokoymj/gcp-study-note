# Test 1-2

**Question 151**

- D. Configure serverless VPC access. 91%
- https://cloud.google.com/vpc/docs/serverless-vpc-access#use_cases
- Your serverless environment needs to access data from your on-premises database through Cloud VPN.
- D. Configuring serverless VPC access App Engine can connect to the VPC and then through VPN tunnel to the on-prem DB

<hr />

**Question 152**

- D. 1. Use gsutil -m to upload the files to Cloud Storage. 2. Use gsutil hash -c FILE_NAME to generate CRC32C hashes of all on-premises files. 3. Use gsutil ls -L gs://[YOUR_BUCKET_NAME] to collect CRC32C hashes of the uploaded files. 4. Compare the hashes. 95%
- https://cloud.google.com/storage/docs/gsutil/commands/hash
- Calculate hashes on local files, which can be used to compare with gsutil ls -L output.

```
gsutil hash [-c] [-h] [-m] filename.
///[-c] - Calculate a CRC32c hash for the specified files.
```

<hr />

**Question 153**

- A. Install Anthos Service Mesh on your cluster. Use the Google Cloud Console to define a Service Level Objective (SLO), and create an alerting policy based on this SLO.
- https://cloud.google.com/service-mesh/docs/observability/slo-overview
- Service Level Objectives (SLOs) are a core tool in the Google service monitoring toolkit.
- **Anthos Service Mesh** lets you set SLOs for your services, and monitor and alert on your services in terms of those SLOs

<hr />

**Question 154**

- C. Create a second GKE cluster in asia-southeast1, and use kubemci to create a global HTTP(s) load balancer.

- we are introducing a new command-line interface (CLI) tool called **kubemci** to automatically configure ingress using Google Cloud Load Balancer (GCLB) for multi-cluster Kubernetes Engine environments.

```
$ kubemci create my-mci --ingress=ingress.yaml \
    --kubeconfig=cluster_list.yaml
```

<hr />

**Question 155**

- D. Create a Compute Engine instance with CPU and memory options similar to your application's current on-premises virtual machine. Install the Cloud Monitoring agent, and deploy the third-party application. Run a load test with normal traffic levels on the application, and follow the Rightsizing Recommendations in the Cloud Console. Most Voted

- https://cloud.google.com/migrate/compute-engine/docs/4.9/concepts/planning-a-migration/cloud-instance-rightsizing?hl=en
- Recommends Compute Engine instances based on the CPU and RAM currently allocated to the on-premises VM.

<hr />

**Question 156**

- C. Configure VPC Service Controls and configure Private Google Access. 100%
- https://cloud.google.com/vpc-service-controls/docs/overview

<hr />

**Question 157**

- D. Use node affinity labels based on the node name when creating Compute Engine instances in order to host each workload on the correct node.
- https://cloud.google.com/compute/docs/nodes/sole-tenant-nodes#default_affinity_labels
- D. Afinity should be set at node level, not node-group as every client has its own node in the group

![](images/157.png)

<hr />

**Question 158**

- B. Google Compute Engine managed instance groups with auto-scaling. 100%

<hr />

**Question 159**

- C. Meet with the cloud operations team and the engineer to discuss load balancer options Most Voted

- WebSocket is a computer communications protocol, providing simultaneous two-way communication channels over a single Transmission Control Protocol (TCP) connection.
- https://en.wikipedia.org/wiki/WebSocket#:~:text=The%20WebSocket%20protocol%20enables%20full,from%20and%20to%20the%20server.
- https://cloud.google.com/load-balancing/docs/https#websocket_support
- Google Cloud HTTP(S)-based load balancers have native support for the WebSocket protocol.

<hr />

**Question 160**

- D. 1. Append metadata to file body 2. Compress individual files 3. Name files with a random prefix pattern 4. Save files to one bucket
- https://cloud.google.com/storage/docs/request-rate#naming-convention

> A longer randomized prefix provides more effective auto-scaling when ramping to very high read and write rates. For example,

```
my-bucket/2fa764-2016-05-10-12-00-00/file1
my-bucket/5ca42c-2016-05-10-12-00-00/file2
my-bucket/6e9b84-2016-05-10-12-00-01/file3
```

<hr />

**Question 161**

- correct
- C - In the Logging section of the console, specify GCE Network as the logging section. Search for the Create Insert entry
- In Logs Explorer , Filter "resource.type="gce_firewall_rule" and Query insert Create

```
You would see below and email address
"methodName": "v1.compute.firewalls.insert",
"authorizationInfo": [
{
"permission": "compute.firewalls.create",
```

- GCE, network origin, SSH (firewall rule)

**Question 162**

- D. Create a snapshot of the root disk, create an image file in Google Cloud Storage from the snapshot, and create a new virtual machine instance in the US-East region using the image file the root disk. 67%, tartar
- in a different project in the US-East region.
- https://cloud.google.com/compute/docs/instances/copy-vm-between-projects
  > you have to create Image from Snapshot and share it to the destination project. Prakzz

**Question 163**

- B. Mount a Local SSD volume as the backup location. After the backup is complete, use gsutil to move the backup to Google Cloud Storage.
- Option B is the most appropriate solution in this case. Mounting a Local SSD volume as the backup location will allow the backups to be taken quickly and efficiently, as Local SSDs have very high I/O performance and low latencies. Additionally, using gsutil to move the backups to Google Cloud Storage after they have been taken will provide a secure and durable storage location for the backups. omermaH

> A, configuring a cron job to use the gcloud tool to take regular backups using persistent disk snapshots, may not be the most efficient option because persistent disks have relatively lower I/O performance compared to Local SSDs.

> C, using gcsfuse to mount a Google Cloud Storage bucket as a volume directly on the instance and writing the backups to the mounted location using mysqldump, may not be the most efficient option because the backups would need to be transferred over the network, which could impact the performance of the backups.

> D, mounting additional persistent disk volumes onto each VM instance in a RAID10 array and using LVM to create snapshots to send to Cloud Storage, may not be the most efficient option because it would require additional disk space and setup, and LVM snapshots may not be as fast as Local SSDs for taking backups.

**Question 164**

- ABF 56%
- ADF, omermaH
- A. Ensure that the load tests validate the performance of Cloud Bigtable
- B. Create a separate Google Cloud project to use for the load-testing environment
- F. Instrument the load-testing tool and the target services with detailed logging and metrics collection
- after reading link: https://cloud.google.com/bigtable/docs/performance, rishab86
  > A:Run your typical workloads against Bigtable :Always run your own typical workloads against a Bigtable cluster when doing capacity planning, so you can figure out the best resource allocation for your applications.
  > B. Create a separate Google Cloud project to use for the load-testing environment
  > F : The most important/standard factor of testing, you gather logs and metrics in TEST environment for further scaling.

**Question 165**

- B. Org viewer, project viewer 100%
- A is not correct because Project owner is too broad. The security team does not need to be able to make changes to projects.
- B is correct because:-Org viewer grants the security team permissions to view the organization's display name.
  - Project viewer grants the security team permissions to see the resources within projects.
- C is not correct because Org admin is too broad. The security team does not need to be able to make changes to the organization.
- D is not correct because Project owner is too broad. The security team does not need to be able to make changes to projects.

**Question 166**

- BE 45% omermaH, DE 37%
- B. Use source code security analyzers as part of the CI/CD pipeline Most Vot
- E. Run a vulnerability security scanner as part of your continuous-integration /continuous-delivery (CI/CD) pipeline
- D. Enable code signing and a trusted binary repository integrated with your CI/CD pipeline Most Voted

> B. Use source code security analyzers as part of the CI/CD pipeline: By using source code security analyzers as part of the CI/CD pipeline, you can automatically detect and alert on security vulnerabilities in the code as it is being developed, which can help prevent security errors from being introduced.

> E. Run a vulnerability security scanner as part of your continuous-integration /continuous-delivery (CI/CD) pipeline: By running a vulnerability security scanner as part of the CI/CD pipeline, you can automatically detect and alert on security vulnerabilities in the application as it is being deployed, which can help prevent security errors from being introduced.
> upvoted 2 times

> Option A, ensuring every code check-in is peer reviewed by a security SME, could be a good way to prevent security errors from being introduced, as peer review can help catch mistakes before they are committed. However, it may not be practical to always have a security SME available to review every code check-in, especially if the company places a high value on release speed and agility.

> Option C, ensuring you have stubs to unit test all interfaces between components, is not directly related to preventing security errors from being introduced. While unit testing can help ensure that the code is working correctly, it is not specifically focused on security.

> Option D, enabling code signing and a trusted binary repository integrated with your CI/CD pipeline, could be a good way to ensure that only trusted code is being deployed. However, it may not be sufficient on its own to prevent security errors from being introduced, as it does not directly address vulnerabilities in the code itself.

**Question 167**

- C. Update the existing Kubernetes Engine cluster with the following command: gcloud alpha container clusters update mycluster - -enable- autoscaling - -min-nodes=1 - -max-nodes=10. 100%
- To enable autoscaling for an existing node pool, run the following command: tartar

```
gcloud container clusters update cluster-name --enable-autoscaling \
--min-nodes 1 --max-nodes 10 --zone compute-zone --node-pool default-pool
```

- https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-autoscaler

**Question 168**

- A. Use Google App Engine to serve the website and Google Cloud Datastore to store user data.
- C. Use a managed instance group to serve the website and Google Cloud Bigtable to store user data. Most Voted
- by omermeH below.
  > A: Google App Engine is a fully managed platform for building and running web applications and APIs. It can automatically scale to meet high traffic demands, making it a good choice for serving the website for the promotional email campaign. Google Cloud Datastore can also scale automatically to meet high traffic demands, making it a good choice for storing user data.

> C: A managed instance group are managed as a single entity and can automatically scale up or down based on demand. This makes it a good choice for serving the website for the promotional email campaign. Google Cloud Bigtable is a fully managed, high-performance NoSQL database that can store and serve large amounts of structured data with low latency. It is designed to scale horizontally and can handle high traffic demands, making it a good choice for storing user data.

**Question 169**

- BC 65%
- B. Google Kubernetes Engine with containers
- C. Google App Engine Standard Environment
- No ops = Serverless / Almost Serverless, less operational management overhead.
  Kubernetes and App Engine are the only one that gives us that flexibility, plus is modernizing apps.alexanderC

**Question 170**

- C. Digitally sign each timestamp and log entry and store the signature. 100%
- by omermaH
  > I would recommend option C, digitally signing each timestamp and log entry and storing the signature. Digitally signing a log entry involves creating a cryptographic hash of the log entry and a timestamp, and then encrypting the hash using a private key. The encrypted hash, known as the signature, can be stored along with the log entry in a secure manner. To verify the authenticity of the log entry, you can use the public key associated with the private key used to create the signature to decrypt the signature and recreate the hash. If the recreated hash matches the original hash, it indicates that the log entry has not been tampered with and is authentic.

**Question 171**

- C. 1. Create folders under the Organization resource named ג€Developmentג€ and ג€Production.ג€ 2. Grant all developers the Project Creator IAM role on the ג€Developmentג€ folder. 3. Move the developer projects into the ג€Developmentג€ folder. 4. Set the policies for all projects on the Organization. 5. Additionally, set the production policies on the ג€Productionג€ folder. omermaH

- I would recommend option C, creating two folders under the Organization resource named "Development" and "Production" and placing developer and production projects in the respective folders. This approach would allow you to centrally manage policies for all projects, while also being able to set more restrictive policies for production projects. It would also allow you to easily move projects between the Development and Production folders as business needs change, without disrupting users or developers.

**Question 172**

- D. 1. Create a managed instance group with Compute Engine instances. 2. Create a global load balancer and configure it with two backends: ג—‹ Managed instance group ג—‹ Cloud Storage bucket 3. Enable Cloud CDN on the bucket backend. 97%

- I would recommend option D, creating a managed instance group with Compute Engine instances and a global load balancer with two backends: the managed instance group and the Cloud Storage bucket, and enabling Cloud CDN on the bucket backend. This approach would allow you to scale the number of instances in the managed instance group as needed to handle the demand for the application, and would also use the Cloud CDN to improve the performance of the application by caching the music files closer to the users. omermaH

**Question 173**

- A. Set up a filter in Cloud Logging and a Cloud Storage bucket as an export target for the logs you want to save. 100%

**Question 174**

- A. Create a Dataflow pipeline to retrieve the data from the external sources. As part of the pipeline, use the Cloud Data Loss Prevention (Cloud DLP) API to remove any PII data. Store the result in BigQuery. 74%
- I would recommend option A, creating a Dataflow pipeline to retrieve the data from the external sources and using the Cloud Data Loss Prevention (Cloud DLP) API to remove any PII data. Storing the result in BigQuery would allow the data warehousing team to easily perform analysis on the data. omermaH

**Question 175**

- A. Create an aggregated export on the Production folder. Set the log sink to be a Cloud Storage bucket in an operations project.

- Option B is not the correct solution because it creates an aggregated export on the Organization resource, which will capture logs from all projects in the Organization, including those outside the Production folder. omermaH

- Option A is the correct solution because it allows you to create an aggregated export on the Production folder, which will capture logs from all the production projects contained in the folder. Setting the log sink to a Cloud Storage bucket in an operations project will allow the operations team to store the logs in a central location. omermaH

**Question 176**

- A. 1. Install a Cloud Logging agent on all instances. 2. Create a sink to export logs into a regional Cloud Storage bucket. 3. Create an Object Lifecycle rule to move files into a Coldline Cloud Storage bucket after one month. 4. Configure a retention policy at the bucket level using bucket lock. 97%
- This approach would allow you to use Cloud Logging to collect and export the logs from the Compute Engine instances into a Cloud Storage bucket. You can then use an Object Lifecycle rule to automatically move the logs from the regional bucket to a Coldline bucket after one month, which will reduce storage costs for logs that are not actively being queried. By configuring a retention policy using bucket lock, you can ensure that the logs are retained for at least two years for audit purposes. This approach follows Google-recommended practices for storing logs and minimizing costs. omermaH

**Question 177**

- A. Configure an organization policy to restrict identities by domain. 100%
- https://cloud.google.com/resource-manager/docs/organization-policy/restricting-domains

**Question 178**

- C. Review your RowKey strategy and ensure that keys are evenly spread across the alphabet. 100%, omermaH
- https://cloud.google.com/bigtable/docs/schema-design#row-keys

**Question 179**
C. 1. Create a dataset for the data science team. 2. Create views of tables that you want to share, excluding PII. 3. Assign an appropriate project-level IAM role to the members of the data science team. 4. Assign access controls to the dataset that contains the view. 5. Authorize the view to access the source dataset. 57%

- C is correct here. You need view to avoid PII data. So materialized view is not needed.
- C: view in a different dataset (https://cloud.google.com/bigquery/docs/share-access-views: "Authorized views should be created in a different dataset from the source data. That way, data owners can give users access to the authorized view without simultaneously granting access to the underlying data.") someone2011

**Question 180**

- B. Use the Storage Transfer Service to move the data.
- https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets#transfer-options

**Question 181**

- C. Set up a Cloud Monitoring sink that triggers the Cloud Function after an instance removal log message arrives in Cloud Logging. 83%, omermaH
- Actually C is correct but Wrong also in a way .. Sink cannot trigger a cloud function directly. It need Pub/Sub which then will trigger Cloud Function. Tesla

**Question 182**

- A. Use Google Cloud Shell in the Google Cloud Console to interact with Google Cloud. 100%
- https://cloud.google.com/sdk/gcloud

**Question 183**

- C. Set up a Cloud VPN gateway in each Shared VPC and peer Cloud VPNs. 79%, omermaH
- https://cloud.google.com/architecture/best-practices-vpc-design#shared-service

**Question 184**

- A. Inspect the logs and metrics from the instances in Cloud Logging and Cloud Monitoring. 100%, omermaH
- When an application becomes slow, the first step you should take is to gather information about the underlying cause of the problem. One way to do this is by inspecting the logs and metrics from the instances where the application is deployed. Google Cloud Platform (GCP) provides tools such as Cloud Logging and Cloud Monitoring that can help you to collect and analyze this information. omermaH

**Question 185**

- A. Configure liveness and readiness probes in the Pod specification.

- A: Configuring the right liveness and readiness probes prevents outages when rolling out a new ReplicaSet of a Deployment, because Pods are only getting traffic when they are considered ready.
- B: With GKE, you do not deal with MIGs.
- C: Does not use GKE tools and is therefore not the best option.
- D: Does alert you but does not prevent the outage.
- https://www.youtube.com/watch?v=mxEvAPQRwhw

**Question 186**

- C. Configure a HorizontalPodAutoscaler for all stateless workloads and for all compatible stateful workloads. Configure the cluster to use node auto scaling. 100%
- Answer C. Use HorizontalPodAutoscaler.

**Question 187**

- B 73%, D 23% omermaH
- D. 1. Activate billing export into BigQuery. 2. Perform a BigQuery query on the billing table to extract the information you need. 23%, omermaH

<blockquote>

- Go to the Billing page of your Google Cloud project.
- In the top left and select "billing Export."
- Follow the prompts to enable billing export and specify the BigQuery dataset and table where you want the data to be exported.
- Perform a BigQuery query on the billing table: Once you have enabled billing export and the data has started flowing into the specified BigQuery table, you can run a query on the table to extract the information you need. For example, you could use a query like the following to get the total cost of queries split by user:

```
SELECT user, SUM(cost) as total_cost
FROM `your-project.your-dataset.billing_export`
GROUP BY user
ORDER BY total_cost DESC
```

</blockquote>

**Question 188**

- A. Set up a network peering between vpc-a and vpc-b. 100%
- https://cloud.google.com/vpc/docs/vpc-peering
  > Google Cloud VPC Network Peering allows internal IP address connectivity across two Virtual Private Cloud (VPC) networks regardless of whether they belong to the same project or the same organization.

**Question 189**

- B. Object Versioning. 100%
- https://cloud.google.com/storage/docs/object-versioning

**Question 190**

- D. Change the filter to metric.label.state = 'free' and the Target utilization to 20. 16%, omermaH
- free is an available state filter for the percent_used metric. MortaW
- https://cloud.google.com/compute/docs/autoscaler/scaling-cloud-monitoring-metrics#autoscale_based_on_memory_usage

<blockquote>
[AMEJack]We have to think in different way.

- Option A: TARGET_TYPE: the autoscaler calculates the average rate of growth per minute and compares that to the utilization target.
  This will not fit question requirments, only the memory utilization growth will be compared with the target value.
- Option C: Adding all the memory cached, buffer, used and free will always be constant. So, this will also not fit the question requirements.
- Option D: I want the "free" memory utilization will be around 20. This will solve the problem.

</blockquote>

**Question 191**

- A. An HA Cloud VPN gateway connected with two tunnels to an on-premises VPN gateway. 81%
- A can provide 99.99% availability as well, and no need for C which will be more expensive. alexandE
- https://cloud.google.com/network-connectivity/docs/vpn/concepts/topologies#1-peer-1-address

**Question 192**

- A. 1. Set a CORS configuration in the target Cloud Storage bucket where the base URL of the App Engine application is an allowed origin. 2. Use the Cloud Storage Signed URL feature to generate a POST URL. 100%
- https://cloud.google.com/storage/docs/cross-origin#server-side-support
- Signed URL is for TIme-Based access. This needs access all the time.

**Question 193**

- B. Configure Cloud NAT and select sub-b in the NAT mapping section. 100%

<blockquote>

- A -> It doesn't make sense, Public Google Access allows you to access Google APIs without an external IP, which doesnt solve the problem
- C -> Bastion host is for the opposite purpose; accessing a machine administratively from the outside without an external IP, not a machine without an external IP accessing the outside.
- D -> It doesn't make sense.
- B -> It's the recommended solution for GCP

</blockquote>

**Question 194**

- D 100%

<blockquote>

1. Create an image of the on-premises virtual machines.
2. Import the image as a virtual disk on Compute Engine using --os=windows-2022-dc-v.
3. Create a sole-tenancy instance on Compute Engine that uses the imported disk as a boot disk.

</blockquote>

- https://cloud.google.com/compute/docs/import/importing-virtual-disks

**Question 195**

- A. An HA Cloud VPN gateway connected with two tunnels to an on-premises VPN gateway. 100%
- HA VPN supports two tunnels to achieve 99.99%. Classic VPN does not. Any more than 2 tunnels is excessive cost.
- https://cloud.google.com/network-connectivity/docs/vpn/how-to/creating-ha-vpn2

| on-prem - GCP |                     |
| ------------- | ------------------- |
| classic VPN   |                     |
| HA VPN        | 99.99%, two tunnels |

<hr />

**Question 196**

- Duplicate so review question #146
