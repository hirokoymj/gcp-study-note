# Topic 8 - TerramEarth

**Question 1**

- A: IoT -> FTP -> Google Cloud LB -> Google Containe Engine -> Pub/Sub -> Dataflow -> BQ -> Analysts (100%)
- A - The company has customers in 100+ countries, while App Engine is regional (rule out B).
- 1. Cloud SQL vs BigQuery for analytics.
- 2. GKE (with or without Anthos) + Cloud Load balancing vs App Engine.
- For the second point, GKE with Cloud Load Balancing is a better fit than App Engine. App Engine is a regional service.
- I vote for A - The company has customers in 100+ countries, while App Engine is regional (rule out B).

<hr />

**Question 2**

- A. Use Google App Engine with Google Cloud Endpoints. Focus on an API for dealers and partners. 90%
- Google offers Cloud Endpoint to develop, deploy and manage APIs on any google cloud backend.
- https://cloud.google.com/endpoints

> With Endpoints Frameworks, you don't have to deploy a third-party web server (such as Apache Tomcat or Gunicorn) with your application. You annotate or decorate the code and deploy your application as you normally would to the App Engine standard environment.

> Cloud Endpoints Frameworks for the App Engine standard environment : https://cloud.google.com/endpoints/docs/frameworks/about-cloud-endpoints-frameworks

<hr />

**Question 3**

- A. Build or leverage an OAuth-compatible access control system. 100%
- https://cloud.google.com/docs/authentication
- https://cloud.google.com/blog/products/identity-security/identity-and-authentication-the-google-cloud-way

<hr />

**Question 4**

- B. Vehicles write data directly to Google Cloud Pub/Sub. 100%
- https://cloud.google.com/pubsub/quotas
- https://cloud.google.com/bigquery/quotas#streaming_inserts
- thanks for sharing the link, but seems pub/sub can handle more streaming data than bigquery. pub/sub 120,000,000 kB per minute (2 GB/s) in large regions, bigquery is 1GB/s

<hr />

**Question 5**

- C 56%/ME/tartar, B 41%
- C. Increase fleet cellular connectivity to 80%, migrate from FTP to streaming transport, and develop machine learning analysis of metrics 56%

- C is correct because using cellular connectivity will greatly improve the freshness of data used for analysis from where it is now, collected when the machines are in for maintenance. Streaming transport instead of periodic FTP will tighten the feedback loop even more. Machine learning is ideal for predictive maintenance workloads.
- Only 200,000 of 20 million vehicles are connected by cellular network
- The question is in google practice exam, answer is C: Increase fleet cellular connectivity to 80%, migrate from FTP to streaming transport...
<hr />

**Question 6**

- B. Capacity planning, TCO calculations, opex/capex allocation
- From the case study, it can conclude that Management (CXO) all concern rapid provision of resources (infrastructure) for growing as well as cost management, such as Cost optimization in Infrastructure, trade up front **capital expenditures** (Capex) for **ongoing operating expenditures** (Opex), and **Total cost of ownership** (TCO)
- GCP practice question confirms that B is correct

<hr />

**Question 7**

- C. Directly transfer the files to different Google Cloud Multi-Regional Storage bucket locations in US, EU, and Asia using Google APIs over HTTP(S). Run the ETL process using the data in the bucket. 27%/Me/omerma

- D. Directly transfer the files to a different Google Cloud Regional Storage bucket location in US, EU, and Asia using Google APIs over HTTP(S). Run the ETL process to retrieve the data from each Regional bucket. 73%
- **c**

  - Multi-Region Name Multi-Region Description
  - asia Data centers in Asia
  - eu Data centers in the European Union1
  - us Data centers in the United States

- (amxexam 1 year, 6 months ago) multi-region is a large geographic area, such as the United States, that contains two or more geographic places.

1. We all know the issue is with the file sending mechanism.
2. Looking at the option direct bucket is better than FTP service hosted on VM.
3. Also, we will look for multi-regional so there is no latency for long-distance customers. Also, the company has 100 countries it is a multi-regional company.

- Hence C
- https://cloud.google.com/storage/docs/locations#location_recommendations

<hr />

**Question 8**

- D. Launch a cluster in each region to preprocess and compress the raw data, then move the data into a region bucket and use a Cloud Dataproc cluster to finish the job. 100%

- There is one thing for sure here. If we move/copy data between continents it will cost us money therefore compressing the data before copying to another region/continent makes sense.
  Preprocessing also makes sense because we probably want to process smaller chunks of data first (remember 100K milage).
  So now type of target bucket; multi-region or standard? multi-region is good for high-availability and low latency with a little more cost however question doesn't require any of these features.
  Therefore I think standard storage option is good to go given lower costs are always better.

- So my answer would be D

**Question 9**
D. Have the vehicle's computer compress the data in hourly snapshots, and store it in a GCS Coldline bucket. 100%

**Question 10**

- AC, 100%
- A. Treat every micro service call between modules on the vehicle as untrusted. Most Voted
- C. Use a trusted platform module (TPM) and verify firmware and binaries on boot.
- Correct answer: A & C
- B is not correct because IPv6 doesn't have any impact on the security during vehicle operation, although it improves system scalability and simplicity.
- D is not correct because merely using a functional programming language doesn't guarantee a more secure level of execution isolation. Any impact on security from this decision would be incidental at best.
- E is not correct because this improves system durability, but it doesn't have any impact on the security during vehicle operation.
- F is not correct because it doesn't have any impact on the security during vehicle operation, although it improves system durability.

**Question 11**

- B. Capture all operating data, train machine learning models that identify ideal operations, and run locally to make operational adjustments automatically

Both B and D starts with "Capture all operating data, train machine learning models that identify ideal operations, ..." so they are offering the same method for training the data.

The keypoint here is "make operational adjustments" such as adjusting the oil pressure so if we host in GCP-ML, how are we going to instruct vehicles on field to adjust their oil pressure if they have no internet connection? There is no way to use GCP-ML model generated parameters to command the "not connected" field vehicles to make operational adjustments automatically.

Therefore, I believe running it locally on the servers sitting in the vehicles is the only option.

My answer: B
