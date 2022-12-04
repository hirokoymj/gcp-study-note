# Quiz: Identity and Access Management

- 66%, 100%

Q: What abstraction is primarily used to administer user access in IAM ?

- Credentials, an abstraction of an authorization token.
- Privileges, an abstraction of access rights. X
- Leases, an abstraction of periodic entitlements.
- Roles, an abstraction of job roles.\*\*

> IAM administration uses pre-defined roles for administration of user access. The roles are defined by more granular permissions. But permissions are not applied to users directly, only through the roles that are assigned to them.

# Quiz: Storage and Database Services

Q: Which data storage service provides data warehouse services for storing data but also offers an interactive SQL interface for querying the data?

- Cloud SQL X
- BigQuery
- Dataproc
- Datalab

> BigQuery is a data warehousing service that allows the storage of huge data sets while making them immediately processable without having to extract or run the processing in a separate service.

# Quiz: Resource Management

- Your score: 33%

Q: How do quotas protect Google Cloud customers?

- By preventing resource use in too many zones in a region.
- By preventing resource use of too many different Google Cloud services.
- By preventing uncontrolled consumption of resources.\*\*
- By preventing resource use by unknown users.

> Quotas are established at reasonable defaults for common cloud usage and proof of concept activities. If you are planning to scale up a production cloud solution you may need to request that the quotas be raised. This is a reasonable checkpoint to verify that actions that might result in a large consumption of resources are reviewed.

<hr />

Q: No resources in Google Cloud can be used without being associated with...

- A user. X
- A bucket.X
- A project.\*\*
- A virtual machine.

> All resources in Google Cloud are tracked and their consumption is logged against a project. A project relates resources to a billing method.

# Quiz: Resource Monitoring

Q: What is the purpose of the Cloud Trace service?

- Reporting on application errors.
- Reporting on latency as part of managing performance.
- Reporting on Google Cloud resource consumption as part of managing performance.
- Reporting on Google Cloud system errors.

> Cloud Trace provides latency sampling and reporting for Google App Engine, Google HTTP(S) load balancers, and applications instrumented with the Cloud Trace SDKs. Reporting includes per-URL statistics and latency distributions.

> Before you can take any of the other actions, you must first be monitoring the system.
