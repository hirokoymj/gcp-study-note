https://cloud.google.com/functions/docs/create-deploy-gcloud

gcloud functions deploy nodejs-http-function5 \
--gen2 \
--runtime=nodejs16 \
--region=us-central1 \
--source=. \
--entry-point=helloGET \
--trigger-http \
--service-account=read-bucket-objects@react-app-demo-363711.iam.gserviceaccount.com \
--allow-unauthenticated
