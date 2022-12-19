# GCP EXAM QUESTIONS -1

https://gcp-examquestions.com/gcp-associate-cloud-engineer-practice-exam-part-1/

Q11. You have an application server running on Compute Engine in the europe-west1-d zone. You need to ensure high availability and replicate the server to the europe-west2-c zone using the fewest steps possible. What should you do?

- A. Create a snapshot from the disk. Create a disk from the snapshot in the europe-west2-c zone. Create a new VM with that disk.
- B. Create a snapshot from the disk. Create a disk from the snapshot in the europe-west1-d zone and then move the disk to europe-west2-c. Create a new VM with that disk.
- C. Use “gcloud” to copy the disk to the europe-west2-c zone. Create a new VM with that disk.
- D. Use “gcloud compute instances move” with parameter “–destination-zone europe-west2-c” to move the instance to the new zone.

Reveal
Answer: A is correct because this makes sure the VM gets replicated in the new zone.

<hr />

Q15. You have created a Kubernetes deployment, called Deployment-A, with 3 replicas on your cluster. Another deployment, called Deployment-B, needs access to Deployment-A. You cannot expose Deployment-A outside of the cluster. What should you do?

- A. Create a Service of type NodePort for Deployment A and an Ingress Resource for that Service. Have Deployment B use the Ingress IP address.
- B. Create a Service of type LoadBalancer for Deployment A. Have Deployment B use the Service IP address.
- C. Create a Service of type LoadBalancer for Deployment A and an Ingress Resource for that Service. Have Deployment B use the Ingress IP address.
- D. Create a Service of type ClusterIP for Deployment A. Have Deployment B use the Service IP address.

Reveal
Answer: D is correct because this exposes the service on a cluster-internal IP address. Choosing this method makes the service reachable only from within the cluster.

**Links:**

1. https://cloud.google.com/kubernetes-engine/docs/concepts/service

**Service**

- There are different types of Services, which you can use to group a set of Pod endpoints into a single resource.[1]

**What is a Kubernetes Service?**

- The idea of a Service is to group a set of Pod endpoints into a single resource. You can configure various ways to access the grouping. By default, you get a stable cluster IP
- A Service identifies its member Pods with a selector.

  ```
  apiVersion: v1
  kind: Service
  metadata:
  name: my-service
  spec:
  selector: // A Service identifies its member Pods with a selector
    app: metrics
    department: engineering
  ports:

  ```

**Why use a Kubernetes Service?**

- In a Kubernetes cluster, each Pod has an internal IP address. But the Pods in a Deployment come and go, and their IP addresses change. So it doesn't make sense to use Pod IP addresses directly. With a Service, you get a stable IP address that lasts for the life of the Service

**Types of Kubernetes Services**

- **ClusterIP** (default): Internal clients send requests to a stable internal IP address.

- **NodePort**: Clients send requests to the IP address of a node on one or more nodePort values that are specified by the Service.

- **LoadBalancer**: Clients send requests to the IP address of a network load balancer.

**Services of type ClusterIP**

- When you create a Service of type ClusterIP, Kubernetes creates a stable IP address that is accessible from nodes in the cluster.

