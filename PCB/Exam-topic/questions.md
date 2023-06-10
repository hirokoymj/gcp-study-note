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
