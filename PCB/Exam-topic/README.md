**Question #1:**
You are developing a new application on a VM that is on your corporate network. The application will use Java Database Connectivity (JDBC) to connect to Cloud SQL for PostgreSQL. Your Cloud SQL instance is configured with IP address 192.168.3.48, and SSL is disabled. You want to ensure that your application can access your database instance without requiring configuration changes to your database. What should you do?

- A. Define a connection string using your Google username and password to point to the external (public) IP address of your Cloud SQL instance.
- B. Define a connection string using a database username and password to point to the internal (private) IP address of your Cloud SQL instance.
- C. Define a connection string using Cloud SQL Auth proxy configured with a service account to point to the internal (private) IP address of your Cloud SQL instance.
- D. Define a connection string using Cloud SQL Auth proxy configured with a service account to point to the external (public) IP address of your Cloud SQL instance.

**Question #1A:**

- C.
  > The IP address given is a private IP address and not routable via the internet. Therefore any answer which references a public IP is wrong by definition (A, D). That leaves B and C. B cannot be correct because the app is on a corporate network and thus not on a Google VPC network. Good security practices dictate using Cloud SQL Auth Proxy and a service account which access the Cloud SQL instance via its private IP address.

<hr />

**Question #2:**
Your digital-native business runs its database workloads on Cloud SQL. Your website must be globally accessible 24/7. You need to prepare your Cloud SQL instance for high availability (HA). You want to follow Google-recommended practices. What should you do? (Choose two.)

- A. Set up manual backups.
- B. Create a PostgreSQL database on-premises as the HA option.
- C. Configure single zone availability for automated backups.
- D. Enable point-in-time recovery.
- E. Schedule automated backups.

**Question #2A:**

- D,E.

  > A is wrong because why bother configuring manual backups when Cloud SQL will automate that for you.

  > B seems attractive, but why bother replicating back to on-prem when you can configure a Cloud SQL for HA.

  > C is wrong because a single zone failure would not give you HA.

  > That leaves D & E.

