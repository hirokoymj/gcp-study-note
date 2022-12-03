# Quiz: Applications in the Cloud

https://www.cloudskillsboost.google/course_sessions/1596805/quizzes/326684

Q:
What are the advantages of using App Engine’s flexible environment instead of its standard environment? (Select 3).

- Your application can write to the local disk.
- Google provides automatic in-place security patches.
- You can use SSH to connect to the virtual machines on which your application runs.
- Your application can execute code in background threads.
- You can install third-party binaries.

Q:
Which statements are true about App Engine? (Select 2).

- The daily billing for an App Engine application can drop to zero.
- App Engine charges you based on the resources you preallocate instead of the resources you use.
- App Engine manages the hardware and networking infrastructure required to run your code.
- Developers who write for App Engine do not need to code their applications in any particular way to use the service.
- App Engine requires you to supply or code your own application load balancing and logging services.

Q:
Cloud Run can only pull images from:

- Docker Hub
- GitHub
- Artifact Registry
- Self-hosted registries

# Quiz: Developing and Deploying in the Cloud

https://www.cloudskillsboost.google/course_sessions/1596805/quizzes/326688

- Your score: 50% Passing score: 75%

Q:
Why might a Google Cloud customer choose to use Cloud Functions?

- Cloud Functions is a free service for hosting compute operations.
- Their application contains event-driven code that they don't want to provision compute resources for.\*\*
- Cloud Functions is the primary way to run Node.js applications in Google Cloud.
- Their application has a legacy monolithic structure that they want to separate into microservices. X

# Quiz: Logging and Monitoring in the Cloud

- Your score: 60% Passing score: 75%

Q:There are “Four Golden Signals” that measure a system’s performance and reliability. What are they?

- Latency, traffic, saturation, errors
- KPIs, SLIs, SLOs, SLAs
- Availability, durability, scalability, resiliency x
- Get, post, put, delete

Q:Which definition best describes a service level indicator (SLI)?

- A percentage goal of a measure you intend your service to achieve X
- A key performance indicator; for example, clicks per session or customer signups X
- A time-bound measurable attribute of a service \*\*
- A contract with your customers regarding service performance X

# Quiz: Containers in the Cloud

- Your score: 57% Passing score: 75%
- Your score: 71% Passing score: 75%
- Your score: 85% Passing score: 75%
- Your score: 100% Passing score: 75%

- Q:What is a Kubernetes pod?

- A group of nodes X
- A group of containers \*\*
- A group of VMs X
- A group of clusters

https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster

> A cluster consists of at least one cluster control plane machine and multiple worker machines called nodes. Nodes are Compute Engine virtual machine (VM) instances that run the Kubernetes processes necessary to make them part of the cluster. You deploy applications to clusters, and the applications run on the nodes.

> Review the "Kubernetes" lecture.

Pods are the smallest, most basic deployable objects in Kubernetes. A Pod represents a single instance of a running process in your cluster. Pods contain one or more containers, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources.

Q: Where do the resources used to build Google Kubernetes Engine clusters come from?

- Bare metal servers
- Compute Engine \*\*
- Cloud Storage
- App Engine

Q: What is a Kubernetes cluster?

- A group of pods that manage the administration of a Kubernetes application. X
- A group of machines where Kubernetes can schedule workloads. \*\*
- A group of containers that provide high availability for applications.

> Review the "Kubernetes" lecture.

Q: How do containers access an operating system?

- Containers use a shared base operating system stored in a Cloud Storage bucket. X
- Each container has its own instance of an operating system. X
- Containers use a shared base operating system stored in a shared runtime layer.X
- Containers use a shared base operating system stored in a shared kernel layer.

> Review the "Introduction to containers" lecture.
