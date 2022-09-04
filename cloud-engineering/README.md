## Quiz - Setting up a cloud solution environment

**Q1**

Which of the following can be categorized as Identity as a service (IDaaS) offering from Google Cloud Platform?

1. Identity Aware Proxy
2. Cloud identity
3. Federated users

```text
1. Manages access to applications running on Google App Engine, GKE and Compute Engine.
2. Cloud identity allows you to manage users, devices and applications in Google Cloud Platform.
3. User federation is the process of authenticating users from one domain to applications in another domain.
```

**Q2**

An enterprise has migrated their workload to GCP. The applications are organized under different projects. Enterprise wants to manage the monitoring information in a centralized environment. Choose the best solution.

1. Use Stackdriver monitoring solution. Copy the metric data to a cloud storage bucket. Use Google Data Studio for analysis and visualization.
2. Add projects to single Stackdriver workspace (a)
3. Use third party monitoring solution and store the data in centralized cloud storage bucket. Use BigQuery to handle queries and Google DataStudio for visualization.

```text
1. Although this seems to be relevant solution, it is not the best solution
2. You can add multiple projects to single workspace and extract all the metric data
3. Use of third-party solutions is not the best solution as Stackdriver provides simple solution to address the given requirement
```

## Quiz- Planning and configuring a cloud solution

**Q1**

A developer has written a Python application and wants to deploy the application in a managed environment which can scale within seconds to cater huge traffic spikes hitting the application. Which of the following is most appropriate service to host the application?

1. Compute Engine
2. Kubernetes Engine
3. App Engine Standard Environment (a)
4. App Engine Flexible Environment

```text
1. Compute Engine would provide you a machine and developer will have to manage the environment
2. Kubernetes Engine is a good choice to host containerized applications
3. App Engine Standard Environment can handle huge traffic spikes and offer immediate scaling
4. App Engine flexible environment is preferred for applications with consistent traffi
```

**Q2**

You have been consulted to improve the performance of a real-time, weather-reporting application.
This application reads data from 20,000 sensors, at a rate of 10 reads per second which includes a timestamp and sensor reading.
Which of the following is most appropriate service to store this data?

1. Google Cloud Storage
2. Google Cloud Bigtable (a)
3. Google Bigquery
4. Google Cloud SQL

```text
1. Google Cloud Storage is not appropriate for large amount of data streaming ingestion rate in real-time
2. Google Cloud Bigtable is suitable for real-time access and analytics workloads.
3. Google Bigquery though is useful for analytics, but cannot handle high ingesting rate in real time
4. Google Cloud SQL is not capable to handle high ingesting rate in real time
```

**Q3**

You have been asked to rewrite an application using a microservice architecture approach, which they are planning to run on Docker containers. Most importantly, the application work on Cloud and can also be deployed internally in private Cloud.Which of the following service is most appropriate and quick to use?

1. Deploy the application on Compute Engine VM instances and export the VM to run on a private cloud.
2. Use Kubernetes and GKE
3. Deploy the application on App Engine Flexible environment and write scripts to copy the application to private cloud
4. Run each service as a Google Cloud Function

```text
1. Deploying application on Compute Engine VM is where you will have to configure the instance, platform, scale the instances and manage the containers on host by your own
2. Kubernetes offer a container-orchestration system for deploying applications with automatic scaling and management.
3. App Engine is preferred to run web applications
4. Cloud Function is an event-driven compute platform to run functions that respond to Cloud events
```

## Quiz-Deploying and implementing a cloud solution

**Q1**

An enterprise has recently deployed their workload to Google Cloud Platform. They have not enabled public access to their webservers according to the security guidelines of the enterprise. However, they discovered that the packages in the instances need to be updated from internet. How to fix the issue?

1. Enable Google Private Access to the VPC and subnet.
2. Enable Cloud VPN for the instances. Connect from on-premise bastion host and update the software packages.
3. Enable Cloud NAT. Software packages can now be installed.
4. Explanation:

```text
1. Private google access does not allow internet access
2. Looks like relevant solution. However, it is a tedious process.
3. Cloud NAT allows you to download updates from internet without enabling public access to the instances.
```

**Q2**

An E-commerce enterprise wants to perform click stream data analytics and derive insights in near real time. Also, they wish to store the data to perform querying. Which of the following solutions is the best solution?

