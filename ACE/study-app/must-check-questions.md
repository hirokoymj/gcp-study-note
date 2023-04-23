Question #7 (Page 2)

Several employees at your company have been creating projects with Cloud Platform and paying for it with their personal credit cards, which the company reimburses. The company wants to centralize all these projects under a single, new billing account. What should you do?

- A. Contact cloud-billing@google.com with your bank account details and request a corporate billing account for your company.
- B. Create a ticket with Google Support and wait for their call to share your credit card details over the phone.
- C. In the Google Platform Console, go to the Resource Manage and move all projects to the root Organizarion.
- D. In the Google Cloud Platform Console, create a new billing account and set up a payment method.

Correct Answer: D

- C is incomplete. Moving projects under an organisation doesn't change their linked billing project.
  https://cloud.google.com/resource-manager/docs/migrating-projects-billing

<hr />

Question #27 (Page 7)

You have sensitive data stored in three Cloud Storage buckets and have enabled data access logging. You want to verify activities for a particular user for these buckets, using the fewest possible steps. You need to verify the addition of metadata labels and which files have been viewed from those buckets. What should you do?

- A. Using the GCP Console, filter the Activity log to view the information.
- B. Using the GCP Console, filter the Stackdriver log to view the information.
- C. View the bucket in the Storage section of the GCP Console.
- D. Create a trace in Stackdriver to view the information.

Correct Answer: A

- Answer is A. Activity log does indeed show information about metadata.
I agree with Eshkrkrkr based on https://cloud.google.com/storage/docs/audit-logs Admin Activity logs: Entries for operations that modify the configuration or metadata of a project, bucket, or object.
<hr />

Question #40 (Page 10)

You have an instance group that you want to load balance. You want the load balancer to terminate the client SSL session. The instance group is used to serve a public web application over HTTPS. You want to follow Google-recommended practices. What should you do?

- A. Configure an HTTP(S) load balancer.
- B. Configure an internal TCP load balancer.
- C. Configure an external SSL proxy load balancer.
- D. Configure an external TCP proxy load balancer.

Correct Answer: A

- B. Configure an internal TCP load balancer. - internal, TCP/UDP traffic, software-defined
- C. Configure an external SSL proxy load balancer. Non-HTTP
- D. Configure an external TCP proxy load balancer. Non-HTTP

<hr />

Question #57 (Page 15)

You have a web application deployed as a managed instance group. You have a new version of the application to gradually deploy. Your web application is currently receiving live web traffic. You want to ensure that the available capacity does not decrease during the deployment. What should you do?

- A. Perform a rolling-action start-update with maxSurge set to 0 and maxUnavailable set to 1.
- B. Perform a rolling-action start-update with maxSurge set to 1 and maxUnavailable set to 0.
- C. Create a new managed instance group with an updated instance template. Add the group to the backend service for the load balancer. When all instances in the new managed instance group are healthy, delete the old managed instance group.
- D. Create a new instance template with the new application version. Update the existing managed instance group with the new instance template. Delete the instances in the managed instance group to allow the managed instance group to recreate the instance using the new instance template.

Correct Answer: B

- If you do not want any unavailable machines during an update, set the maxUnavailable value to 0 and the maxSurge value to greater than 0. With these settings, Compute Engine removes each old machine only after its replacement new machine is created and running.[1]
- maxSurge- configure how many new instances the MIG can create above its targetSize during an automated update.

**Links:**

1. https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups#max_unavailable

<hr />

Question #70 (Page 18)

You are building an application that will run in your data center. The application will use Google Cloud Platform (GCP) services like AutoML. You created a service account that has appropriate access to AutoML. You need to enable authentication to the APIs from your on-premises environment. What should you do?

- A. Use service account credentials in your on-premises application.
- B. Use gcloud to create a key file for the service account that has appropriate permissions.
- C. Set up direct interconnect between your data center and Google Cloud Platform to enable authentication for your on-premises applications.
- D. Go to the IAM & admin console, grant a user account permissions similar to the service account permissions, and use this user account for authentication from your data center.

Correct Answer: B

- Correct answer should be (B):

To use a service account outside of Google Cloud, such as on other platforms or on-premises, you must first establish the identity of the service account. Public/private key pairs provide a secure way of accomplishing this goal.

https://cloud.google.com/iam/docs/creating-managing-service-account-keys

<hr />

Your organization uses G Suite for communication and collaboration. All users in your organization have a G Suite account. You want to grant some G Suite users access to your Cloud Platform project. What should you do?
A. Enable Cloud Identity in the GCP Console for your domain.
B. Grant them the required IAM roles using their G Suite email address.
C. Create a CSV sheet with all users' email addresses. Use the gcloud command line tool to convert them into Google Cloud Platform accounts.
D. In the G Suite console, add the users to a special group called cloud-console-users@yourdomain.com. Rely on the default behavior of the Cloud Platform to grant users access if they are members of this group.

<hr />

Question #94 (Page 24)

You create a Deployment with 2 replicas in a Google Kubernetes Engine cluster that has a single preemptible node pool. After a few minutes, you use kubectl to examine the status of your Pod and observe that one of them is still in Pending status:

