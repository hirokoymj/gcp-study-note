# GCP Study App

# API

**IAP(Identity-Aware Proxy)**

- Identity Aware Proxy API(IAP)- https://cloud.google.com/iap/docs/external-identities
- Proxy(=dairi)
- external identities with Identity-Aware Proxy (IAP) instead of Google accounts.
- external identity: email/password, OAuth (Google, Facebook, Twitter, GitHub, Microsoft, etc.
- This is useful if your application is already using an external authentication system,
- your applications and VMs
- IAP controls access to App Engine apps and VMs
- https://cloud.google.com/architecture/identity/migrating-consumer-accounts

**Data Loss Prevention API**

- automatically detect a sensitive data and mask. Los Angeles[LOCATION], HIROKO[PERSON_NAME],

**Private Google Access**

- VM that only have internal IP addresses (no external IP addresses) can use Private Google Access.
- They can reach the external IP addresses of Google APIs and services.
- VM + internal IP
- No effect public IP
- Private Google Access -> Internal IP -> can access an external Google services
- subnet-a, Private Google Access ON, 10.240.0.2 ---> Can access
- subnet-a, Private Google Access ON, 10.240.0.3 + public IP ---> CAN access
- subnet-b, Private Google Access OFF, 192.168.1.2 ---> CANNOT access
- subnet-b, Private Google Access OFF, 192.168.1.3 + public IP ---> CAN access
- https://cloud.google.com/vpc/docs/private-google-access#example

**Cloud VPN**

- Virtual Private Network(VPN), Virtual Private Cloud(VPC)
- on-prem + VPC = Cloud VPN
- VPC: two subnets(us-east1, us-west1) => communicate internal IP with routing, Cloud gateway, on-prem gateway, two tunnels
- Cloud VPN = static or dynamic routes=> set up Cloud Router with BGP(border gateway protocol)
- Cloud VPN gateway with dynamic routing ---> HA VPN Border Gateway Protocol (BGP).
- The highest level of availability, use HA VPN whenever possible.

**Billing**

| Role                          | Description                                                                                                       |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Billing Account Creator       | create a new Cloud Billing Account                                                                                |
| Billing Account Creator       | Use Billing Account Creator's role for initial billing setup or to allow creation of additional billing accounts. |
| Project Billing Manager       | link/unlink the project to/from a billing.                                                                        |
| Project Billing Manager       | attach the project to the billing account, but does not grant any rights over resources.                          |
| Billing Account User          | Create new projects linked to the billing account                                                                 |
| Billing Account Administrator | Owner, can link/unlink, but cannot create billing accounts, create alert                                          |

- A billing account is assosicated with org.
- Billing alert - Avoid surprises on your bill, who -> Billing Account Administrator, Billing Account Costs Manager
- Moving projects under an organisation doesn't change their linked billing project.
- Billing data -> export BQ -> visualize = Data Studio
- https://cloud.google.com/billing/docs/how-to/billing-access
- https://cloud.google.com/billing/docs/how-to/budgets

**microservices**

- microservices, automation

**Machine Family**

- M1 machine type: "M" Memory-optimized - M, Compute-optimized - C, cost-optimized: E, Balanced price/performance: N
- Local SSD - When you stop a VM, all data on the local SSD is discarded.
- Unlike Persistent Disks, Local SSDs are physically attached to the server on VM.

**Cloud SQL**

- Backup(Data Protection) 1)automate backup is everyday setup only. 2) point-in-time(on-demand)
- Transactional and a single physical location = Cloud SQL.
- Region: us-central1, Single zone - in case of outage, no failover no recommended.
- Region: us-central1, dMultiple zones Automatic failover to another zone - recommended.

**Spanner**

- Spanner, CPU utilization, Cloud Monitoring, scaling
- Spanner is used for global scaling.

**Cross project**

- "Service accounts are both identities and resources. Because service accounts are identities, you can let a service account access resources in your project by granting it a role, just like you would for any other principal."

# VM

- SSH connection/VM: **enable-osLogin=true** with roles/compute.osLogin or roles/compute.osAdminLogin.
- https://medium.com/infrastructure-adventures/centralized-ssh-login-to-google-compute-engine-instances-d00f8654f379
- RDP: Windows login, reset password, download RDP client
- Network tags: it makes FW enable in a vm.
- batch job, preemptible vm
- Maintenance occurs - On host maintenance=Migrate VM instance, Automatic restart=ON
- Stop VM when increasing the memeory 4GB -> 8GB
- disk - persistant disc Local SSD
- MIGs - port 4443 HTTPS
- MIGs - autoscaling- CPU, max/min,
- Authentication - best practice
- each VM that needs to call a Google API should run as a service account with the minimum permissions necessary.(Create new SA)
- how to login using Cloud Identity Proxy for VM Access a paticular instance
- "without allowing other instances" , the other instances are created with default compute engine service account. So you must create a new independant service account

