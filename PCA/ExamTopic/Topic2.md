# TOPIC 2 - JencoMart

**Question 1**
-C. Create a single G Suite account to manage users with each stage of each application in its own project. 90%

- https://cloud.google.com/resource-manager/docs/creating-managing-folders
- https://cloud.google.com/docs/enterprise/best-practices-for-enterprise-organizations

**Question 2**

- C. Take a snapshot of the disk and connect to a new machine to investigate
- D. Check inbound firewall rules for the network the machine is connected to
- F. Print the Serial Console output for the instance for troubleshooting, activate the interactive console, and investigate
- https://cloud.google.com/compute/docs/ssh-in-browser

**Question 3**

- C. Provision service account keys for the on-premises infrastructure and use Google Cloud Platform (GCP) managed keys for the VMs
- https://cloud.google.com/iam/docs/understanding-service-accounts#migrating_data_to_google_cloud_platform

**Question 4**

- C. Total visits, error rates, and latency from Asia. 58%
- **Total visits** covers the business requirements:
  - Optimize for capacity during peak periods and value during off-peak periods.
  - Expand services into Asia.
- **Error rates** covers business requirement:
  - Guarantee service availability and support. \*\* if service is unavailable, errors are reported!
- **Latency** covers technical requirement:
  - Decrease latency in Asia.

**Question 5**

- ACF 50%
- A. A single VPN tunnel, which limits throughput
- C. A copy command that is not suited to operate over long distances Most VotedMost Voted
- F. Complicated internet connectivity between the on-premises infrastructure and GCP Most Voted

**Question 6**

- A. Cloud Spanner
- oracle= Relational +Gloabal = spanner =>A

# TEST3 Helicopter Racing League (HRL)

**Question 1**

- B. Encrypt the card data with a deterministic algorithm stored in Firestore using Datastore mode.
- google https://cloud.google.com/architecture/tokenizing-sensitive-cardholder-data-for-pci-dss

**Question 2**

- D %, omermaH

> The command **gcloud compute security-policies rules update 1000 --security-policy=hlr-policy --expression="evaluatePreconfigurationExpr(`sourceiplist-fastly`)" --action=allow** updates a security policy rule with the name "1000" in the security policy "hlr-policy". The rule allows traffic that matches the specified expression and has the action "allow".

> In this particular case, the expression used in the rule is "evaluatePreconfigurationExpr(sourceiplist-fastly)". The "evaluatePreconfigurationExpr" function is used to reference a preconfigured expression, in this case, the tag "sourceiplist-fastly". This means that the rule will allow traffic from any instances that have the "sourceiplist-fastly" tag.

**Question 3**

- C. Configure the deployment job to notify a Pub/Sub queue that triggers a Cloud Function. 82%, omermaH
- Option A, Set up Cloud Tasks and a Cloud Storage bucket that triggers a Cloud Function, would not be the correct solution because Cloud Tasks is a service for creating and managing asynchronous tasks that are executed later, but it does not support recurring schedules.

- Option B, Set up a Cloud Logging sink and a Cloud Storage bucket that triggers a Cloud Function, would not be the correct solution because Cloud Logging is a service for collecting, viewing, and analyzing logs, but it does not support triggering Cloud Functions on a recurring basis.

- Option D, Set up Identity and Access Management (IAM) and Confidential Computing to trigger a Cloud Function, would not be the correct solution because IAM is a service for managing access to Google Cloud resources and Confidential Computing is a service for running sensitive workloads in hardware-isolated environments, but neither of these services can be used to trigger Cloud Functions on a recurring basis.

**Question 4**

- A. Use Explainable AI. 100%, omermaH
- https://cloud.google.com/explainable-ai

**Question 5**

- C. Use BigQuery for its scalability and ability to add columns to a schema. Partition race data based on season. 100%,
- For HRL's data storage needs, it is recommended to use BigQuery due to its scalability and ability to handle large amounts of data. By partitioning the race data based on season, HRL can easily access and query specific seasons' data while also taking into consideration future data growth. BigQuery also allows for the flexibility to add new columns to the schema as needed, making it easier to adapt to changes in the data being collected. Additionally, BigQuery's pay-per-use pricing model allows HRL to only pay for the data storage and querying they use, making it a cost-effective solution. omermaH

**Question 6**

- C. Use the gcloud recommender command to list the idle virtual machine instances. 100%
- https://cloud.google.com/compute/docs/instances/viewing-and-applying-idle-vm-recommendations

# Case Study

https://cloud.google.com/learn/certification/guides/professional-cloud-architect

- EHR Healthcare
- Helicopter Racing League
- Mountkirk Games
- TerramEarth