- [About high availability](https://cloud.google.com/sql/docs/postgres/connect-auth-proxy)

<hr />

**Question #3:**
Your company wants to move to Google Cloud. Your current data center is closing in six months. You are running a large, highly transactional Oracle application footprint on VMWare. You need to design a solution with minimal disruption to the current architecture and provide ease of migration to Google Cloud. What should you do?

- A. Migrate applications and Oracle databases to Google Cloud VMware Engine (VMware Engine).
- B. Migrate applications and Oracle databases to Compute Engine.
- C. Migrate applications to Cloud SQL.
- D. Migrate applications and Oracle databases to Google Kubernetes Engine (GKE).

**Question #3A:**

- [Migrate databases to Google Cloud VMware Engine (GCVE)](https://cloud.google.com/blog/products/databases/migrate-databases-to-google-cloud-vmware-engine-gcve)

> The following blog covers some common processes and tools used to migrate databases from on-premises (Physical or VMware) to Google Cloud VMware Engine (GCVE). Many customers choose this lift-and-shift migration approach as a first step to quickly migrate databases into Google Cloud before beginning database upgrade and modernization workstreams.

<hr />

**Question #4:**
Your customer has a global chat application that uses a multi-regional Cloud Spanner instance. The application has recently experienced degraded performance after a new version of the application was launched. Your customer asked you for assistance. During initial troubleshooting, you observed high read latency. What should you do?

- A. Use query parameters to speed up frequently executed queries.
- B. Change the Cloud Spanner configuration from multi-region to single region.
- C. Use SQL statements to analyze SPANNER_SYS.READ_STATS\* tables.
- D. Use SQL statements to analyze SPANNER_SYS.QUERY_STATS\* tables.

**Question #4A:**

- [Read statistics](https://cloud.google.com/spanner/docs/introspection/read-statistics)

> Cloud Spanner provides built-in tables that store statistics about reads. You can retrieve statistics from these SPANNER_SYS.READ_STATS\* tables using SQL statements.

<hr />

**Question #5:**
Your company has PostgreSQL databases on-premises and on Amazon Web Services (AWS). You are planning multiple database migrations to Cloud SQL in an effort to reduce costs and downtime. You want to follow Google-recommended practices and use Google native data migration tools. You also want to closely monitor the migrations as part of the cutover strategy. What should you do?

- A. Use Database Migration Service to migrate all databases to Cloud SQL.
- B. Use Database Migration Service for one-time migrations, and use third-party or partner tools for change data capture (CDC) style migrations.
- C. Use data replication tools and CDC tools to enable migration.
- D. Use a combination of Database Migration Service and partner tools to support the data migration strategy.

**Question #5A:**

- A.

  > The question says to use Google native data migration tools. That eliminates B and D. C doesn't specify the data replication tool in question so it's a reasonable assumption its referring to database native replication which wouldn't be a Google native solution. That eliminates C. That leave A.

- [Best practices for homogeneous database migrations](https://cloud.google.com/blog/products/databases/tips-for-migrating-across-compatible-database-engines)
- [Database Migration Service](https://cloud.google.com/database-migration/)

<hr />

**Question #6:**
You are setting up a Bare Metal Solution environment. You need to update the operating system to the latest version. You need to connect the Bare Metal Solution environment to the internet so you can receive software updates. What should you do?

- A. Setup a static external IP address in your VPC network.
- B. Set up bring your own IP (BYOIP) in your VPC.
- C. Set up a Cloud NAT gateway on the Compute Engine VM.
- D. Set up Cloud NAT service.

**Question #6A:**

- C or D (67%, 33%)
- D

  > The BMS documentation mentions the Cloud NAT service as an option but the provided example involves manually deploying a NAT gateway on a GCE machine, without explaining why you would need this option as opposed to the managed NAT service. However there are no limitations mentioned, so I take it both options are valid.

  > In this question, there is no mention of an existing GCE machine, therefore a managed NAT service is the simplest option, which avoids additional infrastructure - hence D is my choice.

- https://cloud.google.com/bare-metal/docs/bms-setup#bms-access-internet

<hr />

**Question #7:**
Your organization is running a MySQL workload in Cloud SQL. Suddenly you see a degradation in database performance. You need to identify the root cause of the performance degradation. What should you do?

- A. Use Logs Explorer to analyze log data.
- B. Use Cloud Monitoring to monitor CPU, memory, and storage utilization metrics.
- C. Use Error Reporting to count, analyze, and aggregate the data.
- D. Use Cloud Debugger to inspect the state of an application.

**Question #7A:**

- B.

> No actual errors are mentioned so using Error reporting would be irrelevant. That eliminates C. Inspecting the state of an application is also irrelevant since so mention of any application changes is made. Eliminate D. That leave A and B and B is the best answer. In Cloud SQL you get monitoring built right in (which you don't by default with GCE VMs). Cloud SQL monitoring metrics include CPU utilization, storage usage, memory usage, r/w operations and egress/ingress bytes. Has to be B.

<hr />

**Question #8:**
You work for a large retail and ecommerce company that is starting to extend their business globally. Your company plans to migrate to Google Cloud. You want to use platforms that will scale easily, handle transactions with the least amount of latency, and provide a reliable customer experience. You need a storage layer for sales transactions and current inventory levels. You want to retain the same relational schema that your existing platform uses. What should you do?

- A. Store your data in Firestore in a multi-region location, and place your compute resources in one of the constituent regions.
- B. Deploy Cloud Spanner using a multi-region instance, and place your compute resources close to the default leader region.
- C. Build an in-memory cache in Memorystore, and deploy to the specific geographic regions where your application resides.
- D. Deploy a Bigtable instance with a cluster in one region and a replica cluster in another geographic region.

**Question #8A:**

- B.
  > The clues are "globally" and "relational schema". Relational rules out Firestore (A) and Bigtable (D). Cloud Spanner is both global in scale and relational, so it fits. So B.

<hr />

**Question #9:**
You host an application in Google Cloud. The application is located in a single region and uses Cloud SQL for transactional data. Most of your users are located in the same time zone and expect the application to be available 7 days a week, from 6 AM to 10 PM. You want to ensure regular maintenance updates to your Cloud SQL instance without creating downtime for your users. What should you do?

- A. Configure a maintenance window during a period when no users will be on the system. Control the order of update by setting non-production instances to earlier and production instances to later.
- B. Create your database with one primary node and one read replica in the region.
- C. Enable maintenance notifications for users, and reschedule maintenance activities to a specific time after notifications have been sent.
- D. Configure your Cloud SQL instance with high availability enabled.

**Question #9A:**

- A
  > Since we don't really need HA and we have a window that users are not need our app - A is fine, and D looks like an overkill

<hr />

**Question #10:**
Your team recently released a new version of a highly consumed application to accommodate additional user traffic. Shortly after the release, you received an alert from your production monitoring team that there is consistently high replication lag between your primary instance and the read replicas of your Cloud SQL for MySQL instances. You need to resolve the replication lag. What should you do?

- A. Identify and optimize slow running queries, or set parallel replication flags.
- B. Stop all running queries, and re-create the replicas.
- C. Edit the primary instance to upgrade to a larger disk, and increase vCPU count.
- D. Edit the primary instance to add additional memory.

correct answer - A
https://cloud.google.com/sql/docs/mysql/replication/manage-replicas#:~:text=Replication%20lag%20is%20consistently,Find%20and%20fix%20them.

**Question #11:**
Your organization operates in a highly regulated industry. Separation of concerns (SoC) and security principle of least privilege (PoLP) are critical. The operations team consists of:
Person A is a database administrator.
Person B is an analyst who generates metric reports.

- A.plication C is responsible for automatic backups.
  You need to assign roles to team members for Cloud Spanner. Which roles should you assign?

- A. roles/spanner.databaseAdmin for Person A
  roles/spanner.databaseReader for Person B
  roles/spanner.backupWriter for Application C
- B. roles/spanner.databaseAdmin for Person A
  roles/spanner.databaseReader for Person B
  roles/spanner.backupAdmin for Application C
- C. roles/spanner.databaseAdmin for Person A
  roles/spanner.databaseUser for Person B
  roles/spanner databaseReader for Application C
- D. roles/spanner.databaseAdmin for Person A
  roles/spanner.databaseUser for Person B
  roles/spanner.backupWriter for Application C

**Question #11:A**

- A.
- B and C are obviously wrong because application only needs backupWriter permissions.
- D is wrong because roles/spanner.databaseUser contains write permissions, and we don't need that.
- https://cloud.google.com/spanner/docs/iam#roles
  > roles/spanner.databaseUser contains the permissions spanner.databases.read and spanner.databases.write.

<hr />

**Question #12:**
You are designing an augmented reality game for iOS and Android devices. You plan to use Cloud Spanner as the primary backend database for game state storage and player authentication. You want to track in-game rewards that players unlock at every stage of the game. During the testing phase, you discovered that costs are much higher than anticipated, but the query response times are within the SLA. You want to follow Google-recommended practices. You need the database to be performant and highly available while you keep costs low. What should you do?

- A. Manually scale down the number of nodes after the peak period has passed.
- B. Use interleaving to co-locate parent and child rows.
- C. Use the Cloud Spanner query optimizer to determine the most efficient way to execute the SQL query.
- D. Use granular instance sizing in Cloud Spanner and Autoscaler.

**Question #12A:**

- D.
  > A is nonsense. Using interleaved tables can help speed up queries, but the question says query response times are OK. So B is wrong. C is wrong for the same reason. That leaves D. The question is about which factors determine the cost of running Spanner. They include region vs. multi-region, compute unit (nodes or processing units), how much storage and how much backup space. From the Google docs, it says “When you create a Cloud Spanner instance, you choose the number of compute capacity nodes or processing units to serve your data. However, if the workload of an instance changes, Cloud Spanner doesn't automatically adjust the size of the instance. This document introduces the Autoscaler tool for Cloud Spanner (Autoscaler), an open source tool that you can use as a companion tool to Cloud Spanner. This tool lets you automatically increase or reduce the number of nodes or processing units in one or more Spanner instances based on how their capacity is being used.”
  > https://cloud.google.com/spanner/docs/autoscaling-overview

<hr />

**Question #13:**
You recently launched a new product to the US market. You currently have two Bigtable clusters in one US region to serve all the traffic. Your marketing team is planning an immediate expansion to APAC. You need to roll out the regional expansion while implementing high availability according to Google-recommended practices. What should you do?

- A. Maintain a target of 23% CPU utilization by locating:

  - cluster-a in zone us-central1-a
  - cluster-b in zone europe-west1-d
  - cluster-c in zone asia-east1-b

- B. Maintain a target of 23% CPU utilization by locating:

  - cluster-a in zone us-central1-a
  - cluster-b in zone us-central1-b
  - cluster-c in zone us-east1-a

- C. Maintain a target of 35% CPU utilization by locating:

  - cluster-a in zone us-central1-a
  - cluster-b in zone australia-southeast1-a
  - cluster-c in zone europe-west1-d
  - cluster-d in zone asia-east1-b

- D. Maintain a target of 35% CPU utilization by locating:
  - cluster-a in zone us-central1-a
  - cluster-b in zone us-central2-a
  - cluster-c in zone asia-northeast1-b
  - cluster-d in zone asia-east1-b

**Question #13A:**

- Looks like D to me - it's the only one with 2 US and 2 Asia regions. Also https://cloud.google.com/bigtable/docs/replication-settings#regional-failover

<hr />

**Question #14:**
Your ecommerce website captures user clickstream data to analyze customer traffic patterns in real time and support personalization features on your website. You plan to analyze this data using big data tools. You need a low-latency solution that can store 8 TB of data and can scale to millions of read and write requests per second. What should you do?

- A. Write your data into Bigtable and use Dataproc and the Apache Hbase libraries for analysis.
- B. Deploy a Cloud SQL environment with read replicas for improved performance. Use Datastream to export data to Cloud Storage and analyze with Dataproc and the Cloud Storage connector.
- C. Use Memorystore to handle your low-latency requirements and for real-time analytics.
- D. Stream your data into BigQuery and use Dataproc and the BigQuery Storage API to analyze large volumes of data.

- A.
  > Cloud SQL could not handle the load, so B is wrong. Memorystore can scale up to 300 GB. The question mentions needing 8 TB, so C must be wrong. BigQuery could not handle the latency requirements of the question, which leaves A. Bigtable could handle the volume of writes at the speeds required.

<hr />

**Question #15:**
Your company uses Cloud Spanner for a mission-critical inventory management system that is globally available. You recently loaded stock keeping unit (SKU) and product catalog data from a company acquisition and observed hotspots in the Cloud Spanner database. You want to follow Google-recommended schema design practices to avoid performance degradation. What should you do? (Choose two.)

- A. Use an auto-incrementing value as the primary key.
- B. Normalize the data model.
- C. Promote low-cardinality attributes in multi-attribute primary keys.
- D. Promote high-cardinality attributes in multi-attribute primary keys.
- E. Use bit-reverse sequential value as the primary key.

**Question #16:**
You are managing multiple applications connecting to a database on Cloud SQL for PostgreSQL. You need to be able to monitor database performance to easily identify applications with long-running and resource-intensive queries. What should you do?

- A. Use log messages produced by Cloud SQL.
- B. Use Query Insights for Cloud SQL.
- C. Use the Cloud Monitoring dashboard with available metrics from Cloud SQL.
- D. Use Cloud SQL instance monitoring in the Google Cloud Console.

**Question #16A:**

- Selected Answer: D
  > The Cloud SQL System insights dashboard helps you detect and analyze system performance problems.
  > https://cloud.google.com/sql/docs/postgres/monitor-instance#sql-system-insights

<hr />

**Question #17:**
You are building an application that allows users to customize their website and mobile experiences. The application will capture user information and preferences. User profiles have a dynamic schema, and users can add or delete information from their profile. You need to ensure that user changes automatically trigger updates to your downstream BigQuery data warehouse. What should you do?

- A. Store your data in Bigtable, and use the user identifier as the key. Use one column family to store user profile data, and use another column family to store user preferences.
- B. Use Cloud SQL, and create different tables for user profile data and user preferences from your recommendations model. Use SQL to join the user profile data and preferences
- C. Use Firestore in Native mode, and store user profile data as a document. Update the user profile with preferences specific to that user and use the user identifier to query.
- D. Use Firestore in Datastore mode, and store user profile data as a document. Update the user profile with preferences specific to that user and use the user identifier to query.

**Question #17:A**

- C
  > Dynamic schema indicates this is a NoSQL solution (ruling out Cloud SQL) and the application use case specifically suits Firestore (the question even refers to storing data in documents) as opposed to BigTable.

Firestore in Native supports realtime client updates, which is needed for the analytics requirement: https://cloud.google.com/firestore/docs/firestore-or-datastore#feature_comparison

<hr />

**Question #18:**
Your application uses Cloud SQL for MySQL. Your users run reports on data that relies on near-real time; however, the additional analytics caused excessive load on the primary database. You created a read replica for the analytics workloads, but now your users are complaining about the lag in data changes and that their reports are still slow. You need to improve the report performance and shorten the lag in data replication without making changes to the current reports. Which two approaches should you implement? (Choose two.)

- A. Create secondary indexes on the replica.
- B. Create additional read replicas, and partition your analytics users to use different read replicas.
- C. Disable replication on the read replica, and set the flag for parallel replication on the read replica. Re-enable replication and optimize performance by setting flags on the primary instance.
- D. Disable replication on the primary instance, and set the flag for parallel replication on the primary instance. Re-enable replication and optimize performance by setting flags on the read replica.
  E. Move your analytics workloads to BigQuery, and set up a streaming pipeline to move data and update BigQuery.

- Vote for AC
- A https://cloud.google.com/sql/docs/mysql/replication/read-replica-indexes increase performance on read operation
- C https://cloud.google.com/sql/docs/mysql/replication/manage-replicas#basic-steps-to-change-parallel-replication-flags
- BC
- A. Create secondary indexes on the replica. - No indication that the reports will benefit from indexes.
- B. Create additional read replicas, and partition your analytics users to use different read replicas. --> might rebalance the load.
- C. Disable replication on the read replica, and set the flag for parallel replication on the read replica. Re-enable replication and optimize performance by setting flags on the primary instance. --> might add parallelism to the replication lag.
- D. Disable replication on the primary instance, and set the flag for parallel replication on the primary instance. Re-enable replication and optimize performance by setting flags on the read replica. --> na
- E. Move your analytics workloads to BigQuery, and set up a streaming pipeline to move data and update BigQuery.--> according to question statement , no SQL rewrite is possible

<hr />

**Question #19:**
You are evaluating Cloud SQL for PostgreSQL as a possible destination for your on-premises PostgreSQL instances. Geography is becoming increasingly relevant to customer privacy worldwide. Your solution must support data residency requirements and include a strategy to: configure where data is stored control where the encryption keys are stored govern the access to data
What should you do?

- A. Replicate Cloud SQL databases across different zones.
- B. Create a Cloud SQL for PostgreSQL instance on Google Cloud for the data that does not need to adhere to data residency requirements. Keep the data that must adhere to data residency requirements on-premises. Make application changes to support both databases.
- C. Allow application access to data only if the users are in the same region as the Google Cloud region for the Cloud SQL for PostgreSQL database.
- D. Use features like customer-managed encryption keys (CMEK), VPC Service Controls, and Identity and Access Management (IAM) policies.

**Question #19:A**

- D, https://cloud.google.com/blog/products/identity-security/meet-data-residency-requirements-with-google-cloud

**Question #20:**
Your customer is running a MySQL database on-premises with read replicas. The nightly incremental backups are expensive and add maintenance overhead. You want to follow Google-recommended practices to migrate the database to Google Cloud, and you need to ensure minimal downtime. What should you do?

- A. Create a Google Kubernetes Engine (GKE) cluster, install MySQL on the cluster, and then import the dump file.
- B. Use the mysqldump utility to take a backup of the existing on-premises database, and then import it into Cloud SQL.
- C. Create a Compute Engine VM, install MySQL on the VM, and then import the dump file.
- D. Create an external replica, and use Cloud SQL to synchronize the data to the replica.

- D.
  > The question says backups and maintenance are an issue, so moving to a managed service (Cloud SQL) would be the right thing to do. That eliminates C and A. Option B could (depending upon the DB size) require a lot of downtime to export, copy the dump file to Cloud Storage, then import into Cloud SQL. Therefore, the least amount of downtime would be D.
  > https://cloud.google.com/sql/docs/mysql/replication/configure-replication-from-external
- B
- https://cloud.google.com/database-migration/docs/mysql/mysql-dump

<hr />

**Question #21:**
Your team uses thousands of connected IoT devices to collect device maintenance data for your oil and gas customers in real time. You want to design inspection routines, device repair, and replacement schedules based on insights gathered from the data produced by these devices. You need a managed solution that is highly scalable, supports a multi-cloud strategy, and offers low latency for these IoT devices. What should you do?

- A. Use Firestore with Looker.
- B. Use Cloud Spanner with Data Studio.
- C. Use MongoD8 Atlas with Charts.
- D. Use Bigtable with Looker.

**Question #21:A**

- C
- MongoDB Atlas supports "multi-cloud" https://www.mongodb.com/atlas/database
- We are missing one key condition "multi-cloud strategy". MongoDB Atlas is the only multi-cloud data service available. So, Answer is C
- Bigtable can't connect to Looker - https://cloud.google.com/looker/docs/dialects

<hr />

**Question #22:**
Your application follows a microservices architecture and uses a single large Cloud SQL instance, which is starting to have performance issues as your application grows. in the Cloud Monitoring dashboard, the CPU utilization looks normal You want to follow Google-recommended practices to resolve and prevent these performance issues while avoiding any major refactoring. What should you do?

- A. Use Cloud Spanner instead of Cloud SQL.
- B. Increase the number of CPUs for your instance.
- C. Increase the storage size for the instance.
- D. Use many smaller Cloud SQL instances.

**Question #22:A**

- Correct answer is D. https://cloud.google.com/sql/docs/mysql/best-practices#data-arch - Split your large instances into smaller instances, where possible.

<hr />

**Question #23:**
You need to perform a one-time migration of data from a running Cloud SQL for MySQL instance in the us-central1 region to a new Cloud SQL for MySQL instance in the us-east1 region. You want to follow Google-recommended practices to minimize performance impact on the currently running instance. What should you do?

- A. Create and run a Dataflow job that uses JdbcIO to copy data from one Cloud SQL instance to another.
- B. Create two Datastream connection profiles, and use them to create a stream from one Cloud SQL instance to another.
- C. Create a SQL dump file in Cloud Storage using a temporary instance, and then use that file to import into a new instance.
- D. Create a CSV file by running the SQL statement SELECT...INTO OUTFILE, copy the file to a Cloud Storage bucket, and import it into a new instance.

**Question #23:A**

- C.
  > The only way to minimize performance impact of running an export on a Cloud SQL instance is to use a serverless export. The fact that no data synchronization is needed since it’s a one off eliminates every option apart from C.
- C - serverless export https://cloud.google.com/sql/docs/mysql/import-export#serverless
<hr />

**Question #24:**
You are running a mission-critical application on a Cloud SQL for PostgreSQL database with a multi-zonal setup. The primary and read replica instances are in the same region but in different zones. You need to ensure that you split the application load between both instances. What should you do?

- A. Use Cloud Load Balancing for load balancing between the Cloud SQL primary and read replica instances.
- B. Use PgBouncer to set up database connection pooling between the Cloud SQL primary and read replica instances.
- C. Use HTTP(S) Load Balancing for database connection pooling between the Cloud SQL primary and read replica instances.
- D. Use the Cloud SQL Auth proxy for database connection pooling between the Cloud SQL primary and read replica instances.

**Question #25:**
Your organization deployed a new version of a critical application that uses Cloud SQL for MySQL with high availability (HA) and binary logging enabled to store transactional information. The latest release of the application had an error that caused massive data corruption in your Cloud SQL for MySQL database. You need to minimize data loss. What should you do?

- A. Open the Google Cloud Console, navigate to SQL > Backups, and select the last version of the automated backup before the corruption.
- B. Reload the Cloud SQL for MySQL database using the LOAD DATA command to load data from CSV files that were used to initialize the instance.
- C. Perform a point-in-time recovery of your Cloud SQL for MySQL database, selecting a date and time before the data was corrupted.
- D. Fail over to the Cloud SQL for MySQL HA instance. Use that instance to recover the transactions that occurred before the corruption.

**Question #26:**
You plan to use Database Migration Service to migrate data from a PostgreSQL on-premises instance to Cloud SQL. You need to identify the prerequisites for creating and automating the task. What should you do? (Choose two.)

- A. Drop or disable all users except database administration users.
- B. Disable all foreign key constraints on the source PostgreSQL database.
- C. Ensure that all PostgreSQL tables have a primary key.
- D. Shut down the database before the Data Migration Service task is started.
- E. Ensure that pglogical is installed on the source PostgreSQL database.

**Question #27:**
You are using Compute Engine on Google Cloud and your data center to manage a set of MySQL databases in a hybrid configuration. You need to create replicas to scale reads and to offload part of the management operation. What should you do?

- A. Use external server replication.
- B. Use Data Migration Service.
- C. Use Cloud SQL for MySQL external replica.
- D. Use the mysqldump utility and binary logs.

**Question #28:**
Your company is shutting down their data center and migrating several MySQL and PostgreSQL databases to Google Cloud. Your database operations team is severely constrained by ongoing production releases and the lack of capacity for additional on-premises backups. You want to ensure that the scheduled migrations happen with minimal downtime and that the Google Cloud databases stay in sync with the on-premises data changes until the applications can cut over. What should you do? (Choose two.)

- A. Use Database Migration Service to migrate the databases to Cloud SQL.
- B. Use a cross-region read replica to migrate the databases to Cloud SQL.
- C. Use replication from an external server to migrate the databases to Cloud SQL.
- D. Use an external read replica to migrate the databases to Cloud SQL.
- E. Use a read replica to migrate the databases to Cloud SQL.

**Question #29:**

Your company is migrating the existing infrastructure for a highly transactional application to Google Cloud. You have several databases in a MySQL database instance and need to decide how to transfer the data to Cloud SQL. You need to minimize the downtime for the migration of your 500 GB instance. What should you do?

- A.

  1. Create a Cloud SQL for MySQL instance for your databases, and configure Datastream to stream your database changes to Cloud SQL.
  2. Select the Backfill historical data check box on your stream configuration to initiate Datastream to backfill any data that is out of sync between the source and destination.
  3. Delete your stream when all changes are moved to Cloud SQL for MySQL, and update your application to use the new instance.

- B.

  1. Create migration job using Database Migration Service.
  2. Set the migration job type to Continuous, and allow the databases to complete the full dump phase and start sending data in change data capture (CDC) mode.
  3. Wait for the replication delay to minimize, initiate a promotion of the new Cloud SQL instance, and wait for the migration job to complete.
  4. Update your application connections to the new instance.

- C.

  1. Create migration job using Database Migration Service.
  2. Set the migration job type to One-time, and perform this migration during a maintenance window.
  3. Stop all write workloads to the source database and initiate the dump. Wait for the dump to be loaded into the Cloud SQL destination database and the destination database to be promoted to the primary database.
  4. Update your application connections to the new instance.

- D.

1. Use the mysqldump utility to manually initiate a backup of MySQL during the application maintenance window.
2. Move the files to Cloud Storage, and import each database into your Cloud SQL instance.
3. Continue to dump each database until all the databases are migrated.
4. Update your application connections to the new instance.

**Question #30:**
Your company uses the Cloud SQL out-of-disk recommender to analyze the storage utilization trends of production databases over the last 30 days. Your database operations team uses these recommendations to proactively monitor storage utilization and implement corrective actions. You receive a recommendation that the instance is likely to run out of disk space. What should you do to address this storage alert?

- A. Normalize the database to the third normal form.
- B. Compress the data using a different compression algorithm.
- C. Manually or automatically increase the storage capacity.
- D. Create another schema to load older data.

**Question #31:**
You are managing a mission-critical Cloud SQL for PostgreSQL instance. Your application team is running important transactions on the database when another DBA starts an on-demand backup. You want to verify the status of the backup. What should you do?

- A. Check the cloudsql.googleapis.com/postgres.log instance log.
- B. Perform the gcloud sql operations list command.
- C. Use Cloud Audit Logs to verify the status.
- D. Use the Google Cloud Console.

**Question #32:**
You support a consumer inventory application that runs on a multi-region instance of Cloud Spanner. A customer opened a support ticket to complain about slow response times. You notice a Cloud Monitoring alert about high CPU utilization. You want to follow Google-recommended practices to address the CPU performance issue. What should you do first?

- A. Increase the number of processing units.
- B. Modify the database schema, and add additional indexes.
- C. Shard data required by the application into multiple instances.
- D. Decrease the number of processing units.

**Question #33:**
Your company uses Bigtable for a user-facing application that displays a low-latency real-time dashboard. You need to recommend the optimal storage type for this read-intensive database. What should you do?

- A. Recommend solid-state drives (SSD).
- B. Recommend splitting the Bigtable instance into two instances in order to load balance the concurrent reads.
- C. Recommend hard disk drives (HDD).
- D. Recommend mixed storage types.

**Question #34:**
Your organization has a critical business app that is running with a Cloud SQL for MySQL backend database. Your company wants to build the most fault-tolerant and highly available solution possible. You need to ensure that the application database can survive a zonal and regional failure with a primary region of us-central1 and the backup region of us-east1. What should you do?

- A.
  - 1. Provision a Cloud SQL for MySQL instance in us-central1-a.
  - 2. Create a multiple-zone instance in us-west1-b.
  - 3. Create a read replica in us-east1-c.
- B.
  - 1. Provision a Cloud SQL for MySQL instance in us-central1-a.
  - 2. Create a multiple-zone instance in us-central1-b.
  - 3. Create a read replica in us-east1-b.
- C.
  - 1. Provision a Cloud SQL for MySQL instance in us-central1-a.
  - 2. Create a multiple-zone instance in us-east-b.
  - 3. Create a read replica in us-east1-c.
- D.
  - 1. Provision a Cloud SQL for MySQL instance in us-central1-a.
  - 2. Create a multiple-zone instance in us-east1-b.
  - 3. Create a read replica in us-central1-b.

**Question #35:**
You are building an Android game that needs to store data on a Google Cloud serverless database. The database will log user activity, store user preferences, and receive in-game updates. The target audience resides in developing countries that have intermittent internet connectivity. You need to ensure that the game can synchronize game data to the backend database whenever an internet network is available. What should you do?

- A. Use Firestore.
- B. Use Cloud SQL with an external (public) IP address.
- C. Use an in-app embedded database.
- D. Use Cloud Spanner.

**Question #36:**
You released a popular mobile game and are using a 50 TB Cloud Spanner instance to store game data in a PITR-enabled production environment. When you analyzed the game statistics, you realized that some players are exploiting a loophole to gather more points to get on the leaderboard. Another DBA accidentally ran an emergency bugfix script that corrupted some of the data in the production environment. You need to determine the extent of the data corruption and restore the production environment. What should you do? (Choose two.)

- A. If the corruption is significant, use backup and restore, and specify a recovery timestamp.
- B. If the corruption is significant, perform a stale read and specify a recovery timestamp. Write the results back.
- C. If the corruption is significant, use import and export.
- D. If the corruption is insignificant, use backup and restore, and specify a recovery timestamp.
- E. If the corruption is insignificant, perform a stale read and specify a recovery timestamp. Write the results back.

**Question #37:**
You are starting a large CSV import into a Cloud SQL for MySQL instance that has many open connections. You checked memory and CPU usage, and sufficient resources are available. You want to follow Google-recommended practices to ensure that the import will not time out. What should you do?

- A. Close idle connections or restart the instance before beginning the import operation.
- B. Increase the amount of memory allocated to your instance.
- C. Ensure that the service account has the Storage Admin role.
- D. Increase the number of CPUs for the instance to ensure that it can handle the additional import operation.

**Question #38:**
You are migrating your data center to Google Cloud. You plan to migrate your applications to Compute Engine and your Oracle databases to Bare Metal Solution for Oracle. You must ensure that the applications in different projects can communicate securely and efficiently with the Oracle databases. What should you do?

- A. Set up a Shared VPC, configure multiple service projects, and create firewall rules.
- B. Set up Serverless VPC Access.
- C. Set up Private Service Connect.
- D. Set up Traffic Director.

**Question #39:**
You are running an instance of Cloud Spanner as the backend of your ecommerce website. You learn that the quality assurance (QA) team has doubled the number of their test cases. You need to create a copy of your Cloud Spanner database in a new test environment to accommodate the additional test cases. You want to follow Google-recommended practices. What should you do?

- A. Use Cloud Functions to run the export in Avro format.
- B. Use Cloud Functions to run the export in text format.
- C. Use Dataflow to run the export in Avro format.
- D. Use Dataflow to run the export in text format.

**Question #40:**
You need to redesign the architecture of an application that currently uses Cloud SQL for PostgreSQL. The users of the application complain about slow query response times. You want to enhance your application architecture to offer sub-millisecond query latency. What should you do?

- A. Configure Firestore, and modify your application to offload queries.
- B. Configure Bigtable, and modify your application to offload queries.
- C. Configure Cloud SQL for PostgreSQL read replicas to offload queries.
- D. Configure Memorystore, and modify your application to offload queries.

**Question #41:**
You need to migrate existing databases from Microsoft SQL Server 2016 Standard Edition on a single Windows Server 2019 Datacenter Edition to a single Cloud SQL for SQL Server instance. During the discovery phase of your project, you notice that your on-premises server peaks at around 25,000 read IOPS. You need to ensure that your Cloud SQL instance is sized appropriately to maximize read performance. What should you do?

- A. Create a SQL Server 2019 Standard on Standard machine type with 4 vCPUs, 15 GB of RAM, and 800 GB of solid-state drive (SSD).
- B. Create a SQL Server 2019 Standard on High Memory machine type with at least 16 vCPUs, 104 GB of RAM, and 200 GB of SSD.
- C. Create a SQL Server 2019 Standard on High Memory machine type with 16 vCPUs, 104 GB of RAM, and 4 TB of SSD.
- D. Create a SQL Server 2019 Enterprise on High Memory machine type with 16 vCPUs, 104 GB of RAM, and 500 GB of SSD.

**Question #42:**
You are managing a small Cloud SQL instance for developers to do testing. The instance is not critical and has a recovery point objective (RPO) of several days. You want to minimize ongoing costs for this instance. What should you do?

- A. Take no backups, and turn off transaction log retention.
- B. Take one manual backup per day, and turn off transaction log retention.
- C. Turn on automated backup, and turn off transaction log retention.
- D. Turn on automated backup, and turn on transaction log retention.

**Question #43:**
You manage a meeting booking application that uses Cloud SQL. During an important launch, the Cloud SQL instance went through a maintenance event that resulted in a downtime of more than 5 minutes and adversely affected your production application. You need to immediately address the maintenance issue to prevent any unplanned events in the future. What should you do?

- A. Set your production instance's maintenance window to non-business hours.
- B. Migrate the Cloud SQL instance to Cloud Spanner to avoid any future disruptions due to maintenance.
- C. Contact Support to understand why your Cloud SQL instance had a downtime of more than 5 minutes.
- D. Use Cloud Scheduler to schedule a maintenance window of no longer than 5 minutes.

**Question #44:**
You are designing a highly available (HA) Cloud SQL for PostgreSQL instance that will be used by 100 databases. Each database contains 80 tables that were migrated from your on-premises environment to Google Cloud. The applications that use these databases are located in multiple regions in the US, and you need to ensure that read and write operations have low latency. What should you do?

- A. Deploy 2 Cloud SQL instances in the us-central1 region with HA enabled, and create read replicas in us-east1 and us-west1.
- B. Deploy 2 Cloud SQL instances in the us-central1 region, and create read replicas in us-east1 and us-west1.
- C. Deploy 4 Cloud SQL instances in the us-central1 region with HA enabled, and create read replicas in us-central1, us-east1, and us-west1.
- D. Deploy 4 Cloud SQL instances in the us-central1 region, and create read replicas in us-central1, us-east1 and us-west1.

**Question #45:**
You work in the logistics department. Your data analysis team needs daily extracts from Cloud SQL for MySQL to train a machine learning model. The model will be used to optimize next-day routes. You need to export the data in CSV format. You want to follow Google-recommended practices. What should you do?

- A. Use Cloud Scheduler to trigger a Cloud Function that will run a select \_ from table(s) query to call the cloudsql.instances.export API.
- B. Use Cloud Scheduler to trigger a Cloud Function through Pub/Sub to call the cloudsql.instances.export API.
- C. Use Cloud Composer to orchestrate an export by calling the cloudsql.instances.export API.
- D. Use Cloud Composer to execute a select \_ from table(s) query and export results.

**Question #46:**
You are choosing a database backend for a new application. The application will ingest data points from IoT sensors. You need to ensure that the application can scale up to millions of requests per second with sub-10ms latency and store up to 100 TB of history. What should you do?

- A. Use Cloud SQL with read replicas for throughput.
- B. Use Firestore, and rely on automatic serverless scaling.
- C. Use Memorystore for Memcached, and add nodes as necessary to achieve the required throughput.
- D. Use Bigtable, and add nodes as necessary to achieve the required throughput.

**Question #47:**
You are designing a payments processing application on Google Cloud. The application must continue to serve requests and avoid any user disruption if a regional failure occurs. You need to use AES-256 to encrypt data in the database, and you want to control where you store the encryption key. What should you do?

- A. Use Cloud Spanner with a customer-managed encryption key (CMEK).
- B. Use Cloud Spanner with default encryption.
- C. Use Cloud SQL with a customer-managed encryption key (CMEK).
- D. Use Bigtable with default encryption

**Question #48:**
You are managing a Cloud SQL for MySQL environment in Google Cloud. You have deployed a primary instance in Zone A and a read replica instance in Zone B, both in the same region. You are notified that the replica instance in Zone B was unavailable for 10 minutes. You need to ensure that the read replica instance is still working. What should you do?

- A. Use the Google Cloud Console or gcloud CLI to manually create a new clone database.
- B. Use the Google Cloud Console or gcloud CLI to manually create a new failover replica from backup.
- C. Verify that the new replica is created automatically.
- D. Start the original primary instance and resume replication.

**Question #49:**
You are migrating an on-premises application to Google Cloud. The application requires a high availability (HA) PostgreSQL database to support business-critical functions. Your company's disaster recovery strategy requires a recovery time objective (RTO) and recovery point objective (RPO) within 30 minutes of failure. You plan to use a Google Cloud managed service. What should you do to maximize uptime for your application?

- A. Deploy Cloud SQL for PostgreSQL in a regional configuration. Create a read replica in a different zone in the same region and a read replica in another region for disaster recovery.
- B. Deploy Cloud SQL for PostgreSQL in a regional configuration with HA enabled. Take periodic backups, and use this backup to restore to a new Cloud SQL for PostgreSQL instance in another region during a disaster recovery event.
- C. Deploy Cloud SQL for PostgreSQL in a regional configuration with HA enabled. Create a cross-region read replica, and promote the read replica as the primary node for disaster recovery.
- D. Migrate the PostgreSQL database to multi-regional Cloud Spanner so that a single region outage will not affect your application. Update the schema to support Cloud Spanner data types, and refactor the application.

**Question #50:**
Your team is running a Cloud SQL for MySQL instance with a 5 TB database that must be available 24/7. You need to save database backups on object storage with minimal operational overhead or risk to your production workloads. What should you do?

- A. Use Cloud SQL serverless exports.
- B. Create a read replica, and then use the mysqldump utility to export each table.
- C. Clone the Cloud SQL instance, and then use the mysqldump utlity to export the data.
- D. Use the mysqldump utility on the primary database instance to export the backup.

**Question #51:**
You are deploying a new Cloud SQL instance on Google Cloud using the Cloud SQL Auth proxy. You have identified snippets of application code that need to access the new Cloud SQL instance. The snippets reside and execute on an application server running on a Compute Engine machine. You want to follow Google-recommended practices to set up Identity and Access Management (IAM) as quickly and securely as possible. What should you do?

- A. For each application code, set up a common shared user account.
- B. For each application code, set up a dedicated user account.
- C. For the application server, set up a service account.
- D. For the application server, set up a common shared user account.

**Question #52:**
Your organization is running a low-latency reporting application on Microsoft SQL Server. In addition to the database engine, you are using SQL Server Analysis Services (SSAS), SQL Server Reporting Services (SSRS), and SQL Server Integration Services (SSIS) in your on-premises environment. You want to migrate your Microsoft SQL Server database instances to Google Cloud. You need to ensure minimal disruption to the existing architecture during migration. What should you do?

- A. Migrate to Cloud SQL for SQL Server.
- B. Migrate to Cloud SQL for PostgreSQL.
- C. Migrate to Compute Engine.
- D. Migrate to Google Kubernetes Engine (GKE).

**Question #53:**

- A. analytics team needs to read data out of Cloud SQL for SQL Server and update a table in Cloud Spanner. You need to create a service account and grant least privilege access using predefined roles. What roles should you assign to the service account?

- A. roles/cloudsql.viewer and roles/spanner.databaseUser
- B. roles/cloudsql.editor and roles/spanner.admin
- C. roles/cloudsql.client and roles/spanner.databaseReader
- D. roles/cloudsql.instanceUser and roles/spanner.databaseUser

**Question #54:**
You are responsible for designing a new database for an airline ticketing application in Google Cloud. This application must be able to:
Work with transactions and offer strong consistency.
Work with structured and semi-structured (JSON) data.
Scale transparently to multiple regions globally as the operation grows.
You need a Google Cloud database that meets all the requirements of the application. What should you do?

- A. Use Cloud SQL for PostgreSQL with both cross-region read replicas.
- B. Use Cloud Spanner in a multi-region configuration.
- C. Use Firestore in Datastore mode.
- D. Use a Bigtable instance with clusters in multiple regions.

**Question #55:**
You are writing an application that will run on Cloud Run and require a database running in the Cloud SQL managed service. You want to secure this instance so that it only receives connections from applications running in your VPC environment in Google Cloud. What should you do?

- A.

  - 1. Create your instance with a specified external (public) IP address.
  - 2. Choose the VPC and create firewall rules to allow only connections from Cloud Run into your instance.
  - 3. Use Cloud SQL Auth proxy to connect to the instance.

- B.

  - 1. Create your instance with a specified external (public) IP address.
  - 2. Choose the VPC and create firewall rules to allow only connections from Cloud Run into your instance.
  - 3. Connect to the instance using a connection pool to best manage connections to the instance.

- C.

  - 1. Create your instance with a specified internal (private) IP address.
  - 2. Choose the VPC with private service connection configured.
  - 3. Configure the Serverless VPC Access connector in the same VPC network as your Cloud SQL instance.
  - 4. Use Cloud SQL Auth proxy to connect to the instance.

- D.
  - 1. Create your instance with a specified internal (private) IP address.
  - 2. Choose the VPC with private service connection configured.
  - 3. Configure the Serverless VPC Access connector in the same VPC network as your Cloud SQL instance.
  - 4. Connect to the instance using a connection pool to best manage connections to the instance.

**Question #56:**
You are troubleshooting a connection issue with a newly deployed Cloud SQL instance on Google Cloud. While investigating the Cloud SQL Proxy logs, you see the message Error 403: Access Not Configured. What should you do?

- A. Check the app.yaml value cloud_sql_instances for a misspelled or incorrect instance connection name.
- B. Check whether your service account has cloudsql.instances.connect permission.
- C. Enable the Cloud SQL Admin API.
- D. Ensure that you are using an external (public) IP address interface.
