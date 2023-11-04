# Topic 8 - TerramEarth

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**
A

- I vote for A - The company has customers in 100+ countries, while App Engine is regional (rule out B).
- 1. Cloud SQL vs BigQuery for analytics.
- 2. GKE (with or without Anthos) + Cloud Load balancing vs App Engine.
- For the second point, GKE with Cloud Load Balancing is a better fit than App Engine. App Engine is a regional service whereas, with the other option, you can have multiple GKE clusters in different regions. And Cloud Load Balancing can send requests to the cluster in the region that is closest to the vehicle. This option minimizes the latency and makes the feedback loop more real-time.

**Question 2**

- A. Use Google App Engine with Google Cloud Endpoints. Focus on an API for dealers and partners. 90%
- Google offers Cloud Endpoint to develop, deploy and manage APIs on any google cloud backend.
- https://cloud.google.com/endpoints

> With Endpoints Frameworks, you don't have to deploy a third-party web server (such as Apache Tomcat or Gunicorn) with your application. You annotate or decorate the code and deploy your application as you normally would to the App Engine standard environment.

> Cloud Endpoints Frameworks for the App Engine standard environment : https://cloud.google.com/endpoints/docs/frameworks/about-cloud-endpoints-frameworks

**Question 3**

- A. Build or leverage an OAuth-compatible access control system. 100%
- https://cloud.google.com/docs/authentication
- https://cloud.google.com/blog/products/identity-security/identity-and-authentication-the-google-cloud-way

**Question 4**

- B. Vehicles write data directly to Google Cloud Pub/Sub. 100%
- https://cloud.google.com/pubsub/quotas
- https://cloud.google.com/bigquery/quotas#streaming_inserts
- thanks for sharing the link, but seems pub/sub can handle more streaming data than bigquery. pub/sub 120,000,000 kB per minute (2 GB/s) in large regions, bigquery is 1GB/s

**Question 5**
**Question 6**
**Question 7**
**Question 8**
**Question 9**
**Question 10**
**Question 11**
