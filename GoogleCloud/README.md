# Google Cloud Notes

- Update: 03/24/2024

## Cloud Function

- [Deploy a function(gcloud) ](https://cloud.google.com/functions/docs/create-deploy-gcloud)

```
gcloud functions deploy my-function \
--gen2 \
--runtime=nodejs20 \
--region=us-central1 \
--source=. \
--entry-point=helloGET \
--trigger-http
```

```
gcloud functions describe my-function --gen2 --region us-central1 --format="value(serviceConfig.uri)"
```

```
curl -m 70 -X POST URI \
    -H "Authorization: Bearer $(gcloud auth print-identity-token)" \
    -H "Content-Type: application/json" \
    -d '{}'
```

## Cloud Build

- [Google-created Cloud Storage bucket](https://cloud.google.com/build/docs/securing-builds/store-manage-build-logs)

## Cloud SQL

- [Connect to an instance using public IP](https://cloud.google.com/sql/docs/mysql/configure-ip#gcloud)

  ```
  gcloud sql instances patch INSTANCE_NAME\
  --assign-ip

  gcloud sql instances describe INSTANCE_NAME
  ```

- [Connect to an instance using private IP](https://cloud.google.com/sql/docs/mysql/configure-private-ip#gcloud)

  ```
  gcloud beta sql instances create INSTANCE_ID \
  --project=PROJECT_ID \
  --network=projects/NETWORK_PROJECT_ID/global/networks/VPC_NETWORK_NAME \
  --no-assign-ip \
  --allocated-ip-range-name=RANGE_NAME \
  --enable-google-private-path
  ```

## Test env

https://www.cloudskillsboost.google/
