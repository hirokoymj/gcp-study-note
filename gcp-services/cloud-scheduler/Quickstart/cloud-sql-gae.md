# Connect to Cloud SQL for MySQL from App Engine Standard

- [Connect to Cloud SQL for MySQL from App Engine Standard](#connect-to-cloud-sql-for-mysql-from-app-engine-standard)
  - [Document and Github](#document-and-github)
  - [Set up Cloud SQL](#set-up-cloud-sql)
  - [Configure the App Engine service account](#configure-the-app-engine-service-account)
  - [Configure and deploy a Cloud SQL sample app](#configure-and-deploy-a-cloud-sql-sample-app)

## Document and Github

- [Quickstart: Connect from App Engine standard](https://cloud.google.com/sql/docs/mysql/connect-instance-app-engine)
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

## Configure the App Engine service account

- List of my project's SA

```
gcloud iam service-accounts list

DISPLAY NAME: App Engine default service account
EMAIL: local-alignment-381806@appspot.gserviceaccount.com
DISABLED: False
```

- Add Cloud SQL Client roles to App Engine SA

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
--filter="bindings.members:local-alignment-381806@appspot.gserviceaccount.com"

ROLE: roles/cloudsql.client
ROLE: roles/editor
```

Links:

- https://stackoverflow.com/questions/47006062/how-do-i-list-the-roles-associated-with-a-gcp-service-account

## Configure and deploy a Cloud SQL sample app

1. Activate your project in Cloud Shell

```
gcloud config set project YOUR-PROJECT-ID
```

2. Update environment variables

- app.standard.yaml

```
runtime: nodejs16
env_variables:
  INSTANCE_UNIX_SOCKET: /cloudsql/local-alignment-381806:us-central1:quickstart-instance
  DB_USER: quickstart-user
  DB_PASS: root
  DB_NAME: quickstart_db
```

3. Deploy the sample app

```
gcloud app deploy app.standard.yaml

Services to deploy:

descriptor:                  [/home/hiroko/cloudshell_open/nodejs-docs-samples-5/cloud-sql/mysql/mysql/app.standard.yaml]
source:                      [/home/hiroko/cloudshell_open/nodejs-docs-samples-5/cloud-sql/mysql/mysql]
target project:              [local-alignment-381806]
target service:              [default]
target version:              [20230326t220403]
target url:                  [https://local-alignment-381806.uc.r.appspot.com]
target service account:      [App Engine default service account]


Do you want to continue (Y/n)?  y

Beginning deployment of service [default]...
Created .gcloudignore file. See `gcloud topic gcloudignore` for details.
82%
88%
94%
100%
100%
File upload done.
Updating service [default]...working..WARNING: *** Improve build performance by generating and committing package-lock.json.

Updating service [default]...done.
Setting traffic split for service [default]...done.
Deployed service [default] to [https://local-alignment-381806.uc.r.appspot.com]

You can stream logs from the command line by running:
  $ gcloud app logs tail -s default

To view your application in the web browser run:
  $ gcloud app browse
```
