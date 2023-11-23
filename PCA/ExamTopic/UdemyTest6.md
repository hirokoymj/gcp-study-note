# Udemy Test 6

**Question 1 Dress4Win**

- D. Identify the number of virtual cores and RAM associated with the application server virtual machines align them to a custom machine type in the cloud, monitor performance, and scale the machine types up until the desired performance is reached.　 58％
- A - not correct. as its talking about Physical server size
- B - not correct. as we its talking about Max spec
- C - not correct. as its talking about the Smallest spec
- D - is CORRECT. as its recommending to map with on premises app VM Size

<hr />

**Question 2**

- A. Build or leverage an OAuth-compatible access control system。100％
- SAML is an authentication system. OAuth is an authorization system.
- Both can be used with SSO (Single sign on). SAML is for users and OAuth is more for applications.
- https://cloud.google.com/docs/authentication

<hr />

**Question 3 TerramEarth**

- B. Capacity planning, TCO calculations, opex/capex allocation. 92%
- From the case study, it can conclude that Management (CXO) all concern rapid provision of resources (infrastructure) for growing as well as cost management, such as Cost optimization in Infrastructure, trade up front capital expenditures (Capex) for ongoing operating expenditures (Opex), and Total cost of ownership (TCO)

<hr />

**Question 4 TerramEarth**

- AC 92%
- A. Open a support case regarding the CVE and chat with the support engineer.
- C. Read the CVEs from the Google Cloud Platform Security Bulletins to understand the impact.
- https://cloud.google.com/support/bulletins

<hr />

**Question 5 TerramEarth**

- A. Request Transfer Appliances from Google Cloud, export the data to appliances, and return the appliances to Google Cloud. 83%
- It will take 123 days to transfer
- The right answer is to use Transfer Appliance
  https://cloud.google.com/architecture/migration-to-google-cloud-transferring-your-large-datasets#time

<hr />

**Question 6 Dress4Win**

- A. Google Cloud Storage Coldline to store the data, and gsutil to access the data.
- **Infrequently** accessed data
- https://cloud.google.com/storage/docs/storage-classes#coldline
- Coldline storage is a very-low-cost, highly durable storage service for storing infrequently accessed data.

<hr />

**Question 7 Dress4Win**

- A. Use regional managed instance groups and a global load balancer to increase performance because the regional managed instance group can grow instances in each region separately based on traffic.
- Creating MIGs across regions behind a GLB, gives HA across Zones and Regions.

<hr />

**Question 8 TerramEarth**

- C. Create a BigQuery time-partitioned table for the European data, and set the partition expiration period to 36 months. For Cloud Storage, use gsutil to enable lifecycle management using a DELETE action with an Age condition of 36 months. 86%

When you create a table partitioned by ingestion time, BigQuery automatically loads data into daily, date-based partitions that reflect the data's ingestion or arrival time.

Ref: https://cloud.google.com/bigquery/docs/partitioned-tables#ingestion_time

And Google recommends you configure the default table expiration for your datasets, configure the expiration time for your tables, and configure the partition expiration for partitioned tables.

Ref: https://cloud.google.com/bigquery/docs/best-practices-storage#use_the_expiration_settings_to_remove_unneeded_tables_and_partitions

If the partitioned table has a table expiration configured, all the partitions in it are deleted according to the table expiration settings. For our specific requirement, we could set the partition expiration to 36 months so that partitions older than 36 months (and the data within) are automatically deleted.

Ref: https://cloud.google.com/bigquery/docs/managing-partitioned-tables#partition-expiration

<hr />

**Question 9 TerramEarth**

- D. Have the vehicle's computer compress the data in hourly snapshots, and store it in a GCS Coldline bucket Most Voted
- D is most cost effective as don't want to use until 'next year'

<hr />

**Question 10 Dress4Win**

- B. In the Cloud Platform Console download the list of the uptime servers' IP addresses and create an inbound firewall rule. 64%
- Uptime check monitoring
- Correct answer is B. https://cloud.google.com/monitoring/uptime-checks/using-uptime-checks#monitoring_uptime_check_list_ips-console
- It would be missing firewall rule that would be causing problem.
