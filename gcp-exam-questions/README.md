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
https://kubernetes.io/docs/concepts/services-networking/service/

<hr />

Q25. Which of the following products will allow you to perform live debugging without stopping your application?

- A. App Engine Active Debugger (AEAD)
- B. Stackdriver Debugger A
- C. Code Inspector
- D. Pause IT

Answer: B
https://cloud.google.com/debugger/docs/

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

45. What option does Cloud SQL offer to help with high availability?

- A. Point-in-time recovery
- B. The AlwaysOn setting
- C. Snapshots
- D. Failover replicas

Reveal
Answer: D
https://cloud.google.com/sql/docs/configure-ha#test

<hr />

46. Regarding Compute Engine: when executing a startup script on a Linux server which user does the instance execute the script as?

- A. ubuntu
- B. The Google provided “gceinstance” user
- C. Whatever user you specify in the console
- D. root

Reveal
Answer: D
https://cloud.google.com/compute/docs/startupscript

<hr />

47. Which of the follow methods will not cause a shutdown script to be executed?

- A. When an instance shuts down through a request to the guest operating system
- B. A preemptible instance being terminated
- C. An instances.reset API call
- D. Shutting down via the cloud console

Reveal
Answer: C
https://cloud.google.com/compute/docs/shutdownscript

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
