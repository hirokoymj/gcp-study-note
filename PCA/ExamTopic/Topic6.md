# Topic 6 - Mountkirk Games

**Question 1**

- AB 100%
- A. Evaluate the impact of migrating their current batch ETL code to Cloud Dataflow.
- B. Write a schema migration plan to denormalize data for better performance in BigQuery.

- Traditional extract, transform, and load (ETL) job
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

- **Denormalization** is the process of adding precomputed redundant data to an otherwise normalized relational database to improve read performance of the database. Normalizing a database involves removing redundancy so only a single copy exists of each piece of information. Denormalizing a database requires data has first been normalized. https://www.techtarget.com/searchdatamanagement/definition/denormalization

<hr />

**Question 2**

- D. Create a global load balancer with managed instance groups and autoscaling policies. Use non-preemptible Compute Engine instances. 100%

<hr />

**Question 3**

- AB 50%/tartar
- A. Store as much analytics and game activity data as financially feasible today so it can be used to train machine learning models to predict user behavior in the future.
- B. Begin packaging their game backend artifacts in container images and running them on Google Kubernetes Engine to improve the ability to scale up or down based on game activity.

- A+B)
  =>(Executive Statement -)as well as other metrics that provide deeper insight into usage patterns so we can adapt the game to target users.

environment that provides autoscaling, low latency load balancing, and frees us up from managing physical servers.

<hr />

**Question 4**

- A. Deploy failure injection software to the game analytics platform that can inject additional latency to mobile client analytics traffic. 67%/tartar
- (a66030) The answer is A. The question asks - test the analytics platform's resilience to changes in mobile network latency.
  Only A adds latency to mobile network.
- C - adds delay at beginning of file processing. does not add delay/latency in mobile network.
  One of the lines in the requirements for analytics: Process data that arrives late because of slow mobile networks
- [Test your resilience](https://cloud.google.com/architecture/scalable-and-resilient-apps?hl=en)

- "If you're using a service mesh like Istio to manage your app services, you can inject faults at the application layer instead of killing pods or machines, or you can inject corrupting packets at the TCP layer. You can introduce delays to simulate network latency or an overloaded upstream system. You can also introduce aborts, which mimic failures in upstream systems."

<hr />

**Question 5**

- D. Use Cloud Bigtable for time series data, use Cloud Spanner for transactional data, and use BigQuery for historical data queries. 100%

- (sri007)
- Storing time-series data in Cloud **Bigtable** is a natural fit,
- Cloud **Spanner** scales horizontally and serves data with low latency while maintaining transactional consistency and industry-leading 99.999% (five 9s) availability - 10x less downtime than four nines (<5 minutes per year). Cloud Spanner helps future-proof your database backend.
- After you load your data into **BigQuery**, you can query the data in your tables. BigQuery supports two types of queries: Interactive queries, Batch queries

<hr />

**Question 6**

- A. Cloud Bigtable 100%

<hr />

**Question 7**

- C. Create an instance template for the backend. For every region, deploy it on a multi-zone managed instance group. Use an L7 load balancer. 69%/tartar

- L4 load balancing offers traffic management of transactions at the network protocol layer (TCP/UDP). ... L7 load balancing works at the highest level of the OSI model. L7 bases its routing decisions on various characteristics of the HTTP/HTTPS header
  Mountrik requirment is global so C is ok

- https://cloud.google.com/load-balancing/docs/https
- An external Application Load Balancer is a proxy-based** Layer 7** load balancer that enables you to run and scale your services behind a single external IP address. The external Application Load Balancer distributes **HTTP and HTTPS** traffic