1. Cloud Dataflow for ingestion and processing of streaming data, Cloud BigQuery for long term querying and local persistent disks for storing the data.
2. Cloud Pub/Sub for data ingestion, Cloud Dataflow for stream data processing, BigQuery for long term querying and Cloud storage for long term data retention
3. Cloud Pub/Sub for data ingestion, Cloud BigTable for processing the data and Cloud storage archive storage class for long term storage
4. Cloud Pub/Sub for data ingestion, Cloud BigTable for processing the data and Cloud BigQuery for querying and data retention for long tenure.

```text
1. Dataflow is not used for data ingestion. Also, persistent disks is not a good choice for long term data retention
2. Pub/Sub, Dataflow, Cloud Storage and BigQuery form a pipeline that addresses the requirements
3. BigTable is not for streaming data analysis. Querying requirement is not addressed here
4. BigTable is not a right choice for this use case.
```

# Successful operation of Cloud solution

## Storage classes

https://cloud.google.com/storage/docs/storage-classes

| Storage Class    | Name     | min storage duration |
| ---------------- | -------- | -------------------- |
| Standard storage | STANDARD | None                 |
| Nearline storage | NEARLINE | 30 days              |
| Coldline storage | COLDLINE | 90 days              |
| Archive storage  | ARCHIVE  | 365 days             |

- **Standard storage** is best for data that is **frequently** accessed ("**hot**" data) and/or stored for only brief periods of time.
- **Nearline storage** is a low-cost, highly durable storage service for storing infrequently accessed data.
- **Coldline storage** is a very-low-cost, highly durable storage service for storing infrequently accessed data, a 90-day minimum storage duration
- **Archive storage** is the lowest-cost, highly durable storage service for data archiving, online backup, and disaster recovery.

![](./images/storage-classes-1.png)
![](./images/storage-classes-2.png)
![](./images/storage-classes-3.png)
![](./images/storage-classes-4.png)
![](./images/storage-classes-5.png)
![](./images/storage-classes-6.png)

## Handling service accounts

https://cloud.google.com/storage/docs/gsutil/commands/defacl

![](images/service-account0.PNG)
![](images/service-account1.PNG)
![](images/service-account2.PNG)

## VM Inventory - describe a virtual machine instance

https://cloud.google.com/sdk/gcloud/reference/compute/instances/describe

**Describe a virtual machine instance**

```js
gcloud compute instances describe [instance-name]
gcloud compute instances describe test-instance
```

## GPU (graphics processing units) platforms

https://cloud.google.com/compute/docs/gpus

- you can add to your virtual machine (VM) instances.
- If you have graphics-intensive workloads, such as 3D visualization, 3D rendering, or virtual applications, you can use NVIDIA RTX virtual workstations (formerly known as NVIDIA GRID).

![](./images/gpu.PNG)

## BigQuery : Cost controls

Project level, user level

Menu -> IAM Admin -> Quatas Quata(割り当て)

## Quiz : Successful operations on GCP

![](./images/vm-desc1.PNG)
![](./images/vm-desc2.PNG)
![](./images/vm-desc3.PNG)
![](./images/vm-desc4.PNG)

**Q1**

You are analyzing Google Cloud Platform service costs from three separate projects. You want to use this information to create service cost estimates by service type, daily and monthly, for the next six months using standard query syntax. What should you do?

1. Export your bill to a Cloud Storage bucket, and then import into Cloud Bigtable for analysis.
2. Export your bill to a Cloud Storage bucket, and then import into Google Sheets for analysis.
3. Export your transactions to a local file, and perform analysis with a desktop tool.
4. Export your bill to a BigQuery dataset, and then write time window-based SQL queries for analysis. (a)

```text

```

**Q2 of 3**

Your company has reserved a monthly budget for your project. You want to be informed automatically of your project spend so that you can take action when you approach the limit. What should you do?

1. Link a credit card with a monthly limit equal to your budget.
2. Create a budget alert for 50%, 90%, and 100% of your total monthly budget. (a)
3. In App Engine Settings, set a daily budget at the rate of 1/30 of your monthly budget.
4. In the GCP Console, configure billing export to BigQuery. Create a saved view that queries your total spend.

```text

```

**Q3 of 3**