```
apiVersion: v1
kind: Service
metadata:
  name: my-cip-service
spec:
  selector:
    app: metrics
    department: sales
  type: ClusterIP
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

- You can create the Service by using kubectl apply -f [MANIFEST_FILE]. After you create the Service, you can use kubectl get service to see the stable IP address:

```
kubectl apply -f [MANIFEST_FILE]
```

```
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)
my-cip-service   ClusterIP   10.11.247.213   none          80/TCP
```

  <hr />

Q25. Which of the following products will allow you to perform live debugging without stopping your application?

- A. App Engine Active Debugger (AEAD)
- B. Stackdriver Debugger A
- C. Code Inspector
- D. Pause IT

Answer: B
https://cloud.google.com/debugger/docs/

![](images/25.png)

<hr />

Q36. Which of the following is not helpful for mitigating the impact of an unexpected failure or reboot?

- A. Use persistent disks
- B. Configure tags and labels
- C. Use startup scripts to re-configure the system as needed
- D. Back up your data

Answer: B

**Unexpected single VM failure**

- Unexpected single VM failures can be due to hardware or system failure. You can mitigate these events by using persistent disks and startup scripts to save your data and re-enable software after you restart the VM.

1. https://cloud.google.com/compute/docs/tutorials/robustsystems#typesoffailures

<hr />
Q41. What type of firewall rule(s) does Google Cloud’s networking support?

- A. deny
- B. allow, deny & filtered
- C. allow
- D. allow & deny

Reveal
Answer: A(D is correct)

- VPC firewall rules let you allow or deny connections to or from your virtual machine (VM) instances based on a configuration that you specify.[3]

Links:

1. https://cloud.google.com/compute/docs/networking
2. https://www.examtopics.com/discussions/google/view/19714-exam-professional-cloud-architect-topic-9-question-22/
3. https://cloud.google.com/vpc/docs/firewalls

<hr />

Q43. Which of the following is not a valid metric for triggering autoscaling?

- A. Google Cloud Pub/Sub queuing
- B. Average CPU utilization
- C. Stackdriver Monitoring metrics
- D. App Engine Task Queues

Reveal
Answer: D
https://cloud.google.com/compute/docs/autoscaler/

![](images/43.png)

<hr />

Q45. What option does Cloud SQL offer to help with high availability?

- A. Point-in-time recovery
- B. The AlwaysOn setting
- C. Snapshots
- D. Failover replicas

Reveal
Answer: D
https://cloud.google.com/sql/docs/configure-ha#test

- 障害迂回 ◆ 主にコンピューターシステムで、エラーが起きたときにそのエラーをやり過ごす（何もなかったかのように振る舞う）ための機能。例えばサーバーなら、エラー時にすぐ別のサーバーに自動的に切り替わるようにしておく。
- high availability (HA)
- ![](images/45.png)
- ![](images/45-failover.png)

**Links:**

1. https://cloud.google.com/sql/docs/mysql/high-availability#failover-overview
2. https://cloud.google.com/sql/docs/mysql/configure-ha#verify_an_instance_has

<hr />

Q46. Regarding Compute Engine: when executing a startup script on a Linux server which user does the instance execute the script as?

- A. ubuntu
- B. The Google provided “gceinstance” user
- C. Whatever user you specify in the console
- D. root

Reveal
Answer: D

**Startup Script Overview**

- A startup script is a file that contains commands that run when a virtual machine (VM) instance boots. Compute Engine provides support for running startup scripts on Linux VMs and Windows VMs.[2]
- For Linux VMs, by using the root user.[1]
- For Windows VMs, by using the System account.[1]

**Links:**

1. https://cloud.google.com/compute/docs/shutdownscript
2. https://cloud.google.com/compute/docs/startupscript

<hr />

Q47. Which of the follow methods will not cause a shutdown script to be executed?

- A. When an instance shuts down through a request to the guest operating system
- B. A preemptible instance being terminated
- C. An instances.reset API call
- D. Shutting down via the cloud console

Reveal
Answer: C

- Create and run shutdown scripts that execute commands right before a virtual machine (VM) instance is stopped or restarted. This is useful if you rely on automated scripts to start up and shut down instances, allowing instances time to clean up or perform tasks, such as exporting logs, or syncing with other systems.

**Links:**

1. https://cloud.google.com/compute/docs/shutdownscript
2. https://cloud.google.com/compute/docs/startupscript

<hr />

Q52. Which is the fastest instance storage option that will still be available when an instance is stopped?

A. Local SSD
B. Standard Persistent Disk
C. SSD Persistent Disk
D. RAM disk

Reveal
Answer: C
https://cloud.google.com/compute/docs/disks/

> Local SSDs and RAM disks disappear when you stop an instance. Standard Persistent Disks and SSD Persistent Disks both survive when you stop an instance, but SSD Persistent Disks have up to 4 times the throughput and up to 40 times the I/O operations per second of a Standard Persistent Disk.
> Reference: https://cloud.google.com/compute/docs/disks/

**Persistent disks**

- Persistent disks are durable network storage devices that your instances can access like physical disks in a desktop or a server. The data on each persistent disk is distributed across several physical disks. Compute Engine manages the physical disks and the data distribution for you to ensure redundancy and optimal performance.

- Persistent disks are located independently from your virtual machine (VM) instances, so you can detach or move persistent disks to keep your data even after you delete your instances.

- Persistent disk performance scales automatically with size, so you can resize your existing persistent disks or add more persistent disks to an instance to meet your performance and storage space requirements.

**Disk types**

- Standard persistent disks (pd-standard)
- Balanced persistent disks (pd-balanced)
- Performance (SSD) persistent disks (pd-ssd)
  > Suitable for enterprise applications and high-performance databases that require lower latency and more IOPS than standard persistent disks provide.

**Local SSDs**

- Local SSDs are physically attached to the server that hosts your VM instance. Local SSDs have higher throughput and lower latency than standard persistent disks or SSD persistent disks

**Links:**

1. https://cloud.google.com/compute/docs/disks/#pdspecs
2. https://cloud.google.com/compute/docs/disks/#localssds

<hr />

Q65. Suppose you have a web server that is working properly, but you can’t connect to its instance VM over SSH. Which of these troubleshooting methods can you use without disrupting production traffic? (Select 3 answers.)

- A. Create a snapshot of the disk and use it to create a new disk; then attach the new disk to a new instance
- B. Use netcat to try to connect to port 22
- C. Access the serial console output
- D. Create a startup script to collect information.

<hr />
Q68. What are two of the actions you can take to troubleshoot a virtual machine instance that won’t start up at all? (Select 2 answers.)

- A. Increase the CPU and memory on the instance by changing the machine type.
- B. Validate that your disk has a valid file system.
- C. Examine your virtual machine instance’s serial port output.
- D. Connect to your virtual machine instance using SSH.

Reveal
Answer: B C
https://cloud.google.com/compute/docs/troubleshooting#pdboot

<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
<hr />
