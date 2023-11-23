# Udemy Test 6

**Question 1 Dress4Win**

- D. Identify the number of virtual cores and RAM associated with the application server virtual machines align them to a custom machine type in the cloud, monitor performance, and scale the machine types up until the desired performance is reached.　 58％
- A - not correct. as its talking about Physical server size
- B - not correct. as we its talking about Max spec
- C - not correct. as its talking about the Smallest spec
- D - is CORRECT. as its recommending to map with on premises app VM Size

<hr />

**Question 2**

- A. Build or leverage an OAuth-compatible access control system。100％
- SAML is an authentication system. OAuth is an authorization system.
- Both can be used with SSO (Single sign on). SAML is for users and OAuth is more for applications.
- https://cloud.google.com/docs/authentication

<hr />

**Question 3 TerramEarth**

- B. Capacity planning, TCO calculations, opex/capex allocation. 92%
- From the case study, it can conclude that Management (CXO) all concern rapid provision of resources (infrastructure) for growing as well as cost management, such as Cost optimization in Infrastructure, trade up front capital expenditures (Capex) for ongoing operating expenditures (Opex), and Total cost of ownership (TCO)

<hr />

**Question 4 TerramEarth**

- AC 92%
- A. Open a support case regarding the CVE and chat with the support engineer.
- C. Read the CVEs from the Google Cloud Platform Security Bulletins to understand the impact.
- https://cloud.google.com/support/bulletins

<hr />

**Question 5 TerramEarth**

- A. Request Transfer Appliances from Google Cloud, export the data to appliances, and return the appliances to Google Cloud. 83%
- It will take 123 days to transfer
- The right answer is to use Transfer Appliance
  https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets#time

<hr />

**Question 6 Dress4Win**

- A. Google Cloud Storage Coldline to store the data, and gsutil to access the data.
- **Infrequently** accessed data
- https://cloud.google.com/storage/docs/storage-classes#coldline
- Coldline storage is a very-low-cost, highly durable storage service for storing infrequently accessed data.

<hr />

**Question 7 Dress4Win**

- A. Use regional managed instance groups and a global load balancer to increase performance because the regional managed instance group can grow instances in each region separately based on traffic.
- Creating MIGs across regions behind a GLB, gives HA across Zones and Regions.

<hr />

**Question 8 TerramEarth**

- C. Create a BigQuery time-partitioned table for the European data, and set the partition expiration period to 36 months. For Cloud Storage, use gsutil to enable lifecycle management using a DELETE action with an Age condition of 36 months. 86%

When you create a table partitioned by ingestion time, BigQuery automatically loads data into daily, date-based partitions that reflect the data's ingestion or arrival time.

Ref: https://cloud.google.com/bigquery/docs/partitioned-tables#ingestion_time

And Google recommends you configure the default table expiration for your datasets, configure the expiration time for your tables, and configure the partition expiration for partitioned tables.

Ref: https://cloud.google.com/bigquery/docs/best-practices-storage#use_the_expiration_settings_to_remove_unneeded_tables_and_partitions

If the partitioned table has a table expiration configured, all the partitions in it are deleted according to the table expiration settings. For our specific requirement, we could set the partition expiration to 36 months so that partitions older than 36 months (and the data within) are automatically deleted.

Ref: https://cloud.google.com/bigquery/docs/managing-partitioned-tables#partition-expiration

<hr />

**Question 9 TerramEarth**

- D. Have the vehicle's computer compress the data in hourly snapshots, and store it in a GCS Coldline bucket Most Voted
- D is most cost effective as don't want to use until 'next year'

<hr />

**Question 10 Dress4Win**

- B. In the Cloud Platform Console download the list of the uptime servers' IP addresses and create an inbound firewall rule. 64%
- Uptime check monitoring
- Correct answer is B. https://cloud.google.com/monitoring/uptime-checks/using-uptime-checks#monitoring_uptime_check_list_ips-console
- It would be missing firewall rule that would be causing problem.

<hr />

**Question 11**

- B. They should add additional unit tests and production scale load tests on their cloud staging environment. 100%
- A - Not Correct. Developer can debug the problem, but cannot _prevent_ the outage.
- B - Correct. Developers are responsible for writing unit tests. They already have end-to-end tests for _endpoints_ but nothing mentioned about the unit tests. Cloud will auto-scale but you need to define your auto-scaling configuration (desired count, max count etc) and production scale load test will help you to configure the auto-scaling policies
- C - Not Correct. They already have end-to-end test. Running it on staging environment will not prevent an outage
- D - Not Correct. Answers says "an impact the new release causes to latency" but question ask for preventing an outage and so this one is ruled out

<hr />

**Question 12 TerramEarth**

