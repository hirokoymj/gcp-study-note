# Topic 3 - Helicopter Racing League (HRL)

https://www.examtopics.com/exams/google/professional-cloud-architect/view/3/

**Question 1**

- B. Encrypt the card data with a deterministic algorithm stored in Firestore using Datastore mode.
- google https://cloud.google.com/architecture/tokenizing-sensitive-cardholder-data-for-pci-dss

**Question 2**

- D %, omermaH
- Google Cloud Armor security policies to filter incoming traffic to the following destinations:
- https://cloud.google.com/armor/docs/configure-security-policies#create-rules

- updates a security policy rule with the name "1000" in the security policy "hlr-policy". The rule allows traffic that matches the specified expression and has the action "allow".

```
  gcloud compute security-policies rules update 1000 --security-policy=hlr-policy --expression="evaluatePreconfigurationExpr(`sourceiplist-fastly`)" --action=allow**
```

- Ex - the following command adds a rule to block traffic from IP address ranges 192.0.2.0/24 and 198.51.100.0/24. The rule has priority 1000 and is a rule in a policy called my-policy:

```
gcloud compute security-policies rules create 1000 \
    --security-policy my-policy \
    --description "block traffic from 192.0.2.0/24 and 198.51.100.0/24" \
    --src-ip-ranges "192.0.2.0/24","198.51.100.0/24" \
    --action "deny-403"
```

**Question 3**

- C. Configure the deployment job to notify a Pub/Sub queue that triggers a Cloud Function. 82%, omermaH

- Answer C seems to be right. There are 2 requirements here,

1. Run every time it is released on Tuesday
2. Set Airwolf to run weekly
   Since a new version of the predictive capability application is released every tuesday evening at 3.00 am, the deployment job would run every time its released which is every week recurring. So both the requirements above are satisfied

**Question 4**

- A. Use Explainable AI. 100%, omermaH
- https://cloud.google.com/explainable-ai

**Question 5**

- C. Use BigQuery for its scalability and ability to add columns to a schema. Partition race data based on season. 100%,
- For HRL's data storage needs, it is recommended to use BigQuery due to its scalability and ability to handle large amounts of data. By partitioning the race data based on season, HRL can easily access and query specific seasons' data while also taking into consideration future data growth. BigQuery also allows for the flexibility to add new columns to the schema as needed, making it easier to adapt to changes in the data being collected. Additionally, BigQuery's pay-per-use pricing model allows HRL to only pay for the data storage and querying they use, making it a cost-effective solution. omermaH

**Question 6**

- C. Use the gcloud recommender command to list the idle virtual machine instances. 100%
- https://cloud.google.com/compute/docs/instances/viewing-and-applying-idle-vm-recommendations

# Case Study

https://cloud.google.com/learn/certification/guides/professional-cloud-architect

- EHR Healthcare
- Helicopter Racing League
- Mountkirk Games
- TerramEarth
