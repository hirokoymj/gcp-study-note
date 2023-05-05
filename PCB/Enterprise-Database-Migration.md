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

- Create a database using CLI

  ```
  gcloud sql instances create db-server --database-version=MYSQL_5_7 --cpu=2 --memory=4GB --region=us-central1 --root-password=password123
  ```

- Backups
- Point-in time recovery
- Failover replica(HA):create a second db server in another zone.
- scale up as needed by adding machine resources.
- Cloud SQL Migration Assistant

### Lab intro: Creating a Cloud SQL Database

### Lab: Creating Cloud SQL Databases

- Create a Cloud SQL PostgreSQL database.
- SQL -> Create Instance -> PostgreSQL

- Connect to the database using the Cloud SDK.

  - Click the link of OPEN CLOUD SHELL

  ```
  \l
  CREATE DATABASE petsdb;
  \l
  \c petsdb;
  CREATE TABLE Pets(ID INT PRIMARY KEY NOT NULL, Name TEXT, Breed TEXT);
  INSERT INTO Pets (ID, Name, Breed) Values (1, 'Noir', 'Schnoodle');
  SELECT * FROM Pets;
  ```

- Create a Cloud SQL MySQL database using the CLI.

```
gcloud sql instances create mysql-db --tier=db-n1-standard-1 --zone=us-central1-a
gcloud sql users set-password root --host=xx.xx.xx.xx --instance=mysql-db --password=your-password-here
gcloud sql connect mysql-db --user=root --quiet
SHOW DATABASES;
```

- Connect to the MySQL database from a virtual machine.

  - SQL -> mysql-db -> Configuration -> Edit -> Connection -> Add Network -> Add VM's external IP -> Save

  ```
  gcloud compute instances create test-client --zone=us-central1-a --image=debian-9-stretch-v20200521 --image-project=debian-cloud
  ## install mysql client
  sudo apt-get update
  sudo apt-get install -y mysql-client !!! ERROR !!!
  mysql --host=[Database Public IP Address] --user=root --password
  SHOW DATABASES;
  ```

### Lab review: Creating a Cloud SQL Database

### Bare Metal Solution

## Networking for Secure Database Connectivity

### Building Secure Networks

- [Module 5: page 1-24](./qwiklab-pdfs/M5_Networking_for_Secure_Database_Connectivity.pdf)

### Lab intro: Using Terraform to Create Networks and Firewalls

### Lab Using Terraform to Create Networks and Firewalls

### Lab review: Using Terraform to Create Networks and Firewalls

1. provider.tf
2. variables.tf
3. terraform.tfvars
4. vpc-network-public.tf
5. terraform init/apply/destroy
6. vpc-firewall-rules-public.tf
7. terraform apply
8. random-id-generator.tf
9. test-server-linux.tf
10. vpc-network-private.tf
11. vpc-firewall-rules-private.tf

**vpc-firewall-rules-public.tf**

```
# allow ssh
resource "google_compute_firewall" "public-allow-ssh" {
  name    = "${google_compute_network.public-vpc.name}-allow-ssh"
  network = google_compute_network.public-vpc.name
  allow {
    protocol = "tcp"
    ports    = ["22"]
  }
  source_ranges = [ ### compare the source ranges with the private one.
    "0.0.0.0/0"
  ]
  target_tags = ["allow-ssh"]
}
```

**vpc-firewall-rules-private.tf**

- In the source_ranges section, don't allow traffic from all sources: only allow traffic from the public subnet IP CIDR range.

```
# allow ssh only from public subnet
resource "google_compute_firewall" "private-allow-ssh" {
  name    = "${google_compute_network.private-vpc.name}-allow-ssh"
  network = google_compute_network.private-vpc.name
  allow {
    protocol = "tcp"
    ports    = ["22"]
  }
  source_ranges = [
    "${var.subnet_cidr_public}" ###
  ]
  target_tags = ["allow-ssh"]
}
```

- [Lab github](https://github.com/GoogleCloudPlatform/training-data-analyst/tree/master/courses/db-migration/terraform-networks-completed)
