# Connect to Cloud SQL for MySQL from Cloud Run with a private IP

- [Quickstart:](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-run)

## SSL Enabled

- [Create a Cloud SQL instance - Private IP](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-run#expandable-2)
- Allocate an IP address range and create a private connection to configure private services access for Cloud SQL

  - [vpc-private-service-connection-1.png](https://drive.google.com/file/d/10cS6WRpSDFt1FvOSh0YDdxyGD17EEZW7/view?usp=share_link)
  - [vpc-private-service-connection-2.png](https://drive.google.com/file/d/10daY-ir2Q9BtbgIQQogj1lren_BvF_AX/view?usp=share_link)

- Run the gcloud sql instances patch command to enable only allow SSL connections for the instance.

  - [cloud-sql-connection.png](https://drive.google.com/file/d/10fur_Z4IKurCHN5qv-DmbAR2HCQctGvE/view?usp=share_link)

  ```
  gcloud sql instances patch quickstart-instance --require-ssl
  ```

- Final command

  ```
gcloud run deploy run-sql-0419 --image gcr.io/local-alignment-381806/run-sql \
  --add-cloudsql-instances local-alignment-381806:us-central1:quickstart-instance-default \
  --vpc-connector="quickstart-connector" --vpc-egress=all-traffic \
  --set-env-vars DB_NAME="quickstart_db" \
  --set-env-vars DB_USER="quickstart-user" \
  --set-env-vars DB_PASS="root" \
  --set-env-vars INSTANCE_CONNECTION_NAME="local-alignment-381806:us-central1:quickstart-instance-default" \
  --set-env-vars DB_PORT="3306" \
  --set-env-vars INSTANCE_HOST="10.8.0.3" \
  --set-env-vars DB_ROOT_CERT="certs/server-ca.pem" \
  --set-env-vars DB_CERT="certs/client-cert.pem" \
  --set-env-vars DB_KEY="certs/client-key.pem" \
  --set-env-vars PRIVATE_IP="TRUE"
  ```

## No SSL enabled

```
gcloud run deploy run-sql-no-ssl --image gcr.io/local-alignment-381806/run-sql \
 --add-cloudsql-instances local-alignment-381806:us-central1:quickstart-instance \
 --vpc-connector="quickstart-connector" --vpc-egress=all-traffic \
 --set-env-vars DB_NAME="quickstart_db" \
 --set-env-vars DB_USER="quickstart-user" \
 --set-env-vars DB_PASS="root" \
 --set-env-vars INSTANCE_CONNECTION_NAME="local-alignment-381806:us-central1:quickstart-instance" \
 --set-env-vars DB_PORT="3306" \
 --set-env-vars INSTANCE_HOST="10.145.0.3" \
 --set-env-vars PRIVATE_IP="TRUE"
```
