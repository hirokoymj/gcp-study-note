# Lab:VPC Networking

[Lab:VPC Networking](https://www.cloudskillsboost.google/course_sessions/1685038/labs/314345)

![](images/vpc-1.png)

![](images/vpc-2.png)

> Note: You can ping the internal IP address of mynet-eu-vm because it is on the same VPC network as the source of the ping (mynet-us-vm), even though both VM instances are in separate zones, regions, and continents!

- they are in a different network does not allow me to ping on the internal IP, unless we set up other mechanisms such as VPC peering or a VPN.

- To test connectivity to managementnet-us-vm's internal IP,
  Note: This should not work, as indicated by a 100% packet loss!

- To test connectivity to privatenet-us-vm's internal IP

> Note: This should not work either, as indicated by a 100% packet loss! You cannot ping the internal IP address of managementnet-us-vm and privatenet-us-vm because they are in separate VPC networks from the source of the ping (mynet-us-vm), even though they are all in the same zone, us-central1-c.

Without a VPC network, you cannot create VM instances, containers, or App Engine applications.

```
gcloud compute networks create privatenet --subnet-mode=custom

gcloud compute networks subnets create privatesubnet-us --network=privatenet --region=us-central1 --range=172.16.0.0/24

gcloud compute networks subnets create privatesubnet-eu --network=privatenet --region=europe-west1 --range=172.20.0.0/20

gcloud compute networks list
gcloud compute networks subnets list --sort-by=NETWORK

gcloud compute instances create privatenet-us-vm --zone=us-central1-c --machine-type=f1-micro --subnet=privatesubnet-us --image-family=debian-10 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=privatenet-us-vm

gcloud compute instances list --sort-by=ZONE*
```