Software engineers are using Google Cloud for development and testing. They have noticed that the instances they use to run tests shutdown without anyone explicitly shutting them down. None of the instances seem to run longer than 24 hours. What would be the first thing to check about the test instance configuration?

1. The instances are running as Shielded VMs
2. The instances are running as preemptible instances or not (a)
3. The instance group has a maximum number of instances that is too large
4. The instance group has a minimum number of instances that is too small

```text
Premptible instances cannot live more than 24 hours
```

## GKE

- Google Kubernetes Engine (GKE) for your containerized applications.
- GKE clusters are powered by the Kubernetes open source cluster management system.
- **Autopilot**: GKE provisions and manages the cluster's underlying infrastructure, including nodes and node pools, giving you an optimized cluster with a hands-off experience.
- **Standard**: You manage the cluster's underlying infrastructure, giving you node configuration flexibility
- Kubernetes Cluster Architecture - **Master/Node/Pods**
- GKE Cluster Types - **1. Zonal, 2. Regional, 3. Private, 4. Alpha**
- A single zone cluster

  ```text
  - Running Small App
  - Prototyping
  - Testing
  ```

![](./images/kuber1.PNG)
![](./images/kuber2.PNG)
![](./images/kuber3.PNG)
![](./images/kuber4.PNG)
![](./images/kuber5.PNG)
![](./images/kuber6.PNG)
![](./images/kuber7.PNG)
![](./images/kuber8.PNG)

## How to create GKE Cluster

1. Menu -> Kubernetes Engine -> Clusters
2. Create Cluster
3. Cluster basics - Name, Zonal/Regional, Zone
4. Master version - leave as default
5. On left site, click on Node Pools -> default-pool
6. Node pool details - Name, Size 3
7. On left side, click on Nodes
8. Nodes - Image type, Machine config.
9. Create -> Create cluster creation
10. Connect -> Run in Cloud Shell

```js
gcloud container clusters get-credentials <cluster-name> --zone <cluster-zone> --project <gcp-project-id>

gcloud container clusters get-credentials demo-gke-cluseter --zone us-central-c --project brio-eta-training

```

> we will be successfully connected to the cluster and kubectl commands can be executed to interact with the
> cluster.

11. View the worker nodes in the cluster

```text
kubectl get nodes
```

**Create a cluster - basic and Master version**
![](./images/cluster2.PNG)
![](./images/cluster3.PNG)

Nodes - Boot disk, Machine type
![](./images/cluster1.PNG)
![](./images/cluster4.PNG)
![](./images/cluster5.PNG)
![](./images/cluster6.PNG)
![](./images/cluster7.PNG)
![](./images/cluster8.PNG)

## Viewing Pods and Nodes

- https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/

```js
kubectl get - list resources
kubectl describe - show detailed information about a resource
kubectl logs - print the logs from a container in a pod
kubectl exec - execute a command on a container in a pod
```

## Kubernetes Pods

When you created a Deployment in Module 2, Kubernetes created a Pod to host your application instance. A Pod is a Kubernetes abstraction that represents a group of one or more application containers (such as Docker), and some shared resources for those containers. Those resources include:

- Shared storage, as Volumes
- Networking, as a unique cluster IP address
- Information about how to run each container, such as the container image version or specific ports to use
- you generally create a set of identical Pods, called **replicas**, to run your application.
- Pods run on nodes in your **cluster**.

![](./images/pods-overview.png)

## Nodes

A Pod always runs on a Node. A Node is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster. Each Node is managed by the control plane. A Node can have multiple pods,

![](./images/node-overview.png)

## Pod lifecycle

- **Pending**: Pod has been created and accepted by the cluster, but one or more of its containers are not yet running. This phase includes time spent being scheduled on a node and downloading images.
- **Running**: Pod has been bound to a node, and all of the containers have been created. At least one container is running, is in the process of starting, or is restarting.
- **Succeeded**: All containers in the Pod have terminated successfully. Terminated Pods do not restart.
- **Failed**: All containers in the Pod have terminated, and at least one container has terminated in failure. A container "fails" if it exits with a non-zero status.
  Unknown: The state of the Pod cannot be determined

## Creating Pods

**Step 1** – Open cloud shell and set the project and compute zone

```js
gcloud config set project <project-id>
gcloud config set compute/zone asia-south1
```

