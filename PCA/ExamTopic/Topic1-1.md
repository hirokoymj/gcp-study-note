# Exam Topic

**Question 1**

- D. Use separate backend pools for each API path behind the load balancer. 100%
- D is the answer because HTTP(S) load balancer can direct traffic reaching a single IP to different backends based on the incoming URL.
- A is not correct because configuring a new load balancer would require a new or different SSL and DNS records which conflicts with the requirements to keep the same SSL and DNS records.
- B is not correct because it goes against the requirements. The company wants to keep the old API available while new customers and testers try the new API.
- C is not correct because it is not a requirement to decommission the implementation behind the old API.

<hr />

**Question 2**

- A. Load data into Google BigQuery
- To optimize the storage of the multi-petabyte data set for ease of analysis by business analysts who have experience only with using a SQL interface, you should load the data into Google BigQuery.

- BigQuery is a fully-managed, cloud-native data warehouse that allows you to perform fast SQL queries on large amounts of data. By loading the data into BigQuery, you can provide your business analysts with a familiar SQL interface for querying the data, making it easier for them to analyze the data set.

- Other options, such as inserting data into Google Cloud SQL, putting flat files into Google Cloud Storage, or streaming data into Google Cloud Datastore, may not provide the necessary SQL interface or query performance for efficient analysis of the data set.

<hr />

**Question 3**

- Correct option is CDE.
  C. Instrument the application with a monitoring tool like Stackdriver Debugger: A monitoring tool like Stackdriver Debugger can help in identifying and debugging issues that arise during the migration process. It can also provide insights into the performance and availability of the application after it has been migrated to the cloud.

- D. Select an automation framework to reliably provision the cloud infrastructure: Automating the provisioning of the cloud infrastructure can help ensure that the process is reliable and repeatable. It can also help reduce the risk of errors and increase the speed of the migration process.

- E. Deploy a continuous integration tool with automated testing in a staging environment: Deploying a continuous integration tool with automated testing in a staging environment can help ensure that the application is thoroughly tested before it is deployed to production. This can help reduce the risk of issues arising in production and provide greater confidence in the stability and reliability of the application.

<hr />

**Question 4**

- A is correct option.
- App Engine spins up new containers automatically according to the load. During peak traffic, HTTP requests originated by the same user could be served by different containers. Given that the variable `sessions` is recreated for each container, it might store different data. The problem here is that this Flask app is stateful. The `sessions` variable is the state of this app. And stateful variables in App Engine / Cloud Run / Cloud Functions are problematic. A solution would be to store the session in some database (e.g., Firestore, Memorystore) and retrieve it from there. This way the app would fetch the session from a single place and would be stateless.

<hr />

**Question 5**

- A should good.
- Stackdriver is Google's logging solution. The answer wouldn't be to find another viable 3rd party logging solution.

<hr />

**Question 6**

- AC is correct.

D) and E) are pointless in this context.

C) is certainly a good practice.

Between A) and B):

A) Blue green deployment is an application release model that gradually transfers user traffic from a previous version of an app or microservice to a nearly identical new release—both of which are running in production.

B) In software, a canary process is usually the first instance that receives live production traffic about a new configuration update, either a binary or configuration rollout. The new release only goes to the canary at first. The fact that the canary handles real user traffic is key: if it breaks, real users get affected, so canarying should be the first step in your deployment process, as opposed to the last step in testing in production. " While both green-blue and canary releases are useful, (B) suggests "replacing QA" with canary releases - which is not good. QA got the issue down by 80%.

Hence (A) and (C) are correct.

<hr />

**Question 7**

- AD 63%
- Use the flag -no-auto-delete with this flag, the disk won't be deleted when the VM is terminated.
- https://cloud.google.com/compute/docs/images/create-custom#gcloud
- By default, the auto-delete option is enabled on the boot disks.
- Billing export to BigQuery enables you to export your daily usage and cost estimates automatically throughout the day to a BigQuery dataset you specify. You can then access your billing data from BigQuery.

<hr />

**Question 8**

- B
- This is time series data. We also have no idea what kinds of data are being captured so it doesn't appear structured.

A does not seem reasonable because a flat file is not easy to query and analyze.

B seems reasonable because this accommodates unstructured data.

C seems unreasonable because we have no idea on the structure of the data.

D seems unreasonable because there is no such Google database type.

<hr />

**Question 9**

- C. Ensure that a firewall rule exists to allow load balancer health checks to reach the instances in the instance group. 100%

- Explanation
  If curl command is working then traffic exists. So, we need to check why health checks are failing. So, firewall issues for health check done by Google probers

<hr />

**Question 10**

- C. Create a new service account with BigQuery access and execute your script with that user
- Explanation
  Service accounts provide a way to authenticate your application to Google Cloud services. When you create a service account, you can assign it specific roles that dictate what resources the service account can interact with, and how it can interact with them. In this case, you would assign the BigQuery access role to the service account, which would then be used to authenticate your script to BigQuery.

<hr />

**Question 11**

- B. Federate authentication via SAML 2.0 to the existing Identity Provider Most Voted
- Explanation
  For this scenario, the most appropriate authentication strategy would be B. Federate authentication via SAML 2.0 to the existing Identity Provider. This approach can achieve single sign-on and will not cause too much disruption to existing users. Additionally, since there are strict security team requirements, SAML federated authentication can ensure the security of password storage and transmission.

Other options may cause issues with security and user experience, such as

option A, which may lead to security issues with password synchronization,

option C, which may require password reassignment,

option D, which may cause user confusion or forgotten passwords.

<hr />

**Question 12**

- B. Google Cloud Dataflow
- Explanation
  These options include a mix of batch and stream processing – points to Dataflow.

