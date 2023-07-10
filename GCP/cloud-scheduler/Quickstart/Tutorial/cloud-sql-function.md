```
gcloud run deploy quickstart-function \
--image us-central1-docker.pkg.dev/local-alignment-381806/quickstart-repo/function-sql:latest \
--add-cloudsql-instances local-alignment-381806:us-central1:quickstart-instance \
--set-env-vars INSTANCE_UNIX_SOCKET="/cloudsql/local-alignment-381806:us-central1:quickstart-instance" \
--set-env-vars INSTANCE_CONNECTION_NAME="local-alignment-381806:us-central1:quickstart-instance" \
--set-env-vars DB_NAME="quickstart_db" \
--set-env-vars DB_USER="quickstart-user" \
--set-env-vars DB_PASS="root"

```
