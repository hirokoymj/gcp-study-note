# Read replica

- Cloud SQL is a regional service with read replicas allowed in other regions.
- HA replica === multiple zones(HA)
- you wouldn’t use a read replica as a source anyway for a migration.
- Native DB replication
- https://cloud.google.com/sql/docs/mysql/replication/external-server
- 20, 27, 28, 49, 68, 82, 96, 121
- a managed service (Cloud SQL)
- The question says backups and maintenance are an issue, so moving to a managed service (Cloud SQL) would be the right thing to do.
- https://cloud.google.com/sql/docs/mysql/replication/manage-replicas#promote-replica
- HA (ADD) -> HA(Enabled) -> For testing, go a primary and Failover
- Read replica --> promote
  ![](read-replica-promote.png)
- MySQL read replicas use asynchronous replication.
- zonal failure > enable HA to recover
- Multiple zone(HA)

# backups

- You cannot configure a custom location for automatic backups. A is wrong. The default option for automatic backups is multi-region. B is wrong.
- 101

# BT

- Key Visualizer

# Cloud SQL

- Cloud SQL could not scale to multiple regions.
- Cloud SQL is a regional service so cannot scale to multiple regions.

- Multi

# Cloud SQL for PostgreSQL

- open source, SQL-compliant database.
- Migration -> installing pglogical

# Query Insights

- Sqlcommenter

# Memorystore (Redis)

- sub-millisecond query latency

# Spanner

- Spanner exports are run as Dataflow jobs.
- Avoiding user disruption if a regional failure occures means multi-region service.

# serverless export

- Use serverless export. With serverless export, Cloud SQL creates a separate, temporary instance to offload the export operation.
  Offloading the export operation allows databases on the primary instance to continue to serve queries and perform operations at the usual performance rate. When the data export is complete, the temporary instance is deleted automatically. This might be a good option if you're taking a one-time export of a large database.

# Firestore/Spanner

- Not scale and latency required.

# gcloud command

- show backups status - gcloud sql operations list
