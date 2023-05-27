# AlloyDB - Database Fundamentals

## Task 1. Create a cluster and instance

- Databases -> AlloyDB for PostgreSQL
- Highly Available, Cluster ID, PW, NW-> Private IP

## Task 2. Create tables and insert data in your database

- Go to vm

  ```
  psql -h $ALLOYDB-privateIP -U postgres

  ```

## Task 3. Use the Google Cloud CLI with AlloyDB

- Create a cluster

```
gcloud beta alloydb clusters create gcloud-lab-cluster \
    --password=Change3Me \
    --network=peering-network \
    --region=Default Region \
    --project=Project ID
```

- Then, create an instance for the cluster

```
gcloud beta alloydb instances create gcloud-lab-instance\
    --instance-type=PRIMARY \
    --cpu-count=2 \
    --region=Default Region  \
    --cluster=gcloud-lab-cluster \
    --project=Project ID
```

![](lab1-alloydb1.png)

- List the AlloyDB clusters instances

```
gcloud beta alloydb clusters list

$ gcloud beta alloydb clusters list
NAME: projects/qwiklabs-gcp-00-aef8a1da1564/locations/us-central1/clusters/lab-cluster
NETWORK: projects/348161538065/global/networks/peering-network
STATUS: READY
```

## Task 4. Deleting a cluster

```
gcloud beta alloydb clusters delete gcloud-lab-cluster \
    --force \
    --region=Default Region \
    --project=Project ID
```

# Migrating to AlloyDB from PostgreSQL Using Database Migration Service

- **Migration job name**: vm-to-cloudsql
- **Source database engine**: PostgreSQL
- **Destination database engine**: Cloud SQL for PostgreSQL
- **Type**: Continuous
- **Connection profile name**: postgres-vm
- **Hostname:Port**: 10.128.0.2:5432
- **data dump options**: Auto-generated dump
- **Destination instance ID**: postgresql-cloudsql
- **Region**: us-central1
- **Connectivity method**: VPN peering

# AlloyDB - Database Fundamentals

## Task 1. Create a cluster and instance

## Task 2. Create tables and insert data in your database

## Task 3. Use the Google Cloud CLI with AlloyDB

```
gcloud beta alloydb clusters create gcloud-lab-cluster \
    --password=Change3Me \
    --network=peering-network \
    --region=Default Region \
    --project=Project ID
```

## Task 4. Deleting a cluster

```
gcloud beta alloydb clusters delete gcloud-lab-cluster \
    --force \
    --region=Default Region \
    --project=Project ID

gcloud beta alloydb clusters list
```

# Migrating to AlloyDB from PostgreSQL Using Database Migration Service

1. Define a source - postgres-vm
2. Create a destination - postgresql-cloudsql created
3. Define connectivity method - VPC peering
4. Test and create migratio job

- **Migration job name**: vm-to-cloudsql
- **Source database engine**: PostgreSQL
- **Destination database engine**: Cloud SQL for PostgreSQL
- **Type**: Continuous
- **Connection profile name**: postgres-vm
- **Hostname:Port**: 10.128.0.2:5432
- **data dump options**: Auto-generated dump
- **Destination instance ID**: postgresql-cloudsql
- **Region**: us-central1
- **Connectivity method**: VPN peering

# Migrating to AlloyDB from PostgreSQL Using PostgreSQL Tools

## Task 1. Verify Data in Source Instance for Migration

```
sudo -u postgres psql
\dt
```

## Task 2. Create a database DMP file using pg_dump

- The pg_dump tool is installed by default with every PostgreSQL installation.
-

```
sudo -u postgres pg_dump -Fc postgres > pg14_source.DMP
ls -l -h pg14_source.DMP
gsutil cp pg14_source.DMP gs://Project ID/pg14_source.DMP
```

## Task 3. Import DMP file using pg_restore

- AlloyDB -> lab-cluster -> lab-instance -> Private IP

# Administering an AlloyDB Database

## Task 1. Examine a Database Flag

- lab-cluster, lab-instance, Private IP
- Enable pgaudit -> Add flag

## Task 2. Setup a Database Extension

