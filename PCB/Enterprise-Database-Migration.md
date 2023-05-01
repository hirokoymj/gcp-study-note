# Enterprise Database Migration

## Google Cloud Data Migration Solutions

### Running Databases in a Kubernetes Cluster

- Kubernetes is an open-source, cross-platform framework for running applications inside a cluster
- Kubernetes automates the deployment of applications running in containers.

### Lab intro: Running Databases in GKE

- Create a GKE cluster
- Deploy MySQL on the cluster
- Use Helm to deploy MySQL on the cluster

### Lab: Running Databases in GKE

- Create a GKE cluster

  ```
  kubanates Engine -> Clusters -> Create -> Standard cluster -> Connect
  gcloud container clusters get-credentials sample-cluster --location=us-central1-f
  kubectl get nodes

  kubectl create secret generic mysql-secrets --from-literal=ROOT_PASSWORD="password"
  ```

- Create the Kubernetes configuration files.

  - **volume.yaml**
  - **deployment.yaml**: configure the MySQL db (MySQL docker image, an environment variable)
  - **service.yaml**: Note: This creates a service that provides access to the database from within the cluster that forwards requests to the MySQL database.

- deploy a db

  ```
  kubectl apply -f volume.yaml
  kubectl apply -f deployment.yaml
  kubectl apply -f service.yaml
  kubectl get pods
  ```

- Run MySQL

```
kubectl exec -it mysql-deployment-76fdc44468-rfhbp /bin/bash

//Now you're at a bash prompt within the MySQL pod.

mysql -u root -p
show databases;
create database pets;
```

- Use Helm

```

helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install mydb bitnami/mysql
helm ls
helm delete

```

### Lab review: Running Databases in GKE

- Created a GKE cluster
- Deployed MySQL on the cluster
- Used Helm to deploy MySQL on the cluster

## Managed Relational Databases

### Lab intro: Creating a Cloud SQL Database

### Lab: Creating Cloud SQL Databases

### Lab review: Creating a Cloud SQL Database
