# Shared VPC

https://www.youtube.com/watch?v=2qSUTrdEnbo

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
