# Udemy Test 5

**Question 1**

- C. Use the gcloud recommender command to list the idle virtual machine instances. 100%
- [View and apply idle VM recommendations](https://cloud.google.com/compute/docs/instances/viewing-and-applying-idle-vm-recommendations)
- how you can use idle VM recommendations to identify and stop idle VM instances to reduce waste of resources and reduce your compute bill on your projects.

```
gcloud recommender recommendations list \
--project=PROJECT_ID \
--location=ZONE \
--recommender=google.compute.instance.IdleResourceRecommender \
--format=yaml
```

<hr />

**Question 2**

- C. Use BigQuery for its scalability and ability to add columns to a schema. Partition race data based on season.

<hr />

**Question 3**

- A. Set up a network peering between vpc-a and vpc-b.
- https://cloud.google.com/vpc/docs/vpc-peering
- Google Cloud VPC Network Peering allows internal IP address connectivity across two Virtual Private Cloud (VPC) networks regardless of whether they belong to the same project or the same organization.
- https://cloud.google.com/vpc/docs/vpc-peering#networking-features-scenarios

<hr />

**Question 4**

- C. Total visits, error rates, and latency from Asia
- Total visits" covers the business requirements: - Optimize for capacity during peak periods and value during off-peak periods. - Expand services into Asia.

- "Error rates" covers business requirement: - Guarantee service availability and support. \*\* if service is unavailable, errors are reported!

- "Latency" covers technical requirement: - Decrease latency in Asia.

<hr />

**Question 5**

- B. Cloud Dataflow, Cloud Storage, Cloud Pub/Sub, and BigQuery. 100%
- A real time requires Stream / Messaging so Pub/Sub, Analytics by Big Query. Ingest millions of streaming events per second from anywhere in the world with Cloud Pub/Sub, powered by Google's unique, high-speed private network. Process the streams with Cloud Dataflow to ensure reliable, exactly-once, low-latency data transformation. Stream the transformed data into BigQuery, the cloud-native data warehousing service, for immediate analysis via SQL or popular visualization tools

<hr />

**Question 6**

- AB (55%), BC (19%)
- A. Store as much analytics and game activity data as financially feasible today so it can be used to train machine learning models to predict user behavior in the future.
- B. Begin packaging their game backend artifacts in container images and running them on Google Kubernetes Engine to improve the ability to scale up or down based on game activity.
- A+Bn =>

  - "as well as other metrics that provide deeper insight into usage patterns so we can adapt the game to target users."

  - environment that provides autoscaling, low latency load balancing, and frees us up from managing physical servers.

<hr />

**Question 7**

- C. Configure the deployment job to notify a Pub/Sub queue that triggers a Cloud Function. 82%
- Answer C seems to be ok. Triggering Pub/Sub to invoke Cloud Functions seems to be relevant. Cloud Storage doesn't make any sense. It would have been straight forward if Cloud Scheduler is mentioned in Option C instead of Deployment Job. But if you make a bit of research on deployment jobs, it's pointing me to cron jobs which is making perfect sense.
  https://cloud.google.com/appengine/docs/flexible/nodejs/scheduling-jobs-with-cron-yaml
  https://cloud.google.com/scheduler/docs/tut-pub-sub

- Answer C seems to be right. There are 2 requirements here,

1. Run every time it is released on Tuesday
2. Set Airwolf to run weekly
   Since a new version of the predictive capability application is released every tuesday evening at 3.00 am, the deployment job would run every time its released which is every week recurring. So both the requirements above are satisfied

<hr />

**Question 8**

- A. Upload your mobile app to the Firebase Test Lab, and test the mobile app on Android and iOS devices. 100%
- The Firebase Test Lab is a cloud-based testing service that allows you to test your mobile app on a variety of physical devices running Android and iOS. It provides a range of options for testing your app, including testing on different device models, screen sizes, and operating system versions.
- A should be correct
- B false - not really feasable
- C false - cannot run Android or IOS on GKE
- D false since that is what A is built to do

<hr />

**Question 9**

- A. Use a private cluster with a private endpoint with master authorized networks configured. 61%
- Using a private cluster with a private endpoint and master authorized networks configured is the best way to reduce the attack surface in Google Kubernetes Engine (GKE). A private cluster ensures that the nodes have private IP addresses, which are not accessible from the internet. The private endpoint allows access to the GKE API server only within the same VPC or through a secure connection (e.g., VPN or VPC peering). Configuring master authorized networks restricts access to the GKE control plane to specific CIDR blocks, further securing the environment and adhering to EHR Healthcare's business and technical requirements.
- https://cloud.google.com/kubernetes-engine/docs/concepts/private-cluster-concept
- A private cluster is a type of VPC-native cluster that only depends on internal IP addresses. Nodes, Pods, and Services in a private cluster require unique subnet IP address ranges.

<hr />

**Question 10**

- B. Use gsutil to batch copy the files in parallel. 100%
- Batch Copying in Parallel Saves time and an efficient option to use ( -m)
- https://cloud.google.com/storage/docs/gsutil/commands/cp
  If you have a large number of files to transfer, you can perform a parallel multi-threaded/multi-processing copy using the top-level gsutil -m option.

```
gsutil -m cp -r dir gs://my-bucket
```

<hr />

**Question 11**

- A. Tests should scale well beyond the prior approaches.65%
- D. Tests should include directly testing the Google Cloud Platform (GCP) infrastructure. 35%/Me/tartar
- Mountkirk Games
- It is D. New to GCP, migrated to GCP.... time to test if it works or not.
- " had problems scaling their global audience, application servers MySQL databases, and analytics tools."

<hr />

**Question 12**

- C. Provision service account keys for the on-premises infrastructure and use Google Cloud Platform (GCP) managed keys for the VMs. 100%

- Answer: C.

  Migrating data to Google Cloud Platform
  Let's say that you have some data processing that happens on another cloud provider and you want to transfer the processed data to Google Cloud Platform. You can use a service account from the virtual machines on the external cloud to push the data to Google Cloud Platform.

  To do this, **you must create and download a service account key when you create the service account and then use that key from the external process to call the Cloud Platform APIs.**

<hr />

**Question 13**

- A. Use Explainable AI. 100%
- Answer A
- AI Explanations helps you understand your model's outputs for classification and regression tasks. Whenever you request a prediction on AI Platform, AI Explanations tells you how much each feature in the data contributed to the predicted result. You can then use this information to verify that the model is behaving as expected, recognize bias in your models, and get ideas for ways to improve your model and your training data.
- https://cloud.google.com/ai-platform/prediction/docs/ai-explanations/overview

<hr />

**Question 14**

- D. Create a global load balancer with managed instance groups and autoscaling policies. Use non-preemptible Compute Engine instances. 100%
- D => KPI game stability = Use non-preemptible
- Agree "D". Preemptible VM is suitable for app which is fault-tolerant. Termination of preemptive VM might affect gaming experience, so it is not a good choice.

<hr />

**Question 15**

- C. Create a single G Suite account to manage users with each stage of each application in its own project. 90%

- Here are the correct answers:
  https://cloud.google.com/resource-manager/docs/creating-managing-folders
  Refer to the diagram on top, different envs are created at the project level.

- https://cloud.google.com/docs/enterprise/best-practices-for-enterprise-organizations
  "A general recommendation is to have one project per application per environment. For example, if you have two applications, "app1" and "app2", each with a development and production environment, you would have four projects: app1-dev, app1-prod, app2-dev, app2-prod. This isolates the environments from each other, so changes to the development project do not accidentally impact production, and gives you better access control, since you can (for example) grant all developers access to development projects but restrict production access to your CI/CD pipeline." The answer is C.

<hr />

**Question 16**

- A. Create a scalable environment in GCP for simulating production load. 100%
- From scenario: Requirements for Game Backend Platform

  1. Dynamically scale up or down based on game activity
  2. Connect to a managed NoSQL database service
  3. Run customize Linux distro

<hr />

**Question 17**

- AB 53%
- A. Store as much analytics and game activity data as financially feasible today so it can be used to train machine learning models to predict user behavior in the future. Most Voted
- B. Begin packaging their game backend artifacts in container images and running them on Google Kubernetes Engine to improve the ability to scale up or down based on game activity.
- A = ML = future stuff
- B = containers = portability (since current platform runs on VM's)

<hr />

**Question 18**

- A. Configure an organizational policy which constrains where resources can be deployed. 88%
- You can limit the physical location of a new resource with the Organization Policy Service resource locations constraint.
- https://cloud.google.com/resource-manager/docs/organization-policy/defining-locations

```
constraint: constraints/gcp.resourceLocations
listPolicy:
    deniedValues:
    - in:us-east1-locations
    - in:northamerica-northeast1-locations
```

<hr />

**Question 19**

- D. Google Cloud Datastore 54%
- A. Cloud Spanner 38%/ME
- Oracle (relational) + global => Spanner
- Cloud Spanner is a fully managed, scalable, and globally distributed relational database service. It provides strong consistency, high availability, and low-latency capabilities, which would be suitable for JencoMart's User Profiles database requirements.

<hr />

**Question 20**

- D. Configure Ingress for Anthos with a global load balancer and Google Kubernetes Engine. 50%
- C. Configure a global load balancer with Google Kubernetes Engine. 25%/Me
- For me is C.
  There is no necessity of Anthos or hybrid connectivity cluster. GKE and Global LB is enought
- C.
  The reason for choosing C is that configuring a global load balancer with Google Kubernetes Engine (GKE) meets the business and technical requirements of Mountkirk Games. A global load balancer automatically routes players to the nearest regional game instances, reducing latency and providing high performance. Moreover, GKE allows dynamic scaling based on game activity and takes advantage of Google Cloud's managed services and resource pooling to minimize costs.
- D.
  Configuring Ingress for Anthos with a global load balancer and Google Kubernetes Engine is more suitable for multi-cluster environments. In this scenario, deploying game instances in multiple regions is required, but a multi-cluster setup is not necessary. Therefore, option C is the best solution.

<hr />
