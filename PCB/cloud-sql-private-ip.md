# Connect to Cloud SQL for MySQL from Cloud Run

https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-run

## Configure a Cloud SQL sample app

**Private IP**

For private IP paths, your application connects directly to your instance through Serverless VPC Access. This method uses a TCP socket to connect directly to the Cloud SQL instance without using the Cloud SQL Auth proxy.

```
gcloud run deploy run-sql --image gcr.io/local-alignment-381806/run-sql \
  --add-cloudsql-instances local-alignment-381806:us-central1:quickstart-instance \
  --vpc-connector="quickstart-connector" --vpc-egress=all-traffic \
  --set-env-vars DB_NAME="quickstart_db" \
  --set-env-vars DB_USER="quickstart-user" \
  --set-env-vars DB_PASS="root" \
  --set-env-vars INSTANCE_CONNECTION_NAME="local-alignment-381806:us-central1:quickstart-instance" \
  --set-env-vars DB_PORT="5432" \
  --set-env-vars INSTANCE_HOST="172.30.0.3" \
  --set-env-vars DB_ROOT_CERT="certs/server-ca.pem" \
  --set-env-vars DB_CERT="certs/client-cert.pem" \
  --set-env-vars DB_KEY="certs/client-key.pem" \
  --set-env-vars PRIVATE_IP="TRUE"
```