<hr />

# FW

- Request -> egress, Response -> ingress.
- egress is leaving

# Cloud Storage

- Storage Admin
- Bucket public -> a signed URL
- failover
- save sensitive data

# log

- Data access audit log - disable as a default

# SA

- Service accohttps://cloud.google.com/iap/docs/external-identitiesunt key: To use a service account from outside of Google Cloud, such as on other platforms or on-premises, you must first establish the identity of the service account

# VPC

- auto or custom mode
- auto mode - one subnet from each region is automatically created within it.
- custom mode: you have to create a subnet
- VPC and the 2 subnets -> custom

# BigQuery

- dry-run select \* from coffee.coffee_dataset -->304538 bytes of data
- External table (source: Cloud Storage)
- BigQuery jobUser - query

# App Engine

- You specify the scaling type in your app's app.yaml.
- app.yaml: runtime, URL, scaling
- gradually deploy - a rolling-action start-update with maxSurge
- --split
- version in a same project

# Deployment Manager

- gcloud deployment-manager deployments update my-deployment --config=new_config.yaml
- gcloud deployment-manager deployments update example-deployment \
   --config configuration-file.yaml \
   --preview ## Checking before deploy

# IAM

- Cloud Identity - verify thrid party authentication
- G Suite
- 'storage.objectCreator or 'storage.objectAdmin - carm down and check if admin role is wider permission.
- Storage Admin, Storage Object Admin, Storage Object Creator

# gcloud commands

- (Expand subnet) - gcloud compute networks subnets expand-ip-range SUBNET --region=us-central1 --prefix-length=16
- GKE| gcloud container node-pools create node-pool-1 --cluster=example-cluster --preemptible
- VM | gcloud compute instances create [INSTANCE_NAME] --deletion-protection
- gcloud | gcloud config configurations create my-config
- gcloud | gcloud config set compute/zone Z
- gcloud | gcloud projects get-iam-policy react-app-demo
- Cloud Function | gcloud functions deploy Hello --http-trigger (--trigger-topic=mytopic)
- gcloud iam roles copy --source="roles/spanner.databaseAdmin" --destination=CustomSpannerDbAdmin --dest-project=PROJECT_ID
- gcloud config list -> view project id
- gcloud iam roles describe roles/spanner.databaseUser.
- gcloud iam roles list
- gcloud iam service-accounts list

# GKE

- Deploy docker file| deokubectl create deployment hello-server --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
- https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster
- gcloud container clusters create-auto hello-cluster --region=us-central1
- kubectl create deployment hello-server --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
- kubectl config use-context black
- kubectl config view
- replicas
- A deployment is responsible for keeping a set of pods running. A service is responsible for enabling network access to a set of pods.
- A deployment is responsible for keeping a set of pods running.
- A service is responsible for enabling network access to a set of pods.
- A Deployment to define your app.
- A Service to define how to access your app.
- A Deployment: define an app, deployment.yaml, cluster resource,

  ```
  //Deploy the resource to the cluster:
  kubectl apply -f deployment.yaml
  kubectl get deployments
  kubectl get pods
  ```

- Service: access/NW, a set of pods, service.yaml,
- https://cloud.google.com/kubernetes-engine/docs/how-to/managing-clusters#default_cluster_kubectl

  ```
  gcloud config set container/cluster CLUSTER_NAME
  ```

- ClusterIP < NP < LB

**Links:**

1. https://matthewpalmer.net/kubernetes-app-developer/articles/service-kubernetes-example-tutorial.html#:~:text=What's%20the%20difference%20between%20a,running%20in%20the%20Kubernetes%20cluster.
2. https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster
3. https://cloud.google.com/kubernetes-engine/docs/quickstarts/deploy-app-container-image#node.js

# Stackdriver

- different projects, monitor a single report

# BigTable

- Cloud Bigtable, our scalable, low-latency time series database that’s reached 40 million

**LB**

- TCP, port 443, SSL offload -> SSL proxy LB

**GKE**

- https://cloud.google.com/kubernetes-engine/docs/how-to/managing-clusters
- gcloud container clusters describe CLUSTER_NAME
- gcloud container clusters list
- gcloud config set container/cluster CLUSTER_NAME

<hr />

**Other Topics**

[other-topics](./other-topics.md)
