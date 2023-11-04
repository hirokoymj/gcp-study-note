# TOPIC 4 - EHR Healthcare

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**

- A. Verify EHR's product usage against the list of compliant products on the Google Cloud compliance page. Most Voted
- B. Advise EHR to execute a Business Associate Agreement (BAA) with Google Cloud.
- the Health Insurance Portability and Accountability Act (known as HIPAA)
- https://cloud.google.com/security/compliance/hipaa
- **Essential best practices:**

```
1. Execute a Google Cloud BAA. You can request a BAA directly from your account manager.

2. Disable or otherwise ensure that you do not use Google Cloud Products that are not explicitly covered by the BAA (see Covered Products) when working with PHI.
```

**Question 2**

- AD 40%
- A. Enable Binary Authorization on GKE, and sign containers as part of a CI/CD pipeline.
- D. Configure Container Registry to use vulnerability scanning to confirm that there are no vulnerabilities before deploying the workload.
- https://cloud.google.com/binary-authorization/docs/overview
- **What is Binary Authorization?**
  > Binary Authorization is a Google Cloud product that you can use to implement software supply-chain security measures when you develop and deploy container-based applications.

**Question 3**

- A. Add a new Dedicated Interconnect connection.
- https://cloud.google.com/network-connectivity/docs/interconnect/how-to/dedicated/modifying-interconnects
- **The following items can't be modified for existing Dedicated Interconnect connections:**

> The link type on a Dedicated Interconnect connection. For example, changing the circuit from 10 Gpbs to 100 Gbps. If you want to migrate to 100 Gbps, you must first provision a new 100‑Gbps Dedicated Interconnect connection alongside your existing 10‑Gbps connection, and then migrate the traffic onto the 100‑Gbps connection.

- B - it is not possible to change interconnect link type.
- C - more problematic and probably more expensive
- D - Google does not offer a service level agreement (SLA) with Carrier Peering

**Question 4**

D. Configure two Dedicated Interconnect connections in one metro (City) and two connections in another metro, and make sure the Interconnect connections are placed in different metro zones.

**Business requirements for this case:**

- Provide a minimum 99.9% availability for all customer-facing systems.
- Provide a secure and high-performance connection between on-premises systems and Google Cloud.

A. - builds us a 99.9% SLA partner interconnect, covering all business requirements.

B. - VPN is not suitable for the business requirements.

C. - Direct peering is used for workspace, instead of DMZ, again - not suitable.

D. - builds us a 99.99% SLA dedicated interconnect, covering all business requirements.

The answer to choosing A or D lies in the question, stating: "You want to follow Google's recommended practices for production-level applications."

Google recommends using the 99.99% SLA interconnect (dedicated or partner) for production-level applications as stated here:

- https://cloud.google.com/network-connectivity/docs/interconnect/tutorials/production-level-overview

**Question 5**

- C. Turn off Pub/Sub message batching.
- C - The cost of batching is latency for individual messages, which are queued in memory until their corresponding batch is filled and ready to be sent over the network. To minimize latency, batching should be turned off.
  https://cloud.google.com/pubsub/docs/publisher?hl=en#batching

- A incorrect. Application timeout because of publisher latency, nothing to do with timeout retry with publish request.
- D does not make sense at all.
- B is about receiver, not publisher.

**Question 6**

- A. Create an Organizational Policy with a constraint to allow external IP addresses only on the frontend Compute Engine instances. Most Voted

- https://cloud.google.com/compute/docs/ip-addresses/reserve-static-external-ip-address#disableexternalip

**Question 7**

- A 61%, C 39%
- A. Use a private cluster with a private endpoint with master authorized networks configured.

- A: https://cloud.google.com/kubernetes-engine/docs/concepts/private-cluster-concept

> Public endpoint access disabled: This is the most secure option as it prevents all internet access to the control plane. This is a good choice if you have configured your on-premises network to connect to Google Cloud using Cloud Interconnect or Cloud VPN.

> If you disable public endpoint access, then you must configure authorized networks for the private endpoint. If you don't do this, you can only connect to the private endpoint from cluster nodes or VMs in the same subnet as the cluster.
