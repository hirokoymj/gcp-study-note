# Foundation

### Google Cloud Console and Cloud Shell

- Task 1. Use the Cloud Console to create a bucket
- Task 2. Access Cloud Shell
- Task 3. Use Cloud Shell to create a Cloud Storage bucket
- Task 4. Explore more Cloud Shell features
- Task 5. Create a persistent state in Cloud Shell
- Task 6. Review the Google Cloud interface

### Infrastructure Preview

> In this lab, you build a sophisticated deployment in minutes using Marketplace. This lab shows several of the Google Cloud infrastructure services in action and illustrates the power of the platform. It introduces technologies that are covered in detail later in the class.

- Task 1. Use Marketplace to build a deployment
- Task 2. Examine the deployment
- Task 3. Administer the service
- Task 4. Review

### Demo: Expand a Subnet

### Demo: Internal and external IP

### VPC Networking

> Google Cloud Virtual Private Cloud (VPC) provides networking functionality to Compute Engine virtual machine (VM) instances, Kubernetes Engine containers, and the App Engine flexible environment. In other words, without a VPC network, you cannot create VM instances, containers, or App Engine applications. Therefore, each Google Cloud project has a default network to get you started.

> You can think of a VPC network as similar to a physical network, except that it is virtualized within Google Cloud. A VPC network is a global resource that consists of a list of regional virtual subnetworks (subnets) in data centers, all connected by a global wide area network (WAN). VPC networks are logically isolated from each other in Google Cloud.

> In this lab, you create an auto mode VPC network with firewall rules and two VM instances. Then, you convert the auto mode network to a custom mode network and create other custom mode networks as shown in the network diagram below. You also test connectivity across networks.

- Task 1. Explore the default network
- Task 2. Create an auto mode network
- Task 3. Create custom mode networks
- Task 4. Explore the connectivity across networks

### Private Google Access and Cloud Nat

> In this lab, you implement Private Google Access and Cloud NAT for a VM instance that doesn't have an external IP address. Then, you verify access to public IP addresses of Google APIs and services and other connections to the internet.

> VM instances without external IP addresses are isolated from external networks. Using Cloud NAT, these instances can access the internet for updates and patches, and in some cases, for bootstrapping. As a managed service, Cloud NAT provides high availability without user management and intervention.

- Task 1. Create the VM instance
- Task 2. Enable Private Google Access
- Task 3. Configure a Cloud NAT gateway
- Task 4. Configure and view logs with Cloud NAT Logging
- Task 5. Review

### Demo: Create a VM

### Creating Virtual Machines

> create several VMs with different characteristics.

- Task 1. Create a utility virtual machine
- Task 2. Create a Windows virtual machine
- Task 3. Create a custom virtual machine

### Working with Virtual Machines

> In this lab, you set up a game application—a Minecraft server.

> The Minecraft server software will run on a Compute Engine instance.

> You use an e2-medium machine type that includes a 10-GB boot disk, 2 virtual CPU (vCPU), and 4 GB of RAM. This machine type runs Debian Linux by default.

> To make sure there is plenty of room for the Minecraft server's world data, you also attach a high-performance 50-GB persistent solid-state drive (SSD) to the instance. This dedicated Minecraft server can support up to 50 players.

- Task 1. Create the VM
- Task 2. Prepare the data disk
- Task 3. Install and run the application
- Task 4. Allow client traffic
- Task 5. Schedule regular backups
- Task 6. Server maintenance
- Task 7. Review

# Core

### Demo: Custom roles

### Cloud IAM

> In this lab, you learn how to use the Service Account User role and how to grant roles.

- Task 1. Setup for two users
- Task 2. Explore the IAM console
- Task 3. Prepare a resource for access testing
- Task 4. Remove project access
- Task 5. Add storage access
- Task 6. Set up the Service Account User
- Task 7. Explore the Service Account User role
- Task 8. Review

### Cloud Storage

> Cloud Storage is a fundamental resource in Google Cloud, with many advanced features. In this lab, you exercise many Cloud Storage features that could be useful in your designs. You explore Cloud Storage using both the console and the gsutil tool.