What is the most likely cause?

- A. The pending Pod's resource requests are too large to fit on a single node of the cluster.
- B. Too many Pods are already running in the cluster, and there are not enough resources left to schedule the pending Pod.
- C. The node pool is configured with a service account that does not have permission to pull the container image used by the pending Pod.
- D. The pending Pod was originally scheduled on a node that has been preempted between the creation of the Deployment and your verification of the Pods' status. It is currently being rescheduled on a new node.

Correct Answer: B

- Reasons for a Pod Status Pending:
  - Troubleshooting Reason #1: Not enough CPU
  - Troubleshooting Reason #2: Not enough memory
  - Troubleshooting Reason #3: Not enough CPU and memory
    https://managedkube.com/kubernetes/k8sbot/troubleshooting/pending/pod/2019/02/22/pending-pod.html

<hr />

Question #98 (Page 25)

Your customer has implemented a solution that uses Cloud Spanner and notices some read latency-related performance issues on one table. This table is accessed only by their users using a primary key. The table schema is shown below.

You want to resolve the issue. What should you do?

- A. Remove the profile_picture field from the table.
- B. Add a secondary index on the person_id column.
- C. Change the primary key to not have monotonically increasing values.
- D. Create a secondary index using the following Data Definition Language (DDL):

Correct Answer: C

- C is the right answer. Why? "This table is accessed only by their users using a primary key." So adding additional indexes on firstname and lastname won't help.
- Choose a primary key to prevent hotspots
  > As mentioned in Schema and data model, you should be careful when choosing a primary key to not accidentally create hotspots in your database. One cause of hotspots is having a column whose value monotonically increases as the first key part, because this results in all inserts occurring at the end of your key space. This pattern is undesirable because Spanner divides data among servers by key ranges, which means all your inserts will be directed at a single server that will end up doing all the work.
- https://cloud.google.com/spanner/docs/schema-design#primary-key-prevent-hotspots

<hr />

Question #191 (Page:48)

You have deployed multiple Linux instances on Compute Engine. You plan on adding more instances in the coming weeks. You want to be able to access all of these instances through your SSH client over the internet without having to configure specific access on the existing and new instances. You do not want the
Compute Engine instances to have a public IP. What should you do?

- A. Configure Cloud Identity-Aware Proxy for HTTPS resources.
- B. Configure Cloud Identity-Aware Proxy for SSH and TCP resources Most Voted
- C. Create an SSH keypair and store the public key as a project-wide SSH Key.
- D. Create an SSH keypair and store the private key as a project-wide SSH Key.

Correct Answer: B

- Use IAP TCP to enable access to VM instances that do not have external IP addresses or do not permit direct access over the internet.
- https://cloud.google.com/iap/docs/using-tcp-forwarding

<hr />

Question #168 (Page:42)

You are working for a hospital that stores its medical images in an on-premises data room. The hospital wants to use Cloud Storage for archival storage of these images. The hospital wants an automated process to upload any new medical images to Cloud Storage. You need to design and implement a solution. What should you do?

- A. Create a Pub/Sub topic, and enable a Cloud Storage trigger for the Pub/Sub topic. Create an application that sends all medical images to the Pub/Sub topic.
- B. Deploy a Dataflow job from the batch template, ג€Datastore to Cloud Storage.ג€ Schedule the batch job on the desired interval.
- C. Create a script that uses the gsutil command line interface to synchronize the on-premises storage with Cloud Storage. Schedule the script as a cron job.
- D. In the Cloud Console, go to Cloud Storage. Upload the relevant images to the appropriate bucket.

Correct Answer: C

- Pub/Sub will be good for all future files in in-prem data-storage. we want to sync all + new, so a local on-prem server running a cron job (not GCE CronJob) to run gsutil to transfer files to Cloud Storage would work.
- Answer is C. gsutil rsync <source_location> <destination_location>. This can sync content with Google cloud storage locations

<hr />

Question #155 (page 39)

You are storing sensitive information in a Cloud Storage bucket. For legal reasons, you need to be able to record all requests that read any of the stored data. You want to make sure you comply with these requirements. What should you do?

- A. Enable the Identity Aware Proxy API on the project.
- B. Scan the bucket using the Data Loss Prevention API.
- C. Allow only a single Service Account access to read the data.
- D. Enable Data Access audit logs for the Cloud Storage API.

Correct Answer: D

- Cloud Audit Logs with Cloud Storage - Admin Activity audit log, Data Access audit log

<hr />

Question #152 (Page:38)

Your company runs its Linux workloads on Compute Engine instances. Your company will be working with a new operations partner that does not use Google
Accounts. You need to grant access to the instances to your operations partner so they can maintain the installed tooling. What should you do?

- A. Enable Cloud IAP for the Compute Engine instances, and add the operations partner as a Cloud IAP Tunnel User.
- B. Tag all the instances with the same network tag. Create a firewall rule in the VPC to grant TCP access on port 22 for traffic from the operations partner to instances with the network tag.
- C. Set up Cloud VPN between your Google Cloud VPC and the internal network of the operations partner.
- D. Ask the operations partner to generate SSH key pairs, and add the public keys to the VM instances.

