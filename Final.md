# Final

Q1:When you run a Kubanates engine cluster on google cloud platform, you gain the benefit of advanced cluster management features that include

1. Node Auto-repair to maintain node health - (Auto repair)
2. Automatic scalling of your claster's count - (Auto scale)
3. Load balancing for instances(Global load balancing)
4. Automatic upgrades for your cluster's node software
5. All of the above (a)

https://cloud.google.com/kubernetes-engine#:~:text=Pod%20and%20cluster%20autoscaling,CPU%20utilization%20or%20custom%20metrics.

<hr />

Q2: Company X is planing to deploy a web application to Google cloud hosted on a custom Linux distribution. The web site is going to be accesible globally and desires to scale to satisfy demand.(Select two)

1. Network Load Balancer
2. App Engine Standard Environment (a)
3. HTTP load Balancer
4. Managed Instance Group on Compute Engine (a)

<hr />

Q3: You have created two types of instances to deliver different types of files based on incoming URL, For example we want to spend request for http://www.example.com/audio to one instance and request for http://www.example.com/video to another instance. Which type of load balancer is perfered in this scenario?

1. TCP load balancer
2. HTTP(s) load balancer (a)
3. UDP load balancer
4. Any of the above

<hr />

Q4: Your company is buliding a large-scale web application. Each team is responsible for its own service component of the application and wants to manage its own individual project. You want each service to communicate with the other over RFC1918 address space. What should you do?

1. Configure Shared VPC. and add each project as a service of Shared VPC project. (a)
2. Configure each service to communicate with other HTTPS protocol
3. Configure a global load balancer for each project, and communicate btw each service using the global load balancer IP addresses.
4. Deploy each service into a single project within the save VPC

https://cloud.google.com/vpc/docs/shared-vpc

<hr />

Q5: You are running an application on Google compute engine instance. The destination IP address = 10.240.1.1 and there is route avaiable 10.240.1.0/24 and a route for 10.240.0.0/16. When an outgoing packets leaves a virtual machine instance, which route is appropriate to select?

1. it chooses the route: 10.240.1.0/24
2. it chooses the route: 10.240.1.0/16
3. GCP discards all the routes and send with smallest priority value
4. You can use tags to spend direct packets fo instances running in different zones
<hr />

Q6: You have configured a auto scaled environment in GCP using a set of configuratino entries such as min, max, cool down period etc. After some day, you made some changes in the auto-scaling configuration s programmatically (either using the set-autoscaling command or API call). You noticed that the scaling happens in a totally different way than expected. What could be possible reason?

1. You forgot to specify the entire set of configuration parameters during the command execution and auto scaler rolled back to default values for un-specified parameters.(A)
2. Auto-scaling changes has not taken effect due to some reason.
3. The command is not executed successfully and resulted in error
4. Auto scalling will allow you to update scaling configuration through console only and not programatically.

https://cloud.google.com/compute/docs/autoscaler

<hr />

Q7: You deployed a web application in a google linux VM instance with an external IP address 130.211.160.207. While trying the access the web application using browser through the URL :130.211.160.207/<project-id>, you are getting a connection denied error.

1. They SSH connection failed because of the incorrect private key.
2. SSH connection is not added in the firewall rule of the instance. (a)
3. HTTP ingress firewall rule is not enabled for the instance
4. RDP ingress is not enabled in the firewall rules

https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-ssh#console

<hr />

Q8: You have a persisntant disk which has static files for read only purpose. You want to make these files available for three different web applications running on three different GCP VM instance. Is it possible to share the persistant disk with all the three instances?
Hint: Refer Google compute engine FAQs

1. No. You cannot share the persistent disk with multiple VM instances
2. Yes. You can share the persistent disk with multiple VM instances since the files are read only
3. No. You cannot share the persistent disk with multiple VM instances
4. Yes. You can share the persistent disk with multiple VM instances if the disk is in read-only mode (correct)

<hr />

Q9: An enterprise has the following requirements. Few legacy applications are to be re-architected in cloud platform as loosely coupled components triggered on events. The events happen asynchronously and does not require any time consuming operations. Which following Google Cloud Services would be suitable?

1. Host the application on Google App Engine
2. Host the application on Google Compute Engine
3. Construct the application as a set of google cloud function that trigger on events.(a)
4. Host the application using Docker containers.

<hr />

Q10: Google Cloud has several tools to support continuous integration and continuous delivery. It offers () to build container images from various source code repositories and () to store and serve your conatiner images.

1. Google Container Builder and Google Cloud Storage
2. Google Kubernates engine and Google Container Registry
3. Google Container Builder and Google Container Storage
4. Google Docker container and Google Container Registry (a)

https://cloud.google.com/container-registry
Store, manage, and secure your Docker container images.

<hr />

Q11: Hema is working as a Network Engineer in a Cloud consulting company. Their application is hosted Google Cloud Platform. She is running a program in compute instance. It pings 10000 websites for every 5 min to check the website availability. Each request is a http head request, hence the response size will be 1kb per request. How Google changes for this ingress and egress traffic?

1. You will be charge for the total inbound and outgoing traffic of GCP.
2. instances with external IP or the use NAT can access internet.
3. Both ingress request an degress request traffics are chargable.
4. Your outbound HTTP requests will be count as egress traffic and you will be charged. (a)

<hr />

Q12:

<hr />

Q13: Stephen is deployed application on App Engine that has to integrate with an on-premise data set. For security purpose, his on-premises data set should not be open through the public. How would it be advisable for him to respond?

1. Deploy his appliation on App Engine standard environment and use App Engine firewall rules to limit access to the on-premise database.
2. Deploy his appliation on App Engine standard environment and use Cloud VPN limit access to opne the on-premise database.
3. Deploy his appliation on App Engine flexible environment and use App Engine firewall rules to limit access to the on-premise database. (a)
4. Deploy his appliation on App Engine flexible environment and use Cloud VPN limit access to on the on-premise database.

<hr />

Q14: With the help of managed instance group a company deployed its web application on multiple instances. If an instance gets crashed, which assertion would be right for this senario from the below options? Select two.

1. Automatically the managed instance group creates an instance with a random name.
2. The managed instance group creates an instance with a new instance template.(a)
3. Traffic will not be sent to the VM that went down.
4. Automatically, new instance gets created with the instance template that is suppled during the creation of a VM. (a)

<hr />

Q15: You need to choose and design register asset for a set of batch progressing jobs. These jobs take around two hours to finish and run nightly. In order to limit administrator costs what would you choose?

1. Select GKE and Use a single-node cluster with a small instance type.
2. Select GKE and Use a three-node cluster with micro instance types. (a)
3. Select Compute Engine and use preemptible VM instance of the standard type.

<hr />

Q16: An Enterprise wants to have a hybrid solution where the instances in cloud can communicate to their on-premise data center and vice versa. They created VPC and provision ed their resource in it. What would be the best solution?

1. Create a custom mode Network adn use Dynamic routes to allow instances to communicate on-premises resources and vice versa.(a)
2. Create an auto mode network and subnets
3. Create a custom mode Network and use static routes to. How instance to communicate on-premises resource and vice versa.

<hr />

Q17: You have created an instance template in us-central-b zone and wan to create managed instance groups having identical configuration using the same instance template in multiple resions. Select the most appropriate solution for doing this with least time and effort?

1. Instance template is a global resource which can be unconditionally used across zones or regions
2. Instance template can be used across zones or regions without any zonal resources in it
3. Create identical template for each rezion and create managed instance group based on the indifidual templates.
4. Copy one instance template to another region using copy-instance template command then use to create instance group in other regions.(a)

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