<hr />

**Question 13**

- C. Roll back to an earlier known good release initially, then use Stackdriver Trace and Logging to diagnose the problem in a development/test/staging environment 95%
- Explanation
  App engine gives flexibility to roll back to previous version. Priority should be restoring the services to working state. And trace the issue using Stackdriver where the logs are already captured from previous failed service.

<hr />

**Question 14**

- Explanation
  Increasing the size of the persistent disk can be done without requiring the virtual machine to be shut down, and the resize2fs command can be used to resize the ext4 filesystem on the disk to take advantage of the additional space. This will allow you to add more storage space to the virtual machine without disrupting the database service.

<hr />

**Question 15**

- A. Create a tokenizer service and store only tokenized data
- Explanation
  Tokenization is a process of replacing sensitive data, such as credit card numbers, with unique, randomly-generated tokens that cannot be used for fraudulent purposes. By using a tokenizer service and storing only tokenized data, you can reduce the scope of PCI compliance to only the tokenization service, rather than the entire application. This can help minimize the amount of sensitive data that needs to be protected and reduce the overall compliance burden.

<hr />

**Question 16**

- B. Google Cloud Bigtable
- Explanation
  Google Cloud Bigtable is a scalable, high-performance NoSQL database that is well-suited for storing large amounts of data with low latency. It is designed for high-throughput workloads such as streaming data, and is able to handle bursts of up to millions of reads and writes per second.

<hr />

**Question 17**

- B. Write a lifecycle management rule in JSON and push it to the bucket with gsutil
- Explanation
  Cloud Storage has lifecycle management rules and could be applied with gsutil and gcloud storage buckets. It is common to use JSON for transferring data.

<hr />

**Question 18**

- B. Google Cloud Dataproc
- Explanation
  Dataproc is a fully managed and highly scalable service for running Apache Hadoop, Apache Spark, Apache Flink, Presto, and 30+ open source tools and frameworks. Use Dataproc for data lake modernization, ETL, and secure data science, at scale, integrated with Google Cloud, at a fraction of the cost.
- https://cloud.google.com/dataproc

<hr />

**Question 19**

- C. Dynamically resize the SSD persistent disk to 500 GB
- Explanation
  Answer is C because persistent disk performance is based on the total persistent disk capacity attached to an instance and the number of vCPUs that the instance has. Incrementing the persistent disk capacity will increment its throughput and IOPS, which in turn improve the performance of MySQL.

<hr />

**Question 20**

- C. Google Cloud Bigtable
- Explanation
  To optimize the performance of an accurate, real-time, weather-charting application that receives data from 50,000 sensors sending 10 readings per second, it would be most appropriate to store the data in a distributed, horizontally scalable, NoSQL database such as Google Cloud Bigtable Other options, such as Google BigQuery, Google Cloud SQL, and Google Cloud Storage, may not be as well-suited for handling high volumes of real-time data and may not provide the same level of performance and scalability as Google Cloud Bigtable.

<hr />

**Question 21**

- B. Create synthetic random user input, replay synthetic load until autoscale logic is triggered on at least one layer, and introduce ג€chaosג€ to the system by terminating random resources on both zones
- Explanation
  By creating synthetic random user input and replaying the load, you can simulate the expected increased user traffic and trigger the autoscale logic on different layers of the application. Introducing chaos to the system by terminating random resources in both zones helps test the resiliency and redundancy of the system under stress. This strategy will help ensure that the system can maintain the 99.99% availability SLA when subjected to additional user load.

**Question 22**

- C. Use a slimmed-down base image like Alpine Linux Most Voted
- E. Copy the source after he package dependencies (Python and pip) are installed
- Explanation
  C: Smaller the base image with minimum dependency faster the container will start

E: Docker image build uses caching. Docker Instructions sequence matter because application’s dependencies change less frequently than the Python code which will help to reuse the cached layer of dependency and only add new layer for code change for Python Source code.

**Question 23**

