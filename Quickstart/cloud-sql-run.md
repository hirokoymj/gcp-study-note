# Connect to Cloud SQL for MySQL from Cloud Run

- [Connect to Cloud SQL for MySQL from Cloud Run](#connect-to-cloud-sql-for-mysql-from-cloud-run)
  - [Document and Github](#document-and-github)
  - [Set up Cloud SQL](#set-up-cloud-sql)
  - [Configure a Cloud Functions service account](#configure-a-cloud-functions-service-account)
  - [Create and Deploy a function](#create-and-deploy-a-function)
  - [Deploy the Cloud SQL sample app as a function](#deploy-the-cloud-sql-sample-app-as-a-function)

## Document and Github

- [Quickstart: Connect from Cloud Run](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-run#optional_cleanup_steps)
- [nodejs-docs-samples/cloud-sql/mysql/mysql/](https://github.com/GoogleCloudPlatform/nodejs-docs-samples/tree/main/cloud-sql/mysql/mysql)

## Set up Cloud SQL

- Create a Cloud SQL instance

```
 gcloud sql instances create quickstart-instance \
--database-version=MYSQL_8_0 \
--cpu=1 \
--memory=4GB \
--region=us-central1 \
--root-password=DB_ROOT_PASSWORD
```

- Create a database

```
gcloud sql databases create quickstart_db --instance=quickstart-instance
```

- Create a user

```
gcloud sql users create quickstart-user \
--instance=quickstart-instance \
--password=PASSWORD
```

## Configure a Cloud Functions service account

- List of my project's SA

```
gcloud iam service-accounts list
```

- Add Cloud SQL Client roles to Comute Engine SA

```
gcloud projects add-iam-policy-binding YOUR_PROJECT_ID \
  --member="serviceAccount:SERVICE_ACCOUNT_EMAIL" \
  --role="roles/cloudsql.client"
```

- How to list the the roles of a service account

```
gcloud projects get-iam-policy local-alignment-381806 \
--flatten="bindings[].members" \
--format='table(bindings.role)' \
--filter="bindings.members:433633104101-compute@developer.gserviceaccount.com"

ROLE: roles/cloudsql.client
ROLE: roles/editor
```

Links:

- https://stackoverflow.com/questions/47006062/how-do-i-list-the-roles-associated-with-a-gcp-service-account

## Create and Deploy a function

1. Go to the Cloud Functions page.
2. Environment: 2nd gen
3. Name: quickstart-function
4. Select Allow unauthenticated invocations
5. Click Next.
6. Runtime Node.js 16
7. Deploy --> Hello, World

## Deploy the Cloud SQL sample app as a function

**Configure a Cloud SQL sample app**

1. Activate your project in Cloud Shell

```
gcloud config set project YOUR-PROJECT-ID
```

2. Create a repository in the Artifact Registr

```
gcloud artifacts repositories create quickstart-repo \
  --project=YOUR_PROJECT_ID \
  --repository-format=docker \
  --location=us-central1 \
  --description="Cloud Function Quickstart Cloud SQL sample app"
```

3. Build a Docker container and publish it to Artifact Registry

```
gcloud builds submit \
  --tag us-central1-docker.pkg.dev/YOUR_PROJECT_ID/quickstart-repo/function-sql .
```

**Deploy the sample app**

```
gcloud run deploy quickstart-function \
--image us-central1-docker.pkg.dev/YOUR_PROJECT_ID/quickstart-repo/function-sql:latest \
--add-cloudsql-instances local-alignment-381806:us-central1:quickstart-instance \
--set-env-vars INSTANCE_UNIX_SOCKET="/cloudsql/local-alignment-381806:us-central1:quickstart-instance" \
--set-env-vars INSTANCE_CONNECTION_NAME="local-alignment-381806:us-central1:quickstart-instance" \
--set-env-vars DB_NAME="quickstart_db" \
--set-env-vars DB_USER="quickstart-user" \
--set-env-vars DB_PASS="root"
```

- Enter the numeric choice provided for **us-central**1 when prompted to specify a region.