**Step 2** – Create a cluster named hello-app-cluster with a single node using the command

```js
gcloud container clusters create hello-app-cluster --num-nodes 1
```

**Step 3** – Create pod configuration file **config.yaml** with the below contents

**Step 4** - Create the deployment using the command

```js
kubectl apply -f config.yaml
```

**Step 5** – To view the pods that are created, we use the command

```js
kubectl get pods
```

**Step 6** - To get the details of our deployment, use the command

```js
Kubectl describe deployment pod-demo
```

**Step 7** - To scale the deployment pods , we use the command

```js
kubectl scale deployment pod-demo --replicas 3
```

**Step 8** – Verify the increase in number of pods using

```js
kubectl get pods
```

Till now you have seen how to create pods using deployment and then to scale a deployment. Now
let’s see how to delete the deployment

**Step 9** - To delete the deployment we use the command

```js
Kubectl delete deployment pod-demo
```

**Step 10** – Verify the deletion of deployment using the command

```js
Kubectl get pod
```

![](./images/pad1.PNG)
![](./images/pad2.PNG)
![](./images/pad3.PNG)
![](./images/pad4.PNG)

## Creating a ConfigMap

- https://cloud.google.com/kubernetes-engine/docs/concepts/configmap
- https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/

```js
kubectl create configmap <map-name> <data-source>
```

**Example**

```js
# Create the local directory
mkdir -p configure-pod-container/configmap/

# Download the sample files into `configure-pod-container/configmap/` directory
wget https://kubernetes.io/examples/configmap/game.properties -O configure-pod-container/configmap/game.properties
wget https://kubernetes.io/examples/configmap/ui.properties -O configure-pod-container/configmap/ui.properties

# Create the configmap
kubectl create configmap game-config --from-file=configure-pod-container/configmap/
```

**Display details of the ConfigMap:**

```js
kubectl describe configmaps game-config
```

**Output**

```js
Name:         game-config
Namespace:    default
Labels:       <none>
Annotations:  <none>

Data
====
game.properties:
----
enemies=aliens
lives=3
enemies.cheat=true
enemies.cheat.level=noGoodRotten
secret.code.passphrase=UUDDLRLRBABAS
secret.code.allowed=true
secret.code.lives=30
ui.properties:
----
color.good=purple
color.bad=yellow
allow.textmode=true
how.nice.to.look=fairlyNice
```

## GKE Services

- ClusterIP
- NodePort Service
- LoadBalancer

**ClusterIp exposure < NodePort exposure < LoadBalancer exposure**

- ClusterIp
  Expose service through k8s cluster with ip/name:port

- NodePort
  Expose service through Internal network VM's also external to k8s ip/name:port

- LoadBalancer
  Expose service through External world or whatever you defined in your LB.

![](./images/GKE-services.jpg)

## Quiz : Managing GKE resources

**Q1 of 3**

You are recently introduced to gcloud commands and you are supposed to create a kubernetes cluster. Identify the right initial part of command to create clusters in GKE.

1. gcloud kubernetes
2. gcloud containers (a)
3. gsutil kubernetes
4. kubectl containers

```js
1. Kubernetes is not to be used with gcloud directly like this.
2. This is the right way as gcloud has to be used for creating clusters
3. gsutil is for cloud storage not for kubernetes
4. kubectl is to be used after the containers are created
```

**Q2 of 3**

A developer on your team has deployed an App Engine application that should be running in a Python 3.4 environment but it is running in a Python 2.7 environment instead. Which configuration file would you edit to correct the problem?

1. App-engine-python.yaml
2. App.yaml (a)
3. App-engine-python.py

**Q3 of 3**

You need to create a new Kubernetes Cluster on Google Cloud Platform that can autoscale the number of worker nodes. What should you do?

1. Create a cluster on Kubernetes Engine and enable autoscaling on Kubernetes Engine. (a)
2. Create a cluster on Kubernetes Engine and enable autoscaling on the instance group of the cluster.
3. Configure a Compute Engine instance as a worker and add it to an unmanaged instance group. Add a load balancer to the instance group and rely on the load balancer to create additional Compute Engine instances when needed.
4. Create Compute Engine instances for the workers and the master, and install Kubernetes. Rely on Kubernetes to create additional Compute Engine instances when needed.

```js
2. Autoscaling is not to be on instance group
```
