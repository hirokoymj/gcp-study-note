# Topic 12 - Dress4Win

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**

- D. Implement managed instance groups for the Tomcat and Nginx. Migrate MySQL to Cloud SQL, RabbitMQ to Cloud Pub/Sub, Hadoop to Cloud Dataproc, and NAS to Cloud Storage. 71%

- C. Implement managed instance groups for Tomcat and Nginx. Migrate MySQL to Cloud SQL, RabbitMQ to Cloud Pub/Sub, Hadoop to Cloud Dataproc, and NAS to Compute Engine with Persistent Disk storage. 29%

- https://cloud.google.com/architecture/filers-on-compute-engine?hl=en#managed_file_storage_solutions

- Managed Instances With Tomcat and Nginx would bring the minimum necessary tweaking to the new environment.
  Migrating from MySql to Cloud SQL does not require any syntax changes.
  Moving from Rabbit MQ to Pub/Sub is relatively straightforward and has very complete documentation.
  DataProc has Libraries and tools to ensure Apache Hadoop interoperability.
  Without many changes in the environment, mainly keeping the original architecture, Datastorage will keep the presentation characteristics of a shared area, mapped to the instances.

**Question 2**

- A. Deploy Nginx and Tomcat using Cloud Deployment Manager to Compute Engine. Deploy a Cloud SQL server to replace MySQL. Deploy Jenkins using Cloud Deployment Manager. 100%

- After reading the question more and kind of linking back to question one, i think it's asking how to "automate the deployment" of web and transactional data layers". In that case, I think focus on deployment automation of existing technology might be a better than mapping new cloud technology in this case? so, A might be a better fit?

- the answer is A because datastore is nosql db and in business requirements it is clarly sais that improve bussiness agility and speed innovation through rapid provisoning of new ressources

**Question 3**

- C. Hadoop/Spark deployed using Cloud Dataproc Regional in High Availability mode. 100%
- A. Web applications deployed using App Engine standard environment - there are multiple web apps, seems project limit of 1 - and not clear on the implications of Standard Env, with Nginx (there seems to be discussions) -- no not clear on this.
- B. RabbitMQ - is always replaced by Pub/Sub - So No.
- C. Hadoop/Spark - This is a well know Use Case
- D. Jenkins, Etc, these duplicate GCP products so it can't be the answer.

**Question 4**

- D. Use the Activity page in the GCP Console and Stackdriver Logging to provide the required insight. 100%
- https://cloud.google.com/logging/docs/audit/

**Question 5**

- C. Assign predefined IAM roles to the Google Groups you created in order to enforce security requirements. Utilize Google's default encryption at rest when storing files in Cloud Storage. 100%

**There 2 requirements**

> 1. best practices = least privilege = custom role
> 2. simplest = default encryption as
>    : If you use customer-supplied encryption keys or client-side encryption, you must securely manage your keys and ensure that they are not lost. If you lose your keys, you are no longer able to read your data, and you continue to be charged for storage of your objects until you delete them.

**Question 6**

- D. Containerize the micro-services and host them in Google Kubernetes Engine.

- Containerizing the existing applications ensures efficient use of resources. This activity the business requirement “optimize architecture for performance in the cloud”. As a precursor to Cloud migration, you could convert the microservices to containers and host them on GKE on-prem: https://cloud.google.com/anthos/gke/docs/on-prem/overview which also makes it very easy for you to migrate to Cloud. GKE on-prem is hybrid cloud software that brings Google Kubernetes Engine (GKE) to on-premises data centres. With GKE on-prem, you can create, manage, and upgrade Kubernetes clusters in your on-premises environment.

- D read business req.

- Cloud SQL supports MySQL 5.6, 5.7 and 8.0 and the current onprem version is MySQL 5.8. So downgrade from 5.8 to 5.7 is the right answer (D).

- 'D' as it matches the requirement - Improve business agility and speed of innovation through rapid provisioning of new resources. Among the choices, containerizing microservices will allow the company to deploy and scale services independantly.
