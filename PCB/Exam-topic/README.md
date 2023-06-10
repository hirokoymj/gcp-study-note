# Questions

- Listed the wrong answered questions only.

## Q11

- principle of least privilege (PoLP)
- Cloud Spanner Backup Writer
  - spanner.backups.create
- Cloud Spanner Backup Admin
  - spanner.backups.create
  - spanner.backups.delete

## Q12

- The question is about which factors determine the cost of running Spanner. They include region vs. multi-region, compute unit (nodes or processing units), how much storage and how much backup space.
- Parent-child table relationships: table interleaving and foreign keys.
- Using interleaved tables can help speed up queries
- https://cloud.google.com/spanner/docs/schema-and-data-model#parent-child
- https://cloud.google.com/spanner/docs/autoscaling-overview

## Q15

- High Cardinality vs Low Cardinality
- Low Cardinality: a gender, three distinct(male, female or other)
- High Cardinality: email (a large number of distinct values (one for each person in the table)
- Bit-reverse sequential values
- https://cloud.google.com/spanner/docs/schema-design#bit_reverse_primary_key

## Q18

- You have 2 problems. Replication lag and slow report performance.
- Since excessive load is mentioned in the question, creating additional read replicas and spreading the analytics workload around makes B correct.
- Cloud SQL enables single threaded replication by default, so it stands to reason enabling parallel replication would help the lag.
- Basic steps to change parallel replication flags
  1. On a read replica, disable replication.
  2. On the read replica, set the flags for parallel replication. Use the gcloud command to set the flags.
- https://cloud.google.com/sql/docs/mysql/replication/manage-replicas#configuring-parallel-replication

## Q20

- MySQL on-premises with read replica
- backups and maintenance are issue
- Wants to migrate to GCP with minimum downtime
- Create an external replica, and use Cloud SQL to synchronize the data to the replica.(GOOD)
- Use the mysqldump utility to take a backup of the existing on-premises database, and then import it into Cloud SQL.(BAD)
- https://cloud.google.com/sql/docs/mysql/replication/configure-replication-from-external#mysql

## Q22

- Adding more storage would increase IOPS, but there’s no indication network throughput is an issue, so that eliminates C.
- A microservice architecture is supposed to use a separate database for each microservice, rather than one big database.
- https://cloud.google.com/sql/docs/mysql/best-practices#data-arch

## Q23

- Cloud SQL, serverless export
- Serverless export

  1. Cloud SQL creates a separate, temporary instance to offload the export operation.

  2. Offloading the export operation allows databases on the primary instance to continue to serve queries and perform operations at the usual performance rate.
  3. When the data export is complete, the temporary instance is deleted automatically.
  4. Use the Google Cloud Console, gcloud with the offload flag, to perform a serverless export operation.

  ```
  gcloud sql export sql INSTANCE_NAME gs://BUCKET_NAME/sqldumpfile.gz \
  --database=DATABASE_NAME \
  --offload
  ```

- A serverless export takes longer to do than a standard export, because it takes time to create the temporary instance.
- https://cloud.google.com/sql/docs/mysql/import-export#serverless
- https://cloud.google.com/sql/docs/mysql/import-export/import-export-sql#gcloud

## Q24

- PosgresSQL, load balancer btw primary instance and read replica
- For read-heavy workloads, add read replicas to offload traffic from the primary instance. Optionally, you can use a load balancer such as HAProxy to manage traffic to the replicas.
- PgBouncer as a connection pooler
- https://cloud.google.com/sql/docs/postgres/best-practices#admin
- https://cloud.google.com/architecture/migrating-postgresql-to-gcp

## Q27

- **External read replicas** are external MySQL instances that replicate from a Cloud SQL primary instance. For example, **a MySQL instance running on Compute Engine** is considered an external instance.
- https://cloud.google.com/sql/docs/mysql/replication#external-read-replicas

## Q28

- you wouldn’t use a read replica as a source anyway
- A is Database Migration Service to migrate the databases with CDC
- C is Replication from an external server is used to Migration Database to Cloud

# Q35

- https://firebase.google.com/docs/firestore
- Realtime updates Like Realtime Database, Cloud Firestore uses data synchronization to update data on any connected device. However, it's also designed to make simple, one-time fetch queries efficiently.

## Q36

- Spanner, ways to recover data
- To **recover a portion of the database**, perform a stale read specifying a query-condition and timestamp in the past, and then write the results back into the live database. This is typically used for surgical operations on a live database. For example, if you accidentally delete a particular row or incorrectly update a subset of data, you can recover it with this method.
- To **recover the entire database**, backup or export the database specifying a timestamp in the past and then restore or import it to a new database. This is typically used to recover from data corruption issues when you have to revert the database to a point-in-time before the corruption occurred.
- https://cloud.google.com/spanner/docs/pitr#ways-to-recover

## Q37

- Cloud SQL MySQL
- Google’s own documention says close unused operations and re-start the instance. This is the best way to ensure maximum resources for the import operation.
- Too many active connections can **interfere with** import operations.
- A restart:
  1. Closes all connections.
  2. Ends any tasks that may be consuming resources.
- https://cloud.google.com/sql/docs/mysql/import-export#troubleshooting

## Q39

- Spanner, export
- **Cloud Spanner to Cloud Storage Avro in the Dataflow** documentation.
- The export process uses Dataflow and writes data to a folder in a Cloud Storage bucket. The resulting folder contains a set of Avro files and JSON manifest files.
- https://cloud.google.com/spanner/docs/export

## Q40

- sub-millisecond latency
- To meet demands of low latency at increased scale and reduced cost you need an in-memory datastore. Redis and Memchaced are among the most popular.
- https://cloud.google.com/blog/topics/developers-practitioners/what-memorystore/

## Q41

- D is wrong since the IOPS would not improve based upon the edition of SQL Server. IOPS increases with the amount of storage,
- When creating a Cloud SQL for SQL Server instance, you have several machine configurations to choose from based on your vCPU and memory requirements.
- Lightweight
  - 1 vCPU, 3.75 GB
  - 2 vCPUs, 3.75 GB
  - 4 vCPUs, 3.75 GB
- Standard
  - 1 vCPU, 3.75 GB
  - 2 vCPUs, 7.50 GB
  - 4 vCPUs, 15 GB
- High Memory

  - 4 vCPUs, 26 GB
  - 8 vCPUs, 52 GB
  - 16 vCPUs, 104 GB

- https://cloud.google.com/sql/docs/sqlserver/create-instance#expandable-3

## Q47

- Cloud Spanner
- Avoiding user disruption if a regional failure occurs means you need to pick a multi-region service.

## Q48

- Read replica

- If replication is interrupted for a few hours, for example by a network or server outage, the replica falls behind the primary. The replica catches up once it reconnects to the primary and starts replicating again.
- https://cloud.google.com/sql/docs/mysql/replication#:~:text=If%20replication%20is,a%20new%20one
- https://cloud.google.com/sql/docs/mysql/replication#replication_use_cases

## Q51

## Q55

## Q60

## Q62

## Q65

## Q66

## Q68

## Q70

## Q72

## Q77

## Q78

## Q79

## Q80

## Q82

## Q84

## Q85

## Q87

## Q90

## Q92

## Q93

## Q94

## Q96

## Q101

## Q106

## Q107

## Q108

- D.
- A does not represent the minimum downtime. Read replicas in Cloud SQL depend upon a primary instance also in Cloud SQL. We’re talking about migrating to GCE, so B is wrong. The Database Migration Service migrates PostgreSQL to Cloud SQL or AlloyDB for PostgreSQL (Preview as of 3/16/23 which means it won’t be on the exam - yet). That makes C wrong. That leaves D. Pgbouncer is a connection pooler used to minimize application downtime.
- https://cloud.google.com/architecture/migrating-postgresql-to-gcp

## Q109

- The default app profile does not change when you add or remove clusters. You must manually update the default app profile to change its settings. However, as a best practice you should create and use a new app profile instead of changing the default app profile.
- https://cloud.google.com/bigtable/docs/app-profiles#how-they-work

## Q113

- The HA configuration provides data **redundancy**.
- [Failover overview] - If an HA-configured instance becomes unresponsive, Cloud SQL **automatically switches** to serving data from the standby instance.
- A Cloud SQL instance configured for HA is also called **a regional instance** and has a primary and secondary **zone** within the configured region. Within a regional instance, the configuration is made up of **a primary instance** and **a standby instance**.

- https://cloud.google.com/sql/docs/mysql/high-availability#failover
- https://cloud.google.com/sql/docs/mysql/high-availability#failover-overview

## Q121

- C.
- No need for restores if you have a read replica which you can promote to be the new primary. Eliminate A and B. Failovers do not happen automatically to read replicas. You have to promote them. Eliminate D. That leaves C which is supported by Google's documentation.
  https://cloud.google.com/sql/docs/postgres/replication/cross-region-replicas#disaster_recovery

**Disaster recovery**

> Cross-region replicas can be used as part of a disaster recovery procedure. You can promote a cross-region replica to fail over to another region should the primary's region become unavailable for an extended period of time.

## Q127

- D.
- Note, you cannot create a read replica in Cloud SQL for SQL Server unless you use an Enterprise Edition. Which is also a requirement for configuring SQL Server AG. That's not a coincidence. That's how Cloud SQL for SQL Server creates SQL Server read replicas. To find out about the replication, use the AG Dashboard in SSMS.
  https://cloud.google.com/sql/docs/sqlserver/replication/manage-replicas#promote-replica

**Promote a replica(SQL Server)**

> A read replica stops replication and converts the primary instance.

> When promoted, read replicas are automatically configured with backups, but they aren't automatically configured as high availability (HA) instances.