Correct Answer: B

- the IAP allow you to access compute engine from the internet without having to have a GCP account
- IAP controls access to your App Engine apps and Compute Engine VMs.
- By default, IAP uses Google identities and IAM. By leveraging Identity Platform instead, you can authenticate users with a wide range of external identity providers, such as:

  - Email/password
  - OAuth (Google, Facebook, Twitter, GitHub, Microsoft, etc.)
  - SAML
  - OIDC
  - Phone number
  - Custom
  - Anonymous

- This is useful if your application is already using an external authentication system, and migrating your users to Google accounts is impractical.

<hr />

Question #153(Page:39)

You have created a code snippet that should be triggered whenever a new file is uploaded to a Cloud Storage bucket. You want to deploy this code snippet. What should you do?

- A. Use App Engine and configure Cloud Scheduler to trigger the application using Pub/Sub.
- B. Use Cloud Functions and configure the bucket as a trigger resource.
- C. Use Google Kubernetes Engine and configure a CronJob to trigger the application using Pub/Sub.
- D. Use Dataflow as a batch job, and configure the bucket as a data source.

Correct Answer: B

- Google Cloud Storage Triggers

<hr />

Question #130(page 33)

You manage an App Engine Service that aggregates and visualizes data from BigQuery. The application is deployed with the default App Engine Service account.
The data that needs to be visualized resides in a different project managed by another team. You do not have access to this project, but you want your application to be able to read data from the BigQuery dataset. What should you do?

- A. Ask the other team to grant your default App Engine Service account the role of BigQuery Job User.
- B. Ask the other team to grant your default App Engine Service account the role of BigQuery Data Viewer.
- C. In Cloud IAM of your project, ensure that the default App Engine service account has the role of BigQuery Data Viewer.
- D. In Cloud IAM of your project, grant a newly created service account from the other team the role of BigQuery Job User in your project.

Correct Answer: B

<hr />

Question #113 (page:29)

You need to assign a Cloud Identity and Access Management (Cloud IAM) role to an external auditor. The auditor needs to have permissions to review your
Google Cloud Platform (GCP) Audit Logs and also to review your Data Access logs. What should you do?

- A. Assign the auditor the IAM role roles/logging.privateLogViewer. Perform the export of logs to Cloud Storage.
- B. Assign the auditor the IAM role roles/logging.privateLogViewer. Direct the auditor to also review the logs for changes to Cloud IAM policy.
- C. Assign the auditor's IAM user to a custom role that has logging.privateLogEntries.list permission. Perform the export of logs to Cloud Storage.
- D. Assign the auditor's IAM user to a custom role that has logging.privateLogEntries.list permission. Direct the auditor to also review the logs for changes to Cloud IAM policy

Correct Answer: C

- Yes, B is correct because: 1) Question doesn't ask us to export and store logs for any long period of time.
- why here cloud storage is mentioned ? they are mentioning only access and why this is coming in the middle

<hr />

Question #106 (page:27)

Your organization has a dedicated person who creates and manages all service accounts for Google Cloud projects. You need to assign this person the minimum role for projects. What should you do?

- A. Add the user to roles/iam.roleAdmin role.
- B. Add the user to roles/iam.securityAdmin role.
- C. Add the user to roles/iam.serviceAccountUser role.
- D. Add the user to roles/iam.serviceAccountAdmin role.

Correct Answer: D

- Service Account User (roles/iam.serviceAccountUser): Includes permissions to list service accounts, get details about a service account, and impersonate a service account.

- Service Account Admin (roles/iam.serviceAccountAdmin): Includes permissions to list service accounts and get details about a service account. Also includes permissions to create, update, and delete service accounts, and to view or change the IAM policy on a service account.

<hr />

Question #121(page 31)

Your managed instance group raised an alert stating that new instance creation has failed to create new instances. You need to maintain the number of running instances specified by the template to be able to process expected application traffic. What should you do?

- A. Create an instance template that contains valid syntax which will be used by the instance group. Delete any persistent disks with the same name as instance names. Most Voted
- B. Create an instance template that contains valid syntax that will be used by the instance group. Verify that the instance name and persistent disk name values are not the same in the template.
- C. Verify that the instance template being used by the instance group contains valid syntax. Delete any persistent disks with the same name as instance names. Set the disks.autoDelete property to true in the instance template.
- D. Delete the current instance template and replace it with a new instance template. Verify that the instance name and persistent disk name values are not the same in the template. Set the disks.autoDelete property to true in the instance template.

Correct Answer: A

1. create new template, while creating ensure that in the new template disks.autoDelete=true, 3. delete existing persistent disks, 4. make rolling update ...
   In order to switch to new template we need "Rolling update". Unfortunately, it is not mentioned.

With current options
C - not correct, we cannot update existing template
D - not correct, we cannot delete existing template when it is in use (just checked in GCP) (We need rolling update)
B - will not solve our problem without Rolling update
A - This is the only option (I know that it can be temporary) that will work without Rolling update according to
https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-migs
