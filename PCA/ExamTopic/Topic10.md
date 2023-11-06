# Topic 10 - TerramEarth

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**

- B. Make func_query 'Require authentication.' Create a unique service account and associate it to func_display. Grant the service account invoker role for func_query. Create an id token in func_display and include the token to the request when invoking func_query. Most Voted

- https://cloud.google.com/functions/docs/securing/authenticating

- B is correct. You need both service account (Authorization) and id token (Authentication)
  When building services that connect multiple functions, it's a good idea to ensure that each function can only send requests to a specific subset of your other functions. For instance, if you have a login function, it should be able to access the user profiles function, but it probably shouldn't be able to access the search function.
  To configure the receiving function to accept requests from a specific calling function, you need to grant the Cloud Functions Invoker (roles/cloudfunctions.invoker) role to the calling function's service account on the receiving function.

**Question 2**

- B. Deploy Cloud Run services to multiple regions. Create serverless network endpoint groups pointing to the services. Add the serverless NEGs to a backend service that is used by a global HTTP(S) Load Balancing in

- B is correct.
  > Cloud Run is a regional service.
  > To serve global users you need to configure a Global HTTP LB and NEG as the backend.
  > Cloud Run services are deployed into individual regions and to route your users to different regions of your service, you need to configure external HTTP(S) Load Balancing.

> https://cloud.google.com/run/docs/multiple-regions

> A network endpoint group (NEG) specifies a group of backend endpoints for a load balancer.
> A serverless NEG is a backend that points to a Cloud Run, App Engine, or Cloud Functions service. https://cloud.google.com/load-balancing/docs/negs/serverless-neg-concepts

**Question 3**

- C. Create a Cloud Monitoring uptime check to validate the application URL. If it fails, put a message in a Pub/Sub queue that triggers a Cloud Function to switch the URL to the "Site is unavailable" page, and notify the Ops team.

**Question 4**

- C. Create a Cloud Monitoring uptime check to validate the application URL. If it fails, put a message in a Pub/Sub queue that triggers a Cloud Function to switch the URL to the "Site is unavailable" page, and notify the Ops team. 100%

**Question 5**

- A. Configure a trigger in Cloud Build for new source changes. Invoke Cloud Build to build container images for each microservice, and tag them using the code commit hash. Push the images to the Container Registry. 100%

**Question 6**

- A. Request Transfer Appliances from Google Cloud, export the data to appliances, and return the appliances to Google Cloud. 83%

- It will take 123 days to transfer
  The right answer is to use Transfer Appliance
  https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets#time
