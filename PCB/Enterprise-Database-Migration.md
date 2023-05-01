# Enterprise Database Migration

## Google Cloud Data Migration Solutions

### Running Databases in a Kubernetes Cluster

### Lab intro: Running Databases in GKE

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
