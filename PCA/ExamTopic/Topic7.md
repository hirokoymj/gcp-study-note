# Topic 7 - Mountkirk Games

**Question 1**

- B. Use gsutil to batch copy the files in parallel. 100%
- https://cloud.google.com/storage/docs/gsutil/commands/cp
- If you have a large number of files to transfer, you can perform a parallel multi-threaded/multi-processing copy using the top-level gsutil -m option (see gsutil help options):

```
gsutil -m cp -r dir gs://my-bucket
```

<hr />

**Question 2**

C. Create a service account (SA) in the legacy game's Google Cloud project, add this SA in the new game's IAM page, and then give it the Firebase Admin role in both projects. 100%

<hr />

**Question 3**

A. Configure an organizational policy which constrains where resources can be deployed. 88%

<hr />

**Question 4**

- D. Configure Ingress for Anthos with a global load balancer and Google Kubernetes Engine. 50%
- C. Configure a global load balancer with Google Kubernetes Engine. 25%/ME
- The reason for choosing C is that configuring a global load balancer with Google Kubernetes Engine (GKE) meets the business and technical requirements of Mountkirk Games. A global load balancer automatically routes players to the nearest regional game instances, reducing latency and providing high performance. Moreover, GKE allows dynamic scaling based on game activity and takes advantage of Google Cloud's managed services and resource pooling to minimize costs.
- A. Configuring a global load balancer connected to a managed instance group running Compute Engine instances does not fully utilize the dynamic scaling and managed services features of GKE.
- B. Configuring kubemci with a global load balancer and Google Kubernetes Engine is not recommended as kubemci is deprecated and no longer considered a best practice by Google.
- D. Configuring Ingress for Anthos with a global load balancer and Google Kubernetes Engine is more suitable for multi-cluster environments. In this scenario, deploying game instances in multiple regions is required, but a multi-cluster setup is not necessary. Therefore, option C is the best solution
- CGS22 8 months, 1 week ago

  - C is the most appropriate solution for Mountkirk Games as it involves configuring a global load balancer with GKE, which allows for dynamic scaling, minimizes latency, and optimizes costs. The use of a global load balancer ensures that players are routed to the closest regional game arena, which helps to minimize latency.

  - In addition, using GKE allows for rapid iteration of game features, as well as the eventual migration of legacy games to the new platform. The use of managed services and pooled resources also helps to minimize costs.

  - Option D is also not the best choice, as Anthos is not required for this scenario, as the game backend can be deployed directly on GKE.

<hr />

**Question 5**

- C. Create Request Latency and Error Rate as service level indicators. 95%

<hr />

**Question 6**

- A. Configure Workload Identity and service accounts to be used by the application platform.
- https://cloud.google.com/kubernetes-engine/docs/concepts/workload-identity
- **Workload Identity** is the recommended way for your workloads running on Google Kubernetes Engine (GKE) to access Google Cloud services in a secure and manageable way.
- https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity

<hr />

**Question 7**

- A. Upload your mobile app to the Firebase Test Lab, and test the mobile app on Android and iOS devices. 100%
