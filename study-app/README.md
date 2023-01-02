# GCP Study App

# Cloud Storage

- Storage Admin
- Bucket public -> a signed URL

# SA

- Service account key: To use a service account from outside of Google Cloud, such as on other platforms or on-premises, you must first establish the identity of the service account

# VM

- SSH: osLogin=true with a IAM based permission ( No SA needed) roles/compute.osLogin or roles/compute.osAdminLogin.
- RDP: Windows login, reset password, download RDP client
- Network tags: it makes FW enable in a vm.
- batch job, preemptible vm
- Maintenance occurs - On host maintenance=Migrate VM instance, Automatic restart=ON
- Stop VM when increasing the memeory 4GB -> 8GB
- disk - persistant disc Local SSD
- MIGs - port 4443 HTTPS
- MIGs - autoscaling- CPU, max/min,

# VPC

- auto mode/custom mode
- auto mode - one subnet from each region is automatically created within it.
- custom mode: you have to create a subnet
- VPC and the 2 subnets - custom

# Cloud VPN

- on-promise and GCP
- GCP: private IPs
-

# BigQuery

- dry-run select \* from coffee.coffee_dataset -->304538 bytes of data
- External table (source: Cloud Storage)
- BigQuery jobUser - query

# gcloud commands

- Expand subnet|gcloud compute networks subnets expand-ip-range SUBNET --region=us-central1 --prefix-length=16
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

# App Engine

- You specify the scaling type in your app's app.yaml.
- app.yaml, runtime, URL, scaling
- gradually deploy - a rolling-action start-update with maxSurge
- --split
- version in a same project

# GKE

- Deploy docker file| deokubectl create deployment hello-server --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
- https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster
- gcloud container clusters create-auto hello-cluster --region=us-central1
- kubectl create deployment hello-server --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0

# Deployment Manager

- gcloud deployment-manager deployments update my-deployment --config=new_config.yaml
- gcloud deployment-manager deployments update example-deployment \
   --config configuration-file.yaml \
   --preview

# Billing

- Billing Account Admin: can link/unlink, but cannot create billing accounts.
- Project Billing Manager: can link/unlink
- A billing account is assosicated with org
- new billing account -> Project Billing Manager

# IAM

- Cloud Identity - verify thrid party authentication
- G Suite

<hr />

- **BigQ**

5, 8, 11, 18, 20, 36, 46, 73, 89, 114, 117, 112, 135, 137, 151, 186, 192, 198

**Billing**

7, 28, 56, 80, 87, 109, 120, 162, 177, 185

**LB**

10, 12, 25, 61, 75, 78, 81, 84, 99, 148, 168, 188

**MIGs**

10, 37, 64, 72, 78, 142, 168

preemptive VM
171

**Scale**

30, 37, 51, 64, 79

**Instance template**

10, 37, 68, 72, 78, 133, 142, 157, 158

**Health check**

25, 64, 68, 72, 64, 72, 153, 168

**Shared VPC**

53, 100, 103, 112, 154

**on-premises/Cloud NAT**

6, 84, 91, 110, 112, 143, 157, 163, 183, 199

**peering**

91, 112, 150, 170

**Network/LB**

188

**Subnet**

103

**Private Google Cloud**

163

**Cloud NAT**

183

**IAM**

3, 4, 21, 22, 31, 46, 47, 49, 55, 59, 104, 116, 134, 136, 139, 198

**Log**

89, 134, 109, 138

**SA**

40, 47, 52, 53, 57, 74, 85, 89, 91, 92, 95, 107, 115, 127, 137, 138, 151, 154, 155, 176, 186, 190, 192, 196, 198

**Cloud Storage**

9, 27, 38, 39, 47, 48, 50, 106, 111, 128, 167, 174, 176, 189, 191

**Other Topics**

[other-topics](./other-topics.md)