- C. Increase the load on your test and staging environments Most Voted
- Explanation
  You want to avoid this problem, which you can only do if you load test, it in a test environment. With option A, B and D you might find the problem and the solution faster (or not since it's a performance problem), but you do not avoid the problem.

**Question 24**

- D. Instrument your application with Stackdriver Trace in order to break down the request latencies at each microserviceD. Instrument your application with Stackdriver Trace in order to break down the request latencies at each microservice
- Explanation
  Stackdriver Trace is a distributed tracing system that allows you to understand the relationships between requests and the various microservices that they touch as they pass through your application. By instrumenting your application with Stackdriver Trace, you can get a detailed breakdown of the latencies at each microservice, which can help you identify which service is taking the longest in those cases where a small number of API requests take a very long time.

**Question 25**

-　 D. Implement routinely scheduled failovers of your databases 　 64％ -　 Explanation
Option D, implementing routinely scheduled failovers of your databases, is the best option in this scenario. This ensures that if the primary database crashes, the replica will automatically be promoted to the master and take over database operations, preventing any downtime or data loss. This can be achieved by setting up automatic failover mechanisms or by manually promoting the replica to the master as soon as the primary database goes down.

**Question 26**

- D. Configure Stackdriver Monitoring for all Projects, and export to Google Cloud Storage.
- Explanation
  D is correct and best practice for long term log storage

**Question 27**

- A. Google Cloud Dedicated Interconnect. 100%
- Explanation
  VPN is not private; it is public but encrypted. Also, VPN is not suitable for large updates that happen frequently

Google Cloud Dedicated Interconnect - large updates and better security, however may not be the most cost effective choice

**Question 28**

- B. Enable Logging export to Google BigQuery and use ACLs and views to scope the data shared with the auditor. 67%
- Explanation
  https://cloud.google.com/iam/docs/job-functions/auditing#scenario_external_auditors

B complies with requirements <analysis and audit> you can audit from GCS but not analyze the data in it, that is done by BQ

**Question 29**

- C. In a secret management system Most Voted
- Explanation
  It is important to store the credentials for your database back-end securely in order to protect them from unauthorized access. One way to do this is by using a secret management system, such as Google Cloud's Secret Manager. Secret Manager is a secure and convenient storage system for API keys, passwords, and other sensitive data that is designed to protect against unauthorized access. By storing the credentials in Secret Manager, you can ensure that they are kept secure and can be easily accessed by your microservices as needed.

**Question 30**

- C. Cloud Deployment Manager is unfamiliar to the company's engineers
- F. Cloud Deployment Manager only supports automation of Google Cloud resources
- Explanation
  C. Cloud Deployment Manager is unfamiliar to the company's engineers: This may lead to a learning curve and potential delays or mistakes in deployment, as the team becomes familiar with the new system.

  F. Cloud Deployment Manager only supports automation of Google Cloud resources: If the company has a multi-cloud or hybrid cloud environment, the custom tool might need to be adapted or additional tools might be required for managing resources in other cloud environments or on-premises infrastructure.

**Question 31**

- A. Google Kubernetes Engine, Jenkins, and Helm. 69%
- Explanation
  It should be A. Helm is needed for "Deploy application bundles using dynamic templates" Load Balancing should be part of GKE Already.

**Question 32**

- C. Create a shutdown script and use it as the value for a new metadata entry with the key shutdown-script in the Cloud Platform Console when you create the new virtual machine instance. 60%
- Explanation
  You can create and apply shutdown script for running VM too.

https://cloud.google.com/compute/docs/shutdownscript#provide_shutdown_script_contents_directly

**Question 33**

- D. Add tags to each tier and set up firewall rules to allow the desired traffic flow. 100%
- Explanation
  The web tier can communicate with end users and the app tier, and the app tier can communicate with the database tier, but no other communication between tiers is allowed. The instances running the web tier have a network tag of web, the instances running the app tier have a network tag of app, and the instances running the database tier have a network tag of db.

**Question 34**

- A. Use Stackdriver Logging to search for the module log entries
- C. Use gcloud or Cloud Console to connect to the serial console and observe the logs
- E. Adjust the Google Stackdriver timeline to match the failure time, and observe the batch server metrics
- Explanation
  To collect details on the failure of the batch servers in GCE VMs, you can take the following actions:

A - Stackdriver Logging can help you identify any issues related to the new Linux kernel module by searching for log entries related to the module.

C - Connecting to the serial console allows you to view the logs in real-time as the batch servers are running. This can help you identify any issues related to the new kernel module.

E - By adjusting the timeline in Stackdriver to match the failure time, you can view the batch server metrics during the time when the failures occurred. This can help you identify any issues related to the new kernel module.

Other options, such as reading the debug GCE Activity log using the API or Cloud Console, identifying whether a live migration event of the failed server occurred, or exporting a debug VM into an image and running the image on a local server, may not provide the necessary information to understand

**Question 35**

- A. Load logs into Google BigQuery
- E. Upload log files into Google Cloud Storage
- Explanation
  If you want to analyze those logs its recommended Big Query. For storing and backup Cloud Storage is your option, so AE.

**Question 36**

- B. Revert the source code change, and rerun the deployment pipeline. 61%
- Explanation
  If a change negatively affects your key performance indicator, it's best to revert the source code change to a known good state and rerun the deployment pipeline. This ensures that your infrastructure is restored to a stable state while you investigate and fix the issue. Reverting the change and redeploying the code will allow your instance groups to continue functioning with the previous stable version, minimizing the impact on your application and users.

**Question 37**

- C. A single Organization with Folders for each department. 100%
- Explanation
  To control IAM policies for different departments independently but centrally, you should create a single organization and use folders to organize the policies for each department. This approach allows you to centralize the management of IAM policies for all departments within a single organization, while also allowing you to set up different policies for each department as needed.

**Question 38**

- B. Digitally sign all of your JAR files and redeploy your application
- Explanation
  The most likely cause of the error is that one of the JAR files in your application has been tampered with or is corrupt. The SHA1 digest error indicates that the JAR file's signature does not match the expected value, which could be due to tampering or corruption.

  To fix the issue, you should try uploading missing JAR files and redeploying your application. If the issue persists, you may need to digitally sign all of your JAR files and redeploy your application to ensure that the signatures are valid. You should not try to recompile the Cloaked

<hr />

**Question 39**

- C. Use public key infrastructure (PKI) to encrypt the message client side using the originating user's private key.

- Explanation
  To prevent message spoofing, it is important to ensure that messages cannot be altered or forged by anyone other than the originating user. One way to accomplish this is by using public key infrastructure (PKI) to encrypt messages using the originating user's private key.

<hr />

**Question 40**

- B. Configure a Google Cloud Dedicated Interconnect.
- Explanation
  It's latency issue. That won't be solved by adding another VPN tunnel. If it was just a throughput issue then VPN would do, however to improve latency you need to go layer 2. Answer is B

<hr />

**Question 41**

- C. De-identify the data with the Cloud Data Loss Prevention API
- Explanation
  The recommended approach for sanitizing data of personally identifiable information or payment card information before storing it in Cloud Bigtable is option C: De-identify the data with the Cloud Data Loss Prevention API.

  The Cloud Data Loss Prevention (DLP) API is a powerful tool that allows you to automatically discover, classify, and redact sensitive data in your organization. It uses advanced machine learning techniques to accurately identify and protect a wide range of sensitive data types, including personal information such as names, addresses, phone numbers, and payment card information.

<hr />

**Question 42**

- A. ~/bin
- Explanation
  https://cloud.google.com/shell/docs/how-cloud-shell-works

  Cloud Shell provisions 5 GB of free persistent disk storage mounted as your $HOME directory on the virtual machine instance. This storage is on a per-user basis and is available across projects. Unlike the instance itself, this storage does not time out on inactivity. All files you store in your home directory, including installed software, scripts and user configuration files like .bashrc and .vimrc, persist between sessions. Your $HOME directory is private to you and cannot be accessed by other users.

<hr />

**Question 43**

- A. Create a VPC and connect it to your on-premises data center using Dedicated Interconnect.
- Explanation
  Cloud VPN supports unto 3 Gbps where as Interconnect can support unto 100 gbps

<hr />

**Question 44**

- B. Utilize free tier and sustained use discounts. Provide training to the team about service cost management. 100%
- Explanation
  Sustained are automatic discounts for running specific GCE a significant portion of the billing month:

  https://cloud.google.com/compute/docs/sustained-use-discounts

  Committed is for workloads with predictable resource needs between 1 year or 3 year, discount is up to 57% for most resources:

  https://cloud.google.com/compute/docs/instances/signing-up-committed-use-discounts

<hr />

**Question 45**

- D. Use Jenkins to monitor tags in the repository. Deploy staging tags to a staging environment for testing. After testing, tag the repository for production and deploy that to the production environment.

- https://stackify.com/continuous-delivery-git-jenkins/

- The question states: "... code changes can be verified BEFORE deploying to production", it eliminates option C.
  The approach of tagging is the correct practise that DevOps use
- Correct answer is D. Question talks about 'before deploying to production'. C talks about after deploying to production.

<hr />

**Question 46**

- C. Disable the health check for the instance group. Add his SSH key to the project-wide SSH Keys. 83%
- C, is the correct answer. As per the requirement linux expert would need access to VM to troubleshoot the issue.
- With health check enabled, old VM will be terminated as soon as health-check fails for the VM and new VM will be auto-created. So, this situation will prevent linux expert to troubleshoot the issue.

<hr />

**Question 47**

- C. GKE and GCP provide the tools you need to build a PCI DSS-compliant environment. 100%
- https://cloud.google.com/security/compliance/pci-dss
  Clearly mention GKE as PCI DSS-Compliant but not all GCP service are PCI DSS-Compliant so answer is definitely C.
- Payment Card Industry (PCI) Data Security Standards (DSS)

<hr />

**Question 48**

- B. Upload your files into Cloud Storage. Use Cloud Dataprep to explore and clean your data. 100%

- Cloud Dataprep is a fully managed data preparation service that allows you to quickly and easily explore, clean, and transform your data for analysis.
- "detect anomalies" <<-Very important.

<hr />

**Question 49**

- C. The effective policy is the union of the policy set at the node and policies inherited from its ancestors. 100%
- intersection, the intersection of the policy set

<hr />

**Question 50**

- C. Use an IP range on Google Cloud that does not overlap with the range you use on-premises. 85%
- https://cloud.google.com/vpc/docs/using-vpc
- "Primary and secondary ranges can't conflict with on-premises IP ranges if you have connected your VPC network to another network with Cloud VPN, Dedicated Interconnect, or Partner Interconnect."

<hr />

**Question 51**

- A. Point gcloud datastore create-indexes to your configuration file. 100%
- https://cloud.google.com/sdk/gcloud/reference/datastore/indexes/create

<hr />

**Question 52**

- C. Deploy the application on two Compute Engine instance groups, each in the same project but in a different region. Use the first instance group to serve traffic, and use the HTTP load balancing service to fail over to the standby instance group in case of a disaster

- Explanation
  Google recommend using MIG for Zonal outage and multiple MIG for regional outage

  https://cloud.google.com/architecture/disaster-recovery#compute-engine

  It says: Compute Engine instances are zonal resources, so in the event of a zone outage instances are unavailable by default. Compute Engine does offer managed instance groups (MIGs) which can automatically scale up additional VMs from pre-configured instance templates, both within a single zone and across multiple zones within a region. MIGs are ideal for applications that require resilience to zone loss and are stateless, but require configuration and resource planning. Multiple regional MIGs can be used to achieve regional outage resilience for stateless applications.

<hr />

**Question 53**

- D. Deploy your application on App Engine flexible environment and use Cloud VPN to limit access to the on-premises database

- https://cloud.google.com/appengine/docs/the-appengine-environments
- Accesses the resources or services of your Google Cloud project that reside in the Compute Engine network.
- https://stackoverflow.com/questions/37137914/is-it-possible-to-use-google-app-engine-with-google-cloud-vpn

> App Engine Flexible Environment is based on Google Compute Engine and consequently can connect to your remote network via Cloud VPNs. As described in this article, you can specify network settings in your app.yaml configuration file of your GAE Flexible application.

<hr />

**Question 54**

- A. Upload the required installation files to Cloud Storage. Configure the VM on a subnet with a Private Google Access subnet. Assign only an internal IP address to the VM. Download the installation files to the VM using gsutil. 78%
- https://cloud.google.com/vpc/docs/configure-private-google-access
- you can follow these steps:
- Upload the required installation files to Cloud Storage.
  Configure the VM on a subnet with a Private Google Access subnet. This will allow the VM to access Google APIs and services, such as Cloud Storage, without requiring a public IP address or internet access.
  Assign only an internal IP address to the VM. This will ensure that the VM is not accessible from the public internet.
  Download the installation files to the VM using gsutil, which is a command-line tool that allows you to access Cloud Storage from the VM.

<hr />

**Question 55**

- A. Move your data onto a Transfer Appliance. Use a Transfer Appliance Rehydrator to decrypt the data into Cloud Storage.
- Explanation
  The gsutil tool is the standard tool for small- to medium-sized transfers (less than a few TB)

  https://cloud.google.com/solutions/migration-to-google-cloud-transferring-your-large-datasets#transfer-options

  Transfer Appliance lets you quickly and securely transfer large amounts of data to Google Cloud Platform via a high-capacity storage server that you lease from Google and ship to Google’s datacenter. Transfer Appliance is recommended for data that exceeds 20 TB or would take more than a week to upload.

<hr />

**Question 56**

- A. Use `kubectl set image deployment/echo-deployment` <new-image>
- Selected A - Source: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment

- Deployment ensures that only a certain number of Pods are down while they are being updated. By default, it ensures that at least 75% of the desired number of Pods are up (25% max unavailable).

- Deployment also ensures that only a certain number of Pods are created above the desired number of Pods. By default, it ensures that at most 125% of the desired number of Pods are up (25% max surge).

<hr />

**Question 57**

- C. Add all users to a group. Grant the group the roles of BigQuery jobUser on the billing project and BigQuery dataViewer on the projects that contain the data. 100%

- Both A & C are correct but using the principle of least privileges C is the most appropriate.

- **BigQuery User**: (roles/bigquery.user) - When applied to a dataset, this role provides the ability to read the dataset's metadata and list tables in the dataset.
  When applied to a project, this role also provides the ability to run jobs, including queries, within the project. A principal with this role can enumerate their own jobs, cancel their own jobs, and enumerate datasets within a project. <b>Additionally, allows the creation of new datasets within the project; the creator is granted the BigQuery Data Owner role(roles/bigquery.dataOwner) on these new datasets.</b>
  Lowest-level resources where you can grant this role: Dataset

- **BigQuery Job User:** (roles/bigquery.jobUser) - Provides permissions to run jobs, including queries, within the project.
  Lowest-level resources where you can grant this role: Project

- https://cloud.google.com/bigquery/docs/access-control

<hr />

**Question 58**

- B. Have users upload the images to Cloud Storage using a signed URL that expires after 24 hours. 100%
- https://cloud.google.com/storage/docs/access-control/signed-urls

<hr />

**Question 59**

- D. Define a design for the security of data in your web application that meets GDPR requirements. 100%
- Explanation
  D - https://cloud.google.com/security/gdpr

  The GDPR lays out specific requirements for businesses and organizations who are established in Europe or who serve users in Europe. It regulates how businesses can collect, use, and store personal data Builds upon current documentation and reporting requirements to increase accountability Authorizes fines on businesses who fail to meet its requirements

<hr />

**Question 60**

- A. Configure a Cloud SQL instance with high availability enabled. 53%
- https://cloud.google.com/sql/docs/sqlserver/high-availability
- High availability feature is available in cloud SQL.
  We dont have to create compute instance, install SQL server and place the db and log file in group of windows compute engine machines with failover clustering. Always chose readymade services from GCP.
- https://cloud.google.com/compute/docs/instances/sql-server/disaster-recovery-for-microsoft-sql-server#high_availability_and_disaster_recovery

<hr />

**Question 61**

- B. Use gcloud to create a Kubernetes cluster. Use kubectl to create the deployment. 100%
- Explanation
  Create a Google Kubernetes Engine (GKE) cluster: You can use the Google Cloud Console or the gcloud command-line tool to create a GKE cluster, which will provide the underlying infrastructure for running your application.

Deploy the application to the cluster: You can use the kubectl command-line tool to apply the Kubernetes Deployment file provided by the development team to the cluster.

kubectl apply -f deployment.yaml

**Question 62**

- B. Allocate budget for team training. Create a roadmap for your team to achieve Google Cloud certification based on job role.
- Explanation
- To evaluate your team's readiness for a new GCP project and create a skills gap plan, you should consider the business goal of cost optimization. One way to optimize costs is to invest in training for your team to increase their skills and knowledge of GCP. This can help your team become more efficient and effective in using GCP, potentially resulting in cost savings over time. You should allocate budget for team training and create a roadmap for your team to achieve Google Cloud certification based on their job roles. This will help ensure that your team has the necessary skills and knowledge to successfully deploy the new GCP project.

**Question 63**

- A. Cloud Functions 93%
- Explanation
  - A. Cloud Functions - managed service scales down to 0
  - B. Compute Engine - not a managed service
  - C. Google Kubernetes Engine - not a managed service and wont scale down to 0
  - D. App Engine flexible environment - managed service but won’t scale down to 0

**Question 64**

- A. Create the Key object for each Entity and run a batch get operation
- Explanation
  Correct Answer: A Create the Key object for each Entity and run a batch get operation https://cloud.google.com/datastore/docs/best-practices

  Use batch operations for your reads, writes, and deletes instead of single operations. Batch operations are more efficient because they perform multiple operations with the same overhead as a single operation. Firestore in Datastore mode supports batch versions of the operations which allow it to operate on multiple objects in a single Datastore mode call. Such batch calls are faster than making separate calls for each individual entity because they incur the overhead for only one service call. If multiple entity groups are involved, the work for all the groups is performed in parallel on the server side.

**Question 65**

- A. Supply the encryption key in a .boto configuration file. Use gsutil to upload the files. 71%
- Explanation
  In GCP document, key could be configured in .boto. No information found which shows gsutil suppots flag "--encryption-key".
  https://cloud.google.com/storage/docs/encryption/customer-supplied-keys

**Question 66**

- B. Output custom metrics to Stackdriver from the game servers, and create a Dashboard in Stackdriver Monitoring Console to view them. 97%

- Explanation
  To capture multiple GBs of aggregate real-time KPIs from game servers running on Google Cloud Platform and monitor them with low latency, the customer should output custom metrics to Stackdriver from the game servers. Stackdriver allows you to collect and store custom metrics, as well as view and analyze them in real-time using the Stackdriver Monitoring Console. The customer can create a Dashboard in the Monitoring Console to view the KPIs and monitor them with low latency.

**Question 67**

- C. Perform the following: 1. Create a Google Kubernetes Engine (GKE) cluster with n1-standard-1 type machines. 2. Build a Docker image from the production branch with all of the dependencies, and tag it with the version number. 3. Create a Kubernetes Deployment with the imagePullPolicy set to 'IfNotPresent' in the staging namespace, and then promote it to the production namespace after testing. 67%

- Explanation
  Using Google Kubernetes Engine (GKE) enables better resource management and allows you to monitor and maximize machine utilization effectively. Creating a Docker image with all the dependencies ensures a consistent environment for your application. By utilizing Kubernetes Deployments, you can reliably deploy new versions of the application and control the rollout process. Additionally, using a staging namespace for testing before promoting to the production namespace ensures a safer deployment process.

**Question 68**

- B. Use Google Cloud Directory Sync to synchronize Active Directory usernames with cloud identities and configure SAML SSO. 100
  %
- Explanation
  To retain their on-premises Active Directory domain controller for identity management while using Google Cloud resources, the company can use Google Cloud Directory Sync to synchronize Active Directory usernames with cloud identities and configure SAML single sign-on (SSO). This will allow users to use their existing Active Directory credentials to access Google Cloud resources, while still maintaining their on-premises Active Directory domain controller as the primary source of identity management.

**Question 69**

- B. Review the Stackdriver logs for the specific GKE container that is serving the unresponsive part of the application.
- Explanation
  Since the application writes logs to standard output, the logs should be available in the Stackdriver logs for the container running the unresponsive part of the application. Kubernetes Engine automatically exports these logs to Stackdriver, so you can use the Stackdriver Logging console to view the logs.

**Question 70**

- D. Create a failover replica instance in the same region, but in a different zone. 53%
- Explanation
  Cloud SQL is regional. For high availability, we need to think fo a failover strategy. So, Option D meets the requirement. create failover replica in the same region but in different Zone

**Question 71**

- C. Create a custom image from the existing disk. Create an instance template from the custom image. Create an autoscaled managed instance group from the instance template. 100%
- Explanation
  Option C is the correct choice because creating a custom image from the existing disk ensures that the application environment is consistent and does not change between instances, which can reduce variability in performance. Creating an instance template from the custom image allows you to easily create new instances that are based on the same image, which can save time and effort. Finally, creating an autoscaled managed instance group allows you to automatically scale the number of instances based on demand, which can ensure that there are enough instances to handle peak traffic while minimizing costs during periods of low traffic

**Question 72**

- B. Use firewall rules based on network tags attached to the compute instances
- Explanation
  Right Option - B. Use firewall rules based on network tags attached to the compute instances

  To restrict communications between VM instances within a VPC without relying on static IP addresses or subnets, you can use firewall rules based on network tags attached to the compute instances. This will allow you to specify which instances are allowed to communicate with each other and on which paths and ports. You can then attach the relevant network tags to the compute instances when they are created, allowing you to control communication between the instances without relying on static IP addresses or subnets.

**Question 73**

- A. 1. Enable automatic storage increase for the instance. 2. Create a Stackdriver alert when CPU usage exceeds 75%, and change the instance type to reduce CPU usage. 3. Create a Stackdriver alert for replication lag, and shard the database to reduce replication time.

- https://cloud.google.com/sql/docs/mysql/instance-settings#automatic-storage-increase-2ndgen

**Enable automatic storage increases**

If you enable this setting, Cloud SQL checks your available storage every 30 seconds. If the available storage falls below a threshold size, Cloud SQL automatically adds additional storage capacity. If the available storage repeatedly falls below the threshold size, Cloud SQL continues to add storage until it reaches the maximum of 64 TB.

<hr />

**Question 74**

- D. BigQuery, because it is designed for large-scale processing of tabular data
- Explanation. 94%
  Cloud SQL/Spanner is OLTP DB but not OLAP. BQ is a well-known OLAP for analytics and also supports RBMS feature too

**Question 75**

- C. In the GCP Console, navigate to Stackdriver Logging. Consult logs for (GKE) and Cloud SQL.
- Explanation
  Post mortem always includes log analysis.
  post mortem = logs

**Question 76**

- A. Ensure that VM service accounts are granted the appropriate Cloud Pub/Sub IAM roles.
- Explanation
  The Google-recommended way for your application to authenticate to Cloud Pub/Sub and other Google Cloud services when running on Compute Engine VMs is to use VM service accounts. VM service accounts are automatically created when you create a Compute Engine VM, and they are associated with the VM instance. To authenticate to Cloud Pub/Sub and other Google Cloud services, you should ensure that the VM service accounts are granted the appropriate IAM roles.

**Question 77**

- D. Deploy Cloud VPN Gateway in each region. Ensure that each region has at least one VPN tunnel to the on-premises peer gateway.

- Cloud VPN Gateway is a regional service, not global.

- https://cloud.google.com/vpn/docs/how-to/creating-static-vpns

- Cloud VPN Gateway is regional. NOt Global

```
gcloud compute vpn-gateways create GW_NAME \
--network=NETWORK \
--region=REGION
```

<hr />

**Question 78**

- B. Make the tables time-partitioned, and configure the partition expiration at 45 days. 100%
- Explanation
  If your tables are partitioned by date, the dataset's default table expiration applies to the individual partitions. You can also control partition expiration using the time_partitioning_expiration flag in the bq command-line tool or the expiration configuration setting in the API. When a partition expires, data in the partition is deleted but the partitioned table is not dropped even if the table is empty.

  https://cloud.google.com/bigquery/docs/best-practices-storage

**Question 79**

- A. Configure a HorizontalPodAutoscaler with a target CPU usage. Enable the Cluster Autoscaler from the GCP Console. Most Voted
- Explanation
  How does Horizontal Pod Autoscaler work with Cluster Autoscaler? Horizontal Pod Autoscaler changes the deployment's or replicaset's number of replicas based on the current CPU load. If the load increases, HPA will create new replicas, for which there may or may not be enough space in the cluster. If there are not enough resources, CA will try to bring up some nodes, so that the HPA-created pods have a place to run. If the load decreases, HPA will stop some of the replicas. As a result, some nodes may become underutilized or completely empty, and then CA will terminate such unneeded nodes.

**Question 80**

- B. Verify that Dedicated Interconnect can replicate files to GCP. Verify that Cloud VPN can establish a secure connection between your networks if Dedicated Interconnect fails. 100%

- Explanation
  Dedicated Interconnect is a connection that provides a private, dedicated connection between your on-premises network and GCP over a Google-owned network. It is a secure and reliable option for connecting your on-premises network to GCP. You can use it to replicate files to GCP as a part of your disaster recovery plan. If Dedicated Interconnect fails for any reason, it is a good idea to have a backup solution in place to establish a secure connection between your networks. Cloud VPN is a secure and reliable solution for establishing a connection between your on-premises network and GCP. It uses a virtual private network (VPN) tunnel to securely connect the networks, and it is a good backup option if Dedicated Interconnect fails.

**Question 81**

- B. Provision preemptible VMs to reduce cost. Disable and then discontinue use of all GCP services and APIs that are not HIPAA-compliant. 94%
- Disabling and then discontinuing allows you to see the effects of not using the APIs, so you can gauge (check) alternatives. So that leaves B and D as viable answers. The question says only some are not time-critical which implies others are. This means preemptible VMs are good because they will secure a spot for scaling when needed.

<hr />

**Question 82**

- C. Schedule a disaster simulation exercise during which you can shut off all VMs in a zone to see how your application behaves. 42%
- Resilience testing of their authentication layer means the testing of availability of service/application even when many of the instances fail in a particular location. That’s why. Disaster type of scenario is better where all VM instances becomes unavailable in a particular zone.
- Chaos testing is to shutdown random instances.

<hr />

**Question 83**

- D. Use Cloud Audit Logging to view Cloud Audit Logs, and create a filter on the query operation to get the required information.

- Cloud Audit Logging records activities and API calls in Google Cloud services, including BigQuery. You can use Cloud Audit Logging to view logs and filter them based on specific operations, such as queries in BigQuery. By filtering on the query operation, you can gather the required information about how many queries each user ran in the last month, which is essential for audit purposes.

- https://cloud.google.com/bigquery/docs/reference/auditlogs#auditdata_examples

<hr />

**Question 84**

- B. Create a custom VM image with all OS package dependencies. Use Deployment Manager to create the managed instance group with the VM image.

- Managed instance groups are a way to manage a group of Compute Engine instances as a single entity. If you want to automate the creation of a managed instance group, you can use tools such as Terraform, Deployment Manager, or Puppet to automate the process. **To minimize the startup time for new VMs in the instance group, you should create a custom VM image with all of the OS package dependencies pre-installed**. This will allow you to create new VMs from the custom image, which will significantly reduce the startup time compared to installing the dependencies on each VM individually. You can then use Deployment Manager to create the managed instance group with the custom VM image.
- https://cloud.google.com/compute/docs/images

**Question 85**

- A. Create a group per country. Add analysts to their respective country-groups. Create a single group 'all_analysts', and add all country-groups as members. Grant the 'all_analysts' group the IAM role of BigQuery jobUser. Share the appropriate dataset with view access with each respective analyst country-group. Most Voted

- **BigQuery Job User (roles/bigquery.jobUser): **
  Provides permissions to run jobs, including queries, within the project.

- A: As all analysts need to execute query, they need JobUser role.
  They should be restricted to view all datasets (not tables) of respective country.

<hr />

**Question 86**

- B. Memcache backed by Cloud Datastore for the customer session state data. Lifecycle-managed Cloud Storage for log archives, thumbnails, and VM boot/data volumes. 68%
- Explanation
  Local SSD cannot be used for neither boot nor data. This rules out other options except B.

**Question 87**

- A. StatefulSets
- Explanation
  StatefulSets is a feature of Kubernetes, which the question asks about. Yes, Persistent volumes are required by StatefulSets https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/

  See the Google documentations for mentioning of hostnames https://cloud.google.com/kubernetes-engine/docs/concepts/statefulset

**Question 88**

- A. Customize the cache keys to omit the protocol from the key. 60%
- https://cloud.google.com/cdn/docs/best-practices#using_custom_cache_keys_to_improve_cache_hit_ratio
- A logo needs to be cached whether displayed through HTTP or HTTPS. When you customize the cache keys for the backend service that holds the logo, clear the Protocol checkbox so that requests through HTTP and HTTPS count as matches for the logo's cache entry.

<hr />

**Question 89**

- B. Stackdriver automatically collects admin activity logs for most services. The Stackdriver Logging agent must be installed on each instance to collect system logs. 100%
- Explanation
  Admin and event logs are configured by default. VM System logs require a logging agent to be configured. So, A is not valid. Answer is B

**Question 90**

- B. Deploy the update as a new version in the App Engine application, and split traffic between the new and current versions. 100%
- Explanation
  To test an update to an App Engine application with production traffic before replacing the current version, you can deploy the update as a new version in the App Engine application and split traffic between the new and current versions. This is known as a "blue-green" deployment, and it allows you to test the new version with a portion of production traffic while the current version is still serving the remainder of traffic.

  To split traffic between the new and current versions, you can use the App Engine traffic splitting feature. This feature allows you to specify the percentage of traffic that should be sent to each version, and it can be used to gradually ramp up traffic to the new version over time. This allows you to test the new version with a small portion of traffic initially, and gradually increase the traffic as you become more confident in the update.

- https://cloud.google.com/appengine/docs/standard/splitting-traffic

**Question 91**

- A. Create an egress rule with priority 1000 to deny all traffic for all instances. Create another egress rule with priority 100 to allow the Active Directory traffic for all instances. 100%

- https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules

- The implied **allow egress rule**: An egress rule whose action is allow, destination is 0.0.0.0/0, and priority is **the lowest possible (65535)** lets any instance send traffic to any destination

- The implied **deny ingress rule**: An ingress rule whose action is deny, source is 0.0.0.0/0, and priority is the lowest possible (65535)

**Question 92**

- D. Save a history of recommendations and results of the recommendations in BigQuery, to be used as training data. 100%

- The following insights and recommendations can be exported (to bigquery):

  - IAM recommender
  - VM machine type recommender
  - Managed instance group machine type recommender
  - Idle PD recommender
  - Idle VM recommender
  - Cloud SQL overprovisioned instance recommender
  - Cloud SQL idle instance recommender
  - Unattended project recommender
  - Cloud Run Service Identity recommender
  - https://cloud.google.com/recommender/docs/bq-export/export-recommendations-to-bq

- https://cloud.google.com/recommender/docs/recommenders

<hr />

**Question 93**

- A. Use the Horizontal Pod Autoscaler and enable cluster autoscaling. Use an Ingress resource to load-balance the HTTPS traffic.
- Explanation
  To load-balance the HTTPS traffic, we should use an Ingress resource, which acts as a reverse proxy to route traffic to different services based on the HTTP(S) header or the hostname. We can use the GKE Ingress controller to manage the Ingress resource, which will automatically create and manage a Google Cloud Load Balancer to distribute traffic to the pods running the application

- https://cloud.google.com/kubernetes-engine/docs/how-to/scaling-apps#autoscaling-deployments

  > kubectl autoscale creates a HorizontalPodAutoscaler (or HPA) object that targets a specified resource (called the scale target) and scales it as needed.

  ```
  kubectl autoscale deployment my-app --max 6 --min 4 --cpu-percent 50
  ```

**Creating an Ingress resource[1]**

Ingress is a Kubernetes resource that encapsulates a collection of rules and configuration for routing external HTTP(S) traffic to internal services.

- [1] https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer#creating_an_ingress_resource

**Question 94**

- B. Create an HTTPS load balancer with URL Maps. 100%
- https://cloud.google.com/load-balancing/docs/https/url-map
- Explanation
  An HTTPS load balancer is a type of load balancer that can distribute incoming HTTPS traffic to one or more back-end services, such as Compute Engine instances or Google Kubernetes Engine clusters. It can also provide SSL/TLS termination, enabling you to use your own SSL/TLS certificates and keys.

You can use URL Maps to configure the HTTPS load balancer to route traffic based on the URL path being requested. This allows you to set up different URL paths to be served by different back-end services, providing a high level of flexibility in your load balancing configuration.

**Question 95**

- B. Implement retry logic using a truncated exponential backoff strategy.
- Explanation
  You should use exponential backoff to retry your requests when receiving errors with 5xx or 429 response codes from Cloud Storage.
  https://cloud.google.com/storage/docs/request-rate

**Question 96**

- B. Use Deployment Manager to automate service provisioning. Use Stackdriver to monitor and debug your tests. 88%
- It is B, Google Best practice ---> never use scripts. They do not trust anyone else's code it seems. TarTar, from exam topic

**Question 97**

- D. Save the files in multiple Multi-Regional Cloud Storage buckets, one bucket per multi-region.
- Explanation
  To reduce latency you need a bucket near your users and you can't setup multi-region with Asia/EU/America selected so A is out and we are left with D.

**Question 98**

- C. Store the data in Cloud Storage and use lifecycle management to delete files when they expire. Most Voted
- Explanation
  To delete objects up to 4 years, you add an object lifecycle rule specifying the following form parameters:

Action = "Delete object" Object conditions = select ""Days since custom time" checkbox and specify 1460 days.

**Question 99**

- A. Set the memcache service level to dedicated. Create a key from the hash of the query, and return database values from memcache before issuing a query to Cloud SQL. 100%
- Explanation
  Right Option - A. Set the memcache service level to dedicated. Create a key from the hash of the query, and return database values from memcache before issuing a query to Cloud SQL.

  A dedicated memcache is always better than shared until cost-effectiveness specify in the exam as objective. So, Option C and D are ruled out.

  From A and B, Option B is sending and updating query every minute which is over killing. So reasonable option left with A which balance performance and cost.

**Question 100**

- B. Using the Cron service provided by App Engine, publish messages to a Cloud Pub/Sub topic. Subscribe to that topic using a message-processing utility service running on Compute Engine instances. 88%
- B is correct. More appropriately: https://cloud.google.com/solutions/reliable-task-scheduling-compute-engine
