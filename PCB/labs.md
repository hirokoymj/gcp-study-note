# Migrating On-premises MySQL Using a Continuous Database Migration Service Job

In this lab, you migrate an on-premises MySQL database (running on a virtual machine) to Cloud SQL for MySQL using a **continuous Database Migration Service job** and **VPC peering** for connectivity. After you create and run the migration job, you confirm that an initial copy of your database has been successfully migrated to your Cloud SQL for MySQL instance. Then, you explore how continuous migration jobs continue to apply data updates from your source database to your Cloud SQL instance until you choose to complete the job. To conclude the migration job, you promote the Cloud SQL instance to be **a new standalone database** for reading and writing data.

## Task 1. Get the connectivity information for the MySQL source instance

- Compute Engine > VM instances
- Internal IP (e.g., 10.128.0.2).

## Task 2. Create a new connection profile for the MySQL source instance

- A connection profile stores information about the source database instance (e.g., on-premises MySQL)
- Database Migration > Connection profiles.
- Source database engine, select MySQL.

## Task 3. Create and start a continuous migration job

- When you create a new migration job, you first define the source database instance using a previously created connection **profile**. Then you create **a new destination database instance** and configure **connectivity** between the source and destination instances.

## Task 4. Review the status of the continuous migration job

- Database Migration > Migration jobs.
- Review the migration job status.
- Running Full Dump
- Running CDC in progress -> proceed to the next task

## Task 5. Confirm the data in Cloud SQL for MySQL

- Databases > SQL.
- Replica Instance menu, click Databases.
- gcloud sql connect mysql-cloudsql --user=root --quiet

## Task 6. Test the continuous migration of data from the source to the destination instance

- Compute Engine > VM instances.
- There are now 5,032 records
- Databases > SQL
- select count(\*) from customers;
- There are now 5,032 records

## Task 7. Promote Cloud SQL to be a standalone instance for reading and writing data

- Database Migration > Migration jobs.
- Click Promote.
- Databases > SQL.
- mysql-cloudsql is now a standalone instance
