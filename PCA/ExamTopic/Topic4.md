# TOPIC 4

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

**Question 5**

**Question 6**

**Question 7**
