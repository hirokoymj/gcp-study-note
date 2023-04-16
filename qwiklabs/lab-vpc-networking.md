# Lab:VPC Networking

## Take1. Explore the default network

## Take2. Create an auto mode network

## Take3. Create custom mode networks

## Take4. Explore the connectivity accross networks

## Take5. Review

1. Delete the FW
2. Delete the default
3. Create auto mode VPC

   - mynetwork
   - automatic
   - Click all FW

4. Create VM in us-central1

   - name: mynet-us-vm
   - Region: us-central1
   - Zone: us-central1-c
   - Series: N1
   - Machine type n1-standard
   - Boot disk Devian GNU/Linux 10

5. Create a v, in europe-west1

   - mynet-eu-vm
   - europe-west1
   - europe-west1-c
   - N1
   - n1-standard-1
   - Devian GNU/Linux 10
   - FW Checked Allow HTTP trafic/ Allow HTTPS traffic

6. VPC-> mynetwork -> Edit -> Change auto to custom

7. Create the management network

   - VPC -> Name: management -> Subnet creation mode Custom,
   - Name: managementsubnet-us
   - Region: us-central1
   - IPv4 range: 10.130.0.0/20

8. Create the privatenet network

- To create the **privatenet** network.

```
gcloud compute networks create privatenet --subnet-mode=custom
```

- To create the **privatesubnet-us** subnet, run the following command.

```
gcloud compute networks subnets create privatesubnet-us --network=privatenet --region=us-central1 --range=172.16.0.0/24
```

- To create the **privatesubnet-eu** subnet, run the following command

```
gcloud compute networks subnets create privatesusnet-eu --network=privatenet --region=europe-west1 --range=172.20.0.0/20
```

```
gcloud compute networks list
```

https://www.youtube.com/watch?v=0UOu5XZlucg&t=245s

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