- Task 1. Preparation
- Task 2. Access control lists (ACLs)
- Task 3. Customer-supplied encryption keys (CSEK)
- Task 4. Rotate CSEK keys
- Task 5. Enable lifecycle management
- Task 6. Enable versioning
- Task 7. Synchronize a directory to a bucket
- Task 8. Cross-project sharing

### Implementing Cloud SQL

> In this lab, you configure a Cloud SQL server and learn how to connect an application to it via a proxy over an external connection. You also configure a connection over a Private IP link that offers performance and security benefits. The app we chose to demonstrate in this lab is Wordpress, but the information and best practices are applicable to any application that needs SQL Server.

> By the end of this lab, you will have 2 working instances of the Wordpress frontend connected over 2 different connection types to their SQL instance backend, as shown in this diagram:

- Task 1. Create a Cloud SQL database
- Task 2. Configure a proxy on a virtual machine
- Task 3. Connect an application to the Cloud SQL instance
- Task 4. Connect to Cloud SQL via internal IP

### Demo: Billing Administration

### Examining Billing data with BigQuery

> In this lab, you learn how to use BigQuery to analyze billing data.

- Task 1. Use BigQuery to import data
- Task 2. Examine the table
- Task 3. Compose a simple query
- Task 4. Analyze a large billing dataset with SQL

### Resource Monitoring

> In this lab, you learn how to use Cloud Monitoring to gain insight into applications that run on Google Cloud.

- Task 1. Create a Cloud Monitoring workspace
- Task 2. Custom dashboards
- Task 3. Alerting policies
- Task 4. Resource groups
- Task 5. Uptime monitoring
- Task 6. Disable the alert

### Error Reporting and Debugging

> In this lab, you learn how to use Cloud Error Reporting and integrate Cloud Debugger.

- Task 1. Create an application
- Task 2. Explore Cloud Error Reporting
- Task 3. Review

# Scaling and Automation

### Virtual Private Networks (VPN)

> In this lab, you establish VPN tunnels between two networks in separate regions such that a VM in one network can ping a VM in the other network over its internal IP address.

- Task 1. Explore the networks and instances
- Task 2. Create the VPN gateways and tunnels
- Task 3. Verify VPN connectivity
- Task 4. Review

### Configuring an HTTP Load Balancer with Autoscaling

> Google Cloud HTTP(S) load balancing is implemented at the edge of Google's network in Google's points of presence (POP) around the world. User traffic directed to an HTTP(S) load balancer enters the POP closest to the user and is then load-balanced over Google's global network to the closest backend that has sufficient available capacity.

> In this lab, you configure an HTTP load balancer as shown in the diagram below. Then, you stress test the load balancer to demonstrate global load balancing and autoscaling.

- Task 1. Configure a health check firewall rule
- Task 2. Create a NAT configuration using Cloud Router
- Task 3. Create a custom image for a web server
- Task 4. Configure an instance template and create instance groups
- Task 5. Configure the HTTP load balancer
- Task 6. Stress test the HTTP load balancer
- Task 7. Review

### Configuring an Internal Load Balancer

> Google Cloud offers Internal Load Balancing for your TCP/UDP-based traffic. Internal Load Balancing enables you to run and scale your services behind a private load balancing IP address that is accessible only to your internal virtual machine instances.

> In this lab, you create two managed instance groups in the same region. Then you configure and test an internal load balancer with the instances groups as the backends, as shown in this network diagram:

- Task 1. Configure internal traffic and health check firewall rules.
- Task 2: Create a NAT configuration using Cloud Router
- Task 3. Configure instance templates and create instance groups
- Task 4. Configure the internal load balancer
- Task 5. Test the internal load balancer
- Task 6. Review

### Terraform

> Terraform enables you to safely and predictably create, change, and improve infrastructure. It is an open-source tool that codifies APIs into declarative configuration files that can be shared among team members, treated as code, edited, reviewed, and versioned.

> In this lab, you create a Terraform configuration with a module to automate the deployment of Google Cloud infrastructure. Specifically, you deploy one auto mode network with a firewall rule and two VM instances, as shown in this diagram:

### Demo: Launch on Google Cloud Marketplace
