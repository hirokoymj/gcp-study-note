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

**Question #56:**
You are troubleshooting a connection issue with a newly deployed Cloud SQL instance on Google Cloud. While investigating the Cloud SQL Proxy logs, you see the message Error 403: Access Not Configured. What should you do?

- A. Check the app.yaml value cloud_sql_instances for a misspelled or incorrect instance connection name.
- B. Check whether your service account has cloudsql.instances.connect permission.
- C. Enable the Cloud SQL Admin API.
- D. Ensure that you are using an external (public) IP address interface.
