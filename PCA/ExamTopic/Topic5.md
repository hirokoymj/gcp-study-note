# Topic 5 - Mountkirk Games

**Question 1**

- D. Tests should include directly testing the Google Cloud Platform (GCP) infrastructure. 35%, tartar
- It is D. New to GCP, migrated to GCP.... time to test if it works or not.

**Question 2**

- A. Create a scalable environment in GCP for simulating production load. 100%
- A: is correct because simulating production load in GCP can scale in an economical way.
- B: is not correct because one of the pain points about the existing infrastructure was precisely that the environment did not scale well.
- C: is not correct because it is a best practice to have a clear separation between test and production environments. Generating test load should not be done from a production environment.
- D: is not correct because Mountkirk Games wants the testing environment to scale as needed. Defining several static environments for specific levels of load goes against this requirement.

**Question 3**

- C. Google Kubernetes Registry, Google Container Engine, Google HTTP(S) Load Balancer. 100%

**Question 4**

- B. Verify that the project quota hasn't been exceeded. 53%
- Given the sudden increase in popularity of the new feature and the resulting 503 errors and slow response times, Mountkirk Games should first investigate if they have exceeded their project quota on Google Cloud Platform

**Question 5**
D. Create one project for development, a second for staging and a third for production. 47%, tartar
https://cloud.google.com/appengine/docs/legacy/standard/php/creating-separate-dev-environments

**Question 6**

- B. Cloud Dataflow, Cloud Storage, Cloud Pub/Sub, and BigQuery. 100%
- https://cloud.google.com/solutions/stream-analytics
