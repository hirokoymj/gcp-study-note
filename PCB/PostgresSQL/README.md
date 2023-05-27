# Migrate to Cloud SQL for PostgreSQL using Database Migration Service

## Objectives

- Prepare the source database for migration.

- Create a profile for a source connection to a PostgreSQL instance (e.g., stand-alone PostgreSQL).

- Configure connectivity between the source and destination database instances using VPC peering.

- Configure firewall and database access rules to allow access to the source database for migration.

- Create, run, and verify a continuous migration job using Database Migration Service.

- Promote the destination instance (Cloud SQL for PostgreSQL) to be a stand-alone database for reading and writing data.

# Lab3: Migrate to Cloud SQL for PostgreSQL using Database Migration Service

## Objective

- Prepare the source database for migration.
- Create a profile for a source connection to a PostgreSQL instance (e.g., stand-alone PostgreSQL).
- Configure connectivity between the source and destination database instances using VPC peering.
- Configure firewall and database access rules to allow access to the source database for migration.
- Create, run, and verify a continuous migration job using Database Migration Service.
- Promote the destination instance (Cloud SQL for PostgreSQL) to be a stand-alone database for reading and writing data.

## Task 1. Prepare the source database for migration

- Installing and configuring the pglogical database extension.

  ```
  sudo apt update
  sudo apt install postgresql-13-pglogical
  sudo nano /etc/postgresql/13/main/postgresql.conf
  # Alt + /
  # Add settings for extensions here
  ```

wal*level = logical # minimal, replica, or logical
max_worker_processes = 10 # one per database needed on provider node # one per node needed on subscriber node
max_replication_slots = 10 # one per node needed on provider node
max_wal_senders = 10 # one per node needed on provider node
shared_preload_libraries = 'pglogical'
max_wal_size = 1GB
min_wal_size = 80MB
listen_addresses = '*' # what IP address(es) to listen on, '\_' is all

sudo nano /etc/postgresql/13/main/pg_hba.conf
host all all 0.0.0.0/0 md5
sudo systemctl restart postgresql@13-main
sudo su - postgres
psql
\c postgres;
CREATE EXTENSION pglogical;
\c orders;
CREATE EXTENSION pglogical;
\l

```

- Creating a migration_admin user (with Replication permissions) for database migration and granting the required permissions to schemata and relations to that user.

```

psql
CREATE USER migration_admin PASSWORD 'DMS_1s_cool!';
ALTER DATABASE orders OWNER TO migration_admin;
ALTER ROLE migration_admin WITH REPLICATION;

```

```

\c postgres;
GRANT USAGE ON SCHEMA pglogical TO migration_admin;
GRANT ALL ON SCHEMA pglogical TO migration_admin;
GRANT SELECT ON pglogical.tables TO migration_admin;
GRANT SELECT ON pglogical.depend TO migration_admin;
GRANT SELECT ON pglogical.local_node TO migration_admin;
GRANT SELECT ON pglogical.local_sync_status TO migration_admin;
GRANT SELECT ON pglogical.node TO migration_admin;
GRANT SELECT ON pglogical.node_interface TO migration_admin;
GRANT SELECT ON pglogical.queue TO migration_admin;
GRANT SELECT ON pglogical.replication_set TO migration_admin;
GRANT SELECT ON pglogical.replication_set_seq TO migration_admin;
GRANT SELECT ON pglogical.replication_set_table TO migration_admin;
GRANT SELECT ON pglogical.sequence_state TO migration_admin;
GRANT SELECT ON pglogical.subscription TO migration_admin;

```

```

\c orders;
GRANT USAGE ON SCHEMA pglogical TO migration_admin;
GRANT ALL ON SCHEMA pglogical TO migration_admin;
GRANT SELECT ON pglogical.tables TO migration_admin;
GRANT SELECT ON pglogical.depend TO migration_admin;
GRANT SELECT ON pglogical.local_node TO migration_admin;
GRANT SELECT ON pglogical.local_sync_status TO migration_admin;
GRANT SELECT ON pglogical.node TO migration_admin;
GRANT SELECT ON pglogical.node_interface TO migration_admin;
GRANT SELECT ON pglogical.queue TO migration_admin;
GRANT SELECT ON pglogical.replication_set TO migration_admin;
GRANT SELECT ON pglogical.replication_set_seq TO migration_admin;
GRANT SELECT ON pglogical.replication_set_table TO migration_admin;
GRANT SELECT ON pglogical.sequence_state TO migration_admin;
GRANT SELECT ON pglogical.subscription TO migration_admin;
GRANT USAGE ON SCHEMA public TO migration_admin;
GRANT ALL ON SCHEMA public TO migration_admin;
GRANT SELECT ON public.distribution_centers TO migration_admin;
GRANT SELECT ON public.inventory_items TO migration_admin;
GRANT SELECT ON public.order_items TO migration_admin;
GRANT SELECT ON public.products TO migration_admin;
GRANT SELECT ON public.users TO migration_admin;

```

```

\c orders;
\dt
ALTER TABLE public.distribution_centers OWNER TO migration_admin;
ALTER TABLE public.inventory_items OWNER TO migration_admin;
ALTER TABLE public.order_items OWNER TO migration_admin;
ALTER TABLE public.products OWNER TO migration_admin;
ALTER TABLE public.users OWNER TO migration_admin;
\dt

```

ALTER TABLE inventory_items ADD CONSTRAINT inventory_items_pkey PRIMARY KEY (id);

# psql commands

- https://hasura.io/blog/top-psql-commands-and-flags-you-need-to-know-postgresql/
- https://www.geeksforgeeks.org/postgresql-psql-commands/

| Description                | command                            |
| -------------------------- | ---------------------------------- |
| Connect to a database      | psql -d <db-name> -U <username> -W |
| List all databases         | \l                                 |
| Switch to another database | \c <db-name>                       |
| List database tables       | \dt                                |
| Describe a table           | \d <table-name>                    |
| Quit psql                  | \q                                 |
|                            |                                    |
```