- enable the pgaudit feature for your AlloyDB cluster
- Go to vm
  ```
   psql -h $ALLOYDB -U postgres
   CREATE EXTENSION IF NOT EXISTS PGAUDIT;
   select extname, extversion from pg_extension where extname = 'pgaudit';
    extname | extversion
    ---------+------------
    pgaudit | 1.6.1
  ```

## Task 3. Create a Read Pool Instance for an Existing Cluster

- A read pool instance increases your cluster’s read capacity by aggregating nodes, which you can scale, enabling highly available reads.
- gcloud beta alloydb backups list
- Recovery of a backup is very simple. Click the Restore

## Task 4. Setup Backups

- Automatic backups are configured by default when every AlloyDB cluster is created.
- You can however create backups as needed, on-demand for additional recovery options.

## Task 5. Examine Monitoring in the AlloyDB Console

- Top Queries and Tags

# Create and Manage AlloyDB Databases - Challenge Lab

## Task 1. Create a cluster and instance

```
gcloud beta alloydb clusters create lab-cluster \
    --password=Change3Me \
    --network=peering-network \
    --region=us-central1 \
    --project=qwiklabs-gcp-02-fc0205cb654b
```

```
gcloud beta alloydb instances create lab-instance \
    --instance-type=PRIMARY \
    --cpu-count=2 \
    --region=us-central1  \
    --cluster=lab-cluster  \
    --project=qwiklabs-gcp-02-fc0205cb654b
```

## Task 2. Create tables in your instance

172.27.0.2

psql -h 172.27.0.2B -U postgres

- Table: regions

```
CREATE TABLE regions (
    region_id bigint NOT NULL,
    region_name varchar(25)
) ;
ALTER TABLE regions ADD PRIMARY KEY (region_id);
```

- Table: countries

```
CREATE TABLE countries (
    country_id char(2) NOT NULL,
    country_name varchar(40),
    region_id bigint
) ;
ALTER TABLE countries ADD PRIMARY KEY (country_id);
```

- Table: departments

```
CREATE TABLE departments (
    department_id smallint NOT NULL,
    department_name varchar(30),
    manager_id integer,
    location_id smallint
) ;
ALTER TABLE departments ADD PRIMARY KEY (department_id);
```

## Task 3. Load simple datasets into tables

- Table: regions

```
INSERT INTO regions VALUES (1, 'Europe');
INSERT INTO regions VALUES (2, 'Americas');
INSERT INTO regions VALUES (3, 'Asia');
INSERT INTO regions VALUES (4, 'Middle East and Africa');
```

- Table: countries

```
INSERT INTO countries VALUES ('IT', 'Italy', 1);
INSERT INTO countries VALUES ('JP', 'Japan', 3);
INSERT INTO countries VALUES ('US', 'United States of America', 2);
INSERT INTO countries VALUES ('CA', 'Canada', 2);
INSERT INTO countries VALUES ('CN', 'China', 3);
INSERT INTO countries VALUES ('IN', 'India', 3);
INSERT INTO countries VALUES ('AU', 'Australia', 3);
INSERT INTO countries VALUES ('ZW', 'Zimbabwe', 4);
INSERT INTO countries VALUES ('SG', 'Singapore', 3);
```

- Table: departments

```
INSERT INTO departments VALUES(10, 'Administration', 200, 1700);
INSERT INTO departments VALUES(20, 'Marketing', 201, 1800);
INSERT INTO departments VALUES(30, 'Purchasing', 114, 1700);
INSERT INTO departments VALUES(40, 'Human Resources', 203, 2400);
INSERT INTO departments VALUES(50, 'Shipping', 121, 1500);
INSERT INTO departments VALUES(60, 'IT', 103, 1400);
```

## Task 4. Create a Read Pool instance

```
gcloud beta alloydb instances create lab-instance-rp1 \
--instance-type=READ_POOL \
--cpu-count=2 \
--read-pool-node-count=2 \
--region=us-central1  \
--cluster=lab-cluster  \
--project=qwiklabs-gcp-02-fc0205cb654b
```

## Task 5. Create a backup

```
gcloud beta alloydb backups create lab-backup \
--cluster=lab-cluster \
--region=us-central1 \
--project=qwiklabs-gcp-02-fc0205cb654b




```