- D. Use Cloud Dataprep and configure the BigQuery tables as the source. Schedule a daily job to clean the data. 100%
- **Cloud Dataprep** is an intelligent data service for visually exploring, cleaning, and preparing structured and unstructured data for analysis, reporting, and machine learning. https://cloud.google.com/dataprep
- **Cloud Dataproc** is a fast, easy-to-use, fully managed cloud service for running Apache Spark and Apache Hadoop clusters in a simpler way. https://cloud.google.com/dataproc?hl=en
- **Dataflow** is a managed service for executing a wide variety of data processing patterns. https://cloud.google.com/dataflow?hl=en

<hr />

**Question 13 TerramEarth**

- B. Make func_query 'Require authentication.' Create a unique service account and associate it to func_display. Grant the service account invoker role for func_query. Create an id token in func_display and include the token to the request when invoking func_query. 100%

- For 1st gen functions, the invoker role is Cloud Functions Invoker (roles/cloudfunctions.invoker)

```
gcloud functions add-iam-policy-binding RECEIVING_FUNCTION \
  --member='serviceAccount:CALLING_FUNCTION_IDENTITY' \
  --role='roles/cloudfunctions.invoker'
```

- https://cloud.google.com/functions/docs/securing/authenticating#authenticating_function_to_function_calls

<hr />

**Question 14 TerramEarth's**

- B. Capture all operating data, train machine learning models that identify ideal operations, and run locally to make operational adjustments automatically. 100%
- Run Locally -> That's exactly what gcp ca, provide:
  https://cloud.google.com/blog/products/gcp/bringing-intelligence-edge-cloud-iot

<hr />

**Question 15 TerramEarth**

- B. Deploy Cloud Run services to multiple regions. Create serverless network endpoint groups pointing to the services. Add the serverless NEGs to a backend service that is used by a global HTTP(S) Load Balancing instance. 95%

- Cloud Run is a regional service. To serve global users you need to configure a Global HTTP LB and NEG as the backend. Cloud Run services are deployed into individual regions and to route your users to different regions of your service, you need to configure external HTTP(S) Load Balancing.

- https://cloud.google.com/run/docs/multiple-regions

- A network endpoint group (NEG) specifies a group of backend endpoints for a load balancer. A serverless NEG is a backend that points to a Cloud Run, App Engine, or Cloud Functions service.

- https://cloud.google.com/load-balancing/docs/negs/serverless-neg-concepts

<hr />

**Question 16**

- A. Configure a trigger in Cloud Build for new source changes. Invoke Cloud Build to build container images for each microservice, and tag them using the code commit hash. Push the images to the Container Registry. 95%
- https://cloud.google.com/architecture/best-practices-for-building-containers#tagging_using_the_git_commit_hash

<hr />

**Question 17 Dress4Win**

- A. Grant the operations engineer access to use Google Cloud Shell. 100%

<hr />

**Question 18 TerramEarth**

- B. Vehicles write data directly to Google Cloud Pub/Sub. 100%
- We need to buffer, the default limit of BigQuery is 100 API calls per second, till now this cannot be changed. Hence we should ease using Pub/Sub so B.

- To handle the volume of data that TerramEarth plans to ingest, it is recommended to use a scalable and reliable data ingestion solution such as Google Cloud Pub/Sub. With Cloud Pub/Sub, the vehicles can stream data directly to the service, which can handle the high volume of data and provide a buffer to absorb sudden spikes in traffic. The data can then be processed and stored in a data warehouse such as BigQuery for analysis.

- Option A (writing data directly to GCS) may not be suitable for handling high volumes of data in real-time and may result in data loss if the volume exceeds the capacity of GCS.
- Option C (streaming data directly to BigQuery) may not be suitable for handling high volumes of data in real-time as it may result in data loss or ingestion delays.
- Option D (continuing to write data using the existing system) may not be suitable as the current system may not be able to handle the increased volume of data and may result in data loss or ingestion delays.

<hr />

**Question 19 Dress4Wm**

- A. Store image files in a Google Cloud Storage bucket. Use Google Cloud Datastore to maintain metadata that maps each customer's ID and their image files. 100%
- I think it's A, because in the question says "The customer has exclusive control over who may view these images"
  And I think it is easier to develop this feature having in cloud datastore a NOSQL database where you can manage the control of file's viewer

<hr />

**Question 20**

- C. Create a Cloud Monitoring uptime check to validate the application URL. If it fails, put a message in a Pub/Sub queue that triggers a Cloud Function to switch the URL to the "Site is unavailable" page, and notify the Ops team. 100%
- Cloud monitoring for Uptime check to validate the application URL and leverage pub/sub to trigger Cloud Function to switch URL
- https://cloud.google.com/monitoring/uptime-checks?hl=e

