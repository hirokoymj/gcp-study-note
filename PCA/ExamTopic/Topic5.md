# Topic 5 - Mountkirk Games

**Question 1**

- D. Tests should include directly testing the Google Cloud Platform (GCP) infrastructure. 35%, tartar
- It is D. New to GCP, migrated to GCP.... time to test if it works or not.

<hr />

**Question 2**

- A. Create a scalable environment in GCP for simulating production load. 100%
- A: is correct because simulating production load in GCP can scale in an economical way.
- B: is not correct because one of the pain points about the existing infrastructure was precisely that the environment did not scale well.
- C: is not correct because it is a best practice to have a clear separation between test and production environments. Generating test load should not be done from a production environment.
- D: is not correct because Mountkirk Games wants the testing environment to scale as needed. Defining several static environments for specific levels of load goes against this requirement.

<hr />

**Question 3**

- C. Google Kubernetes Registry, Google Container Engine, Google HTTP(S) Load Balancer. 100%

<hr />

**Question 4**

- B. Verify that the project quota hasn't been exceeded. 53%
- Given the sudden increase in popularity of the new feature and the resulting 503 errors and slow response times, Mountkirk Games should first investigate if they have exceeded their project quota on Google Cloud Platform

<hr />

**Question 5**

- D 51%, A 40%/ME/tartar, others
- A. Create a project for development and test and another for staging and production
- D. Create one project for development, a second for staging and a third for production.
- https://cloud.google.com/appengine/docs/legacy/standard/php/creating-separate-dev-environments

- "The staging environment needs access to some services from production"
  Its not the best practice, but A has less effort
- Dev and test. Staging and production.
- yes and there is no mention of test environment in option D.

- Based on Google's best practices, "Create one project for development, a second for staging and a third for production" would be the best option to pick. It follows the principles of "separation of duties" and "separation of concern". Anyway, it doesn't mention any test env.

End goal is to separate dev from staging/production. Putting staging/production in same project fits the requirements. Further effort would be required to change access between Staging and Production projects but that is out of scope of question.

Hence, "Create a project for development and test and another for staging and production" is the correct answer, even if it is not the best practice.

<hr />

**Question 6**

- B. Cloud Dataflow, Cloud Storage, Cloud Pub/Sub, and BigQuery. 100%
- https://cloud.google.com/solutions/stream-analytics
