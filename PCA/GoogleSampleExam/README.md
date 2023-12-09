# Google Sample Exam

**Question 1**

- B. Deploy an external HTTP(S) load balancer, configure Google Cloud Armor, and move the application onto Compute Engine virtual machines.
- B is correct because the external HTTP(s) load balancer will improve access latency and Cloud Armor can be configured to block the Distributed Denial-of-Service (DDoS) attack.

- [Optimize application latency with load balancing](https://cloud.google.com/load-balancing/docs/tutorials/optimize-app-latency)

- load balancing options shows how your choice of a specific load balancer on Google Cloud affects end-to-end **latency**.

- [Cloud Armor - Security policy overview](https://cloud.google.com/armor/docs/security-policy-overview)
  - Google Cloud Armor security policies protect your application by providing Layer 7 filtering
  - Google Cloud Armor security policies are available for the following load balancer and endpoint types:
  - Global external Application Load Balancer (HTTP/HTTPS)

<hr />

**Question 2**

- C is correct because it allows the customer to lower latency by connecting directly to a partner network that is directly connected to Google. This option will also allow the customer to use the lower bandwidth interfaces that they have on their current firewall.

- D is not correct because Dedicated Interconnect would require the customer to buy new hardware to get a 10 gig interface for their firewall.

- https://cloud.google.com/blog/products/networking/google-cloud-network-connectivity-options-explained
- If you need private, high-performance connectivity to Google Cloud, but installing equipment isn’t an option—or you would prefer to work with a service provider partner as an intermediary, then we recommend you go with a **Partner Interconnect.**

<hr />

**Question 3**

- B. Enable Virtual Private Cloud Service Controls, and create a service perimeter around the Cloud Storage resources.
- VPC service Controls, perimiter, data exfiltration

<hr />

**Question 4**

- A. Create an Identity-Aware Proxy (IAP) connector that points to the sales tool application.
- A is correct because Identity-Aware Proxy (IAP) connector allows you to manage access to HTTP-based apps outside of Google Cloud.
- C is not correct because Cloud Armor does not authenticate or authorize application access.
- Identity-Aware Proxy (IAP) allows you to manage access to HTTP-based apps outside of Google Cloud. This includes apps on-premises in your enterprise's data centers.

<hr />

**Question 5**

- C. Archive audit logs in BigQuery, and generate reports using Google Data Studio.
- C is correct because BigQuery allows easy querying for report generation, with low storage costs.
- https://cloud.google.com/logging/docs/audit#console

  - Build queries in the Logs Explorer.
  - Build queries using SQL.
  - Sample queries for security insights.

- [Query logs by using BigQuery](https://cloud.google.com/logging/docs/analyze/query-and-view#query-linked)

<hr />

**Question 6**

- A. Ensure that you aren’t running privileged containers.
- C. Ensure that you are using the native logging mechanisms.
- https://cloud.google.com/architecture/best-practices-for-operating-containers#use_the_native_logging_mechanisms_of_containers
- https://cloud.google.com/architecture/best-practices-for-operating-containers#avoid_privileged_containers
- A privileged container is a container that has access to all the devices of the host machine, bypassing almost all the security features of containers.

<hr />

**Question 7**

- D. Create a service perimeter around only the projects that handle sensitive data, and do not grant your developers access to it
- D is correct because VPC Service Controls protects data, and Cloud Shell facilitates rapid iteration of Google Cloud architecture changes.
- [VPC Service Controls - Cloud Shell](https://cloud.google.com/vpc-service-controls/docs/supported-products#shell)
- VPC Service Controls doesn't support Cloud Shell. VPC Service Controls treats Cloud Shell as outside of service perimeters and denies access to data that VPC Service Controls protects. However, VPC Service Controls allows access to Cloud Shell if a device that meets the access level requirements of the service perimeter initiates Cloud Shell.

<hr />

**Question 8**

- C. Define one SLO as 99% HTTP requests return the 2xx status code. Define the other SLO as 99% requests return within 100 ms.
- C is correct because it clearly defines the service level indicators and how to measure them.

- https://sre.google/workbook/implementing-slos/
- Service level objectives (SLOs) specify a target level for the reliability of your service. Because SLOs are key to making data-driven decisions about reliability

<hr />

**Question 9**

- B. Use Cloud CDN to cache the video content from HRL’s existing public cloud provider.
- Cloud CDN, Cache large object(video)
- B is correct because Cloud CDN can be used to cache data hosted on other cloud providers and supports large objects such as video.

<hr />

**Question 10**

- C. Use the Cloud Data Loss Prevention (DLP) API to provide data to the recommendation service.
- C is correct because Cloud DLP was specifically designed for this use case.

<hr />

**Question 11**

- D. Create a network plan for your VPC in Google Cloud that uses non- overlapping CIDR ranges with your on-premises environment. Use a Cloud Interconnect connection between your on-premises environment and Google Cloud.
- D is correct because this ensures your on premises network is compatible with your Google Cloud VPC.

<hr />

**Question 12**

- C. Have devices poll for connectivity to Pub/Sub and publish the latest messages on a regular interval to a shared topic for all devices.
- C is correct because Pub/Sub can handle the frequency of this data, and consumers of the data can pull from the shared topic for further processing.
- Sensor, pubsub

<hr />

**Question 13**

- A. Load logs into BigQuery.
- E. Upload log files into Cloud Storage.

- A is correct because BigQuery is a serverless cloud data warehouse for analytics and supports the volume and analytics requirement.
- B is not correct because Cloud SQL does not support the expected 100 TB. Additionally, Cloud SQL is a relational database and not the best fit for time-series log data formats.
- C is not correct because Cloud Logging is optimized for monitoring, error reporting, and debugging instead of analytics queries.
- D is not correct because Cloud Bigtable is optimized for read-write latency and analytics throughput, not analytics querying and reporting.
- E is correct because Cloud Storage provides the Coldline and Archive storage classes to support long-term storage with infrequent access, which would support the long-term disaster recovery backup requirement.

<hr />

**Question 14**

- C. Ensure that a firewall rule exists to allow load balancer health checks to reach the instances in the instance group.

- C is correct because health check failures lead to a VM being marked unhealthy and can result in termination if the health check continues to fail. Because you have already verified that the instances are functioning properly, the next step would be to determine why the health check is continuously failing.

<hr />

**Question 15**

- D. Add tags to each tier and set up firewall rules to allow the desired traffic flow.
- D is correct because as instances scale, they will all have the same tag to identify the tier. These tags can then be leveraged in firewall rules to allow and restrict traffic as required, because tags can be used for both the target and source.
- https://cloud.google.com/vpc/docs/add-remove-network-tags
- Tags enable you to make firewall rules and routes applicable to specific VM instances.
- You can set the network tags associated with an instance by making a direct API request.

<hr />

**Question 16**

- C. In a secret management system
- C is correct because a secret management system such as Secret Manager is a secure and convenient storage system for API keys, passwords, certificates, and other sensitive data. Secret Manager provides a central place and single source of truth to manage, access, and audit secrets across Google Cloud.

<hr />

**Question 17**

- B. Organization viewer, Project viewer
- Organization viewer grants the security team permissions to view the organization's display name.
- Project viewer grants the security team permissions to see the resources within projects.

<hr />

**Question 18**

- A. Use persistent disks to store the state. Start and stop the VM as needed.
- D. Use BigQuery billing export and labels to relate cost to groups.
- A is correct because persistent disks will not be deleted when an instance is stopped.
- D is correct because exporting daily usage and cost estimates automatically throughout the day to a BigQuery dataset is a good way of providing visibility to the finance department. Labels can then be used to group the costs based on team or cost center.

<hr />

**Question 19**

- C. Dynamically resize the SSD persistent disk to 500 GB.
- C is correct because persistent disk performance is based on the total persistent disk capacity attached to an instance and the number of vCPUs that the instance has. Incrementing the persistent disk capacity will increment its throughput and IOPS, which in turn improve the performance of MySQL.