<hr />

**Question 21 Dress4Win**

- C. Monitoring, Logging, Alerts, Error Reporting. 53%/ME
- D. Monitoring, Logging, Debug, Error Report. 47%
- With D you cannot achieve "Their administrators are notified automatically when their application reports errors."
- However, with Error Reporting (Log insights) - Notifies you when new errors are detected. So, perfect option is C.

<hr />

**Question 22 Dress4Win**

- C. Hadoop/Spark deployed using Cloud Dataproc Regional in High Availability mode. 100%
- Google Cloud includes Dataproc, which is a managed Hadoop and Spark environment. You can use Dataproc to run most of your existing jobs with minimal alteration, so you don't need to move away from all of the Hadoop tools you already know.

<hr />

**Question 23 Dress4Win**

- D. Use the Activity page in the GCP Console and Stackdriver Logging to provide the required insight.
- https://cloud.google.com/logging/docs/audit/
- Admin Activity audit logs contain log entries for API calls or other administrative actions that modify the configuration or metadata of resources. For example, these logs record when users create VM instances or change Identity and Access Management permissions. To view these logs, you must have the IAM role Logging/Logs Viewer or Project/Viewer.

<hr />

**Question 24 TerramEarth**

- B. Cloud IoT Core with public/private key pairs
- https://cloud.google.com/iot-core/
- IoT Core was developed for connecting existing devices spread around the world to GCP. Also, it supports end-to-end security using asymmetric key authentication over TLS 1.2. So, this is exact match for this question.

<hr />

**Question 25**

- AC 100%
- A. Treat every micro service call between modules on the vehicle as untrusted.
- C. Use a trusted platform module (TPM) and verify firmware and binaries on boot.
- B is not correct because IPv6 doesn't have any impact on the security during vehicle operation, although it improves system scalability and simplicity.
- D is not correct because merely using a functional programming language doesn't guarantee a more secure level of execution isolation. Any impact on security from this decision would be incidental at best.
- E is not correct because this improves system durability, but it doesn't have any impact on the security during vehicle operation.
- F is not correct because it doesn't have any impact on the security during vehicle operation, although it improves system durability.

<hr />

**Question 26 Dress4Win**

- A. Deploy Nginx and Tomcat using Cloud Deployment Manager to Compute Engine. Deploy a Cloud SQL server to replace MySQL. Deploy Jenkins using Cloud Deployment Manager.
- The requriements also specify:
  "Easily create non-production environment in the cloud.
  Implement an automation framework for provisioning resources in cloud.
  Implement a continuous deployment process for deploying applications to the on-premises datacenter or cloud."
  So A is better.

<hr />

**Question 27 Dress4Win**

- C. Create a Cloud Storage Transfer Service Job to copy the files to a Coldline Storage bucket.
- https://cloud.google.com/storage-transfer/docs/transfer-options
- We recommend using Storage Transfer Service to move or back up your data from other cloud storage providers to Cloud Storage.
  - Amazon S3
  - Microsoft Azure Blob Storage

<hr />

**Question 28 Dress4Win**

- A. Identify self-contained applications with external dependencies as a first move to the cloud. 82%
- To become familiar with deploying applications to the cloud, it is recommended to start with simple, self-contained applications with external dependencies that can be easily moved to the cloud. These applications are likely to have fewer dependencies on other components in the infrastructure and can be migrated with minimal effort, helping the team to get comfortable with the cloud deployment process. Once the team has gained experience with the cloud deployment process, they can gradually move more complex applications with internal dependencies to the cloud.

<hr />

**Question 29**

- C. Increase fleet cellular connectivity to 80%, migrate from FTP to streaming transport, and develop machine learning analysis of metrics. 59%
- C is right choice because using cellular connectivity will greatly improve the freshness of data used for analysis from where it is now, collected when the machines are in for maintenance. Streaming transport instead of periodic FTP will tighten the feedback loop even more. Machine learning is ideal for predictive maintenance workloads.

<hr />

**Question 30**

- D. Directly transfer the files to a different Google Cloud **Regional** Storage bucket location in US, EU, and Asia using Google APIs over HTTP(S). Run the ETL process to retrieve the data from each Regional bucket. 72%
- C. Directly transfer the files to different Google Cloud **Multi-Regional** Storage bucket locations in US, EU, and Asia using Google APIs over HTTP(S). Run the ETL process using the data in the bucket. 28%
- D - https://cloud.google.com/storage/docs/locations#considerations

  - Regional: 200 Gbps (per region, per project)
  - Multi-regional: 50 Gbps (per region, per project)

- Sending Data to all Multi Region Buckets >> Incurs more cost , More Latency
- Sending Data only to Regional Bucket >> Incurs less cost , Less Latency

<hr />
