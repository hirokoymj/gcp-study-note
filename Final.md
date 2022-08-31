# Final

Q1:When you run a Kubanates engine cluster on google cloud platform, you gain the benefit of advanced cluster management features that include

1. Node Auto-repair to maintain node health
2. Automatic scalling of your claster's count
3. Load balancing for instances
4. Automatic upgrades for your cluster's node software
5. All of the above

<hr />

Q2: Company X is planing to deploy a web application to Google cloud hosted on a custom Linux distribution. The web site is going to be accesible globally and desires to scaleto satisfy demand.(Select two)

1. Network Load Balancer
2. App Engine Standard Environment
3. HTTP load Balancer
4. Managed Instance Group on Compute Engine

<hr />

Q3: You have created two types of instances to deliver different types of files based on incoming URL, For example we want to spend request for http://www.example.com/audio to one instance and request for http://www.example.com/video to another instance. Which type of load balancer is perfered in this scenario?

1. TCP load balancer
2. HTTP(s) load balancer
3. UDP load balancer
4. Any of the above

<hr />

Q4: Your company is buliding a large-scale web application. Each team is responsible for its own service component of the application and wants to manage its own individual project. You want each service to communicate with the other over RFC1918 address space. What should you do?

1. Configure Shared VPC. and add each project as a service of Shared VPC project
2. Configure each service to communicate with other HTTPS protocol
3. Configure a global load balancer for each project, and communicate btw each service using the global load balancer IP addresses.
4. Deploy each service into a single project within the save VPC

<hr />

Q5: You are running an application on Google compute engine instance. The destination IP address = 10.240.1.1 and there is route avaiable 10.240.1.0/24 and a route for 10.240.0.0/16. When an outgoing packets leaves a virtual machine instance, which route is appropriate to select?

1. it chooses the route: 10.240.1.0/24
2. it chooses the route: 10.240.1.0/16
3. GCP discards all the routes and send with smallest priority value
4. You can use tags to spend direct packets fo instances running in different zones
<hr />


Q7:
<hr />


Q8:
<hr />


Q9:
<hr />


Q10: Google Cloud has several tools to support continuous integration and continuous delivery. It offers () to build container images from various source code repositories and () to store and serve your conatiner images.

1. Google Container Builder and Google Cloud Storage
2. Google Kubernates engine and Google Container Registry
3. Google Container Builder and Google Container Storage
4. Google Docker container and Google Container Registry

<hr />

<hr />
Q18 Aron needs to bulid up a Compute Engine application in a solitary VPC accross two regions. The application should communicate over VPN to an on-premises network. How should the deploy the VPN?

1. Deploy Cloud VPN gateway in each region and ensure that each resion has at least one VPN tunnel to the on-premise peer gateway.
2. Create a Global Cloud VPN Gateway with VPN tunnels from each region to the on-premises Peer gateway.
3. Using VPC Shareing expose the VPC to on-premises n/w
4. None of the above

<hr />
Q19: You have deployed a web application in a load balanced, auto-scaled environment in Google Compute Engine. What are the possible policies that you can configure for initiating scalling action?

1. Average CPU utilization
2. Stackdriver Monitoring metric
3. HTTP load balancing serving capacity
4. Google cloud Pub/Sub queuing workload
5. All

<hr />
Q20: Nancy deployed a web application Google Kubernetes engine. The deployed application is running on port 8080. However when she tried to access the application, it was not accessible from internet. Which of the following option will help Nancy to access the application.

1. Access by configuring the load balancer to your cluster
2. Explicity expose your application to the internet which create an external IP address
3. You can replicate your cluster using kubectl scale command
4. Create another cluster with providing custom IP address
