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

- C 56%, B 41%
- B. Migrate from FTP to streaming transport, migrate from CSV to binary format, and develop machine learning analysis of metrics
- C. Increase fleet cellular connectivity to 80%, migrate from FTP to streaming transport, and develop machine learning analysis of metrics

- This question is in the sample questions from google
- A is not correct because machine learning analysis is a good means toward the end of reducing downtime, but shuffling formats and transport doesn't directly help at all.

- B is not correct because machine learning analysis is a good means toward the end of reducing downtime, and moving to streaming can improve the freshness of the information in that analysis, but changing the format doesn't directly help at all.
- C is correct because using cellular connectivity will greatly improve the freshness of data used for analysis from where it is now, collected when the machines are in for maintenance. Streaming transport instead of periodic FTP will tighten the feedback loop even more. Machine learning is ideal for predictive maintenance workloads.
- D is not correct because machine learning analysis is a good means toward the end of reducing downtime, but the rest of these changes don't directly help at all.

**Question 6**

- B. Capacity planning, TCO calculations, opex/capex allocation
- From the case study, it can conclude that Management (CXO) all concern rapid provision of resources (infrastructure) for growing as well as cost management, such as Cost optimization in Infrastructure, trade up front **capital expenditures** (Capex) for **ongoing operating expenditures** (Opex), and **Total cost of ownership** (TCO)

**Question 7**

**Question 8**

**Question 9**

**Question 10**

**Question 11**
