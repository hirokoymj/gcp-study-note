# PLAN

| Month     | count | holidays  | Weekends | commute |
| --------- | ----- | --------- | -------- | ------- |
| March 18  | 0     | 3/21      | sundays  | tue/wed |
| April 18, | 1     |           | sundays  | tue/wed |
| May 18    | 2     | 5/3, 4, 5 | sundays  | tue/wed |
| June 18   | 3     |           |          |         |

# Cloud SQL

- [Connect to Cloud SQL for MySQL from Cloud Shell](./cloud-sql-cloud-shell.md)
- [Connect to a Cloud SQL for MySQL instance with private IP]()
- [Connect to Cloud SQL for MySQL using the Cloud SQL Auth proxy]()
- [Connect to Cloud SQL for MySQL from Cloud Run](./cloud-sql-run.md)
- [Connect to Cloud SQL for MySQL from Cloud Functions]()
- [Connect to Cloud SQL for MySQL from App Engine standard environment](./cloud-sql-gae.md)
- [Connect to Cloud SQL for MySQL from App Engine flexible environment]()
- [Connect to Cloud SQL for MySQL from your local computer]()
- [Connect to Cloud SQL for MySQL from Compute Engine]()

# App Engine Standard

## Building a Node.js app on App Engine

**Summary**

- [Tutorial](https://cloud.google.com/appengine/docs/standard/nodejs/)
- [Github Repo](https://github.com/GoogleCloudPlatform/nodejs-docs-samples/tree/3bb14ef7c23305613bbfe04f03d3b83f6a120e1a/appengine/building-an-app/build)
- Service: GAE standard with Node.js
- Date: 04/09/2023
- Result:
  - [HelloWorld](https://drive.google.com/file/d/1-MCD6Mj1tsdmzotkSM08aFcGDnEQrbhU/view?usp=share_link)
  - [GCP -> Services -> default](https://drive.google.com/file/d/1-NXiNJKREb5z2v2BKC4dw9L-6wr__8Kx/view?usp=share_link)

**how to clean up the project**

- App Engine -> Settings -> disable application
- Disable Cloud Build API

## Building an App - Updating your web service

**Summary**

- [Tutorial](https://cloud.google.com/appengine/docs/standard/nodejs/building-app/updating-web-service)
- [Github Repo](https://github.com/GoogleCloudPlatform/nodejs-docs-samples/tree/3bb14ef7c23305613bbfe04f03d3b83f6a120e1a/appengine/building-an-app/update)
- Service: GAE standard with Node.js
- Date: 04/09/2023
- Result:
  - [GCP -> Services -> myform](https://drive.google.com/file/d/1-NXiNJKREb5z2v2BKC4dw9L-6wr__8Kx/view?usp=share_link)

<hr />

# Compute Engine

https://cloud.google.com/compute/docs/instances/sql-server/setup-mysql#gcloud

# Cloud SDK

- [output of gcloud components list](https://drive.google.com/file/d/1-GQviZahBgyUzVwNAizeA_j84hcx765N/view?usp=share_link)

```
gcloud components list
gcloud components install COMPONENT
gcloud components update
```

- How to output gcloud list commands showing in table form.

```
gcloud config set accessibility/screen_reader false
```

**References:**

- [gcloud components](https://cloud.google.com/sdk/gcloud/reference/components)
- [stackoverflow](https://stackoverflow.com/questions/70674524/output-of-gcloud-list-commands-not-displaying-in-table-form)

<hr />

# Material

- [ExamTopic Professional Cloud Database](https://www.examtopics.com/exams/google/professional-cloud-database-engineer/view/)
- [Q1-Q123 in 30 pages](./questions.md)
- [QuickLab]()
- [youtube - Google Cloud Quick Tutorials](https://www.youtube.com/playlist?list=PLuJRcdtonlDAN73rZsRk_eiJ0NU9h1Cms)
- [Professional Cloud Database Engineer](https://cloud.google.com/certification/cloud-database-engineer)
- regular expression
  Question #[1-5]
  **Question #[1-5]:**

```
Question #(\d\d)
**Question #$1:**

Topic 1

^([A-D]).
- $1.
```
