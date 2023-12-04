# Topic 6 - Mountkirk Games

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**

- AB 100%
- A. Evaluate the impact of migrating their current batch ETL code to Cloud Dataflow. Most Voted
- B. Write a schema migration plan to denormalize data for better performance in BigQuery.
- Now A is a must, the ETL is definitely what Cloud Dataflow does.
  Now between B / C. Its talking about a lot of data. we know that Cloud SQL is not the best for huge volume of data, plus not real time data. Big Query is the best option
- https://cloud.google.com/bigquery/docs/loading-data#loading_denormalized_nested_and_repeated_data
- **There are several ways to ingest data into BigQuery:**

  - Batch load a set of data records.
  - Stream individual records or batches of records.
  - Use queries to generate new data and append or overwrite the results to a table.
  - Use a third-party application or service.

- **Batch loading**

With batch loading, you load the source data into a BigQuery table in** a single batch operation**. For example, the data source could be **a CSV file**, an external database, or a set of log files. Traditional extract, transform, and load (ETL) jobs fall into this category.

<hr />

**Question 2**

- D. Create a global load balancer with managed instance groups and autoscaling policies. Use non-preemptible Compute Engine instances. 100%

**Question 3**

- AB 5%, BC 26%
- A. Store as much analytics and game activity data as financially feasible today so it can be used to train machine learning models to predict user behavior in the future.
- B. Begin packaging their game backend artifacts in container images and running them on Google Kubernetes Engine to improve the ability to scale up or down based on game activity.
- C. Set up a CI/CD pipeline using Jenkins and Spinnaker to automate canary deployments and improve development velocity.
- B & C - C beause: "Mountkirk Games wants to design their solution for the future in order to take advantage of cloud and technology improvements as they become available". Spinnaker makes it easy to use new features as they become available: https://console.cloud.google.com/marketplace/product/google-cloud-platform/spinnaker?pli=1 - Pre-integrated with Google Cloud Platform

Spinnaker for Google Cloud Platform is pre-configured to work with GCP products like Cloud Build, Compute Engine, App Engine, Google Kubernetes Engine, and Stackdriver.

**Question 4**

- A. Deploy failure injection software to the game analytics platform that can inject additional latency to mobile client analytics traffic. 67%
- B. Build a test client that can be run from a mobile phone emulator on a Compute Engine virtual machine, and run multiple copies in Google Cloud Platform regions all over the world to generate realistic traffic. 17%

**Question 5**

- D. Use Cloud Bigtable for time series data, use Cloud Spanner for transactional data, and use BigQuery for historical data queries. 100%

**Question 6**

- A. Cloud Bigtable 100%

**Question 7**

- C. Create an instance template for the backend. For every region, deploy it on a multi-zone managed instance group. Use an L7 load balancer. 69%

- L4 load balancing offers traffic management of transactions at the network protocol layer (TCP/UDP). ... L7 load balancing works at the highest level of the OSI model. L7 bases its routing decisions on various characteristics of the HTTP/HTTPS header
  Mountrik requirment is global so C is ok
