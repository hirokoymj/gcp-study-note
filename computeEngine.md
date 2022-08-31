# Compute Engine

1. Creating GCE instance
2. Image in GCP
3. Persistent disk

## What is Compute Engine?

https://cloud.google.com/compute

## Create a GCE instance

1. Create a new project
2. Enable the Compute Engine API
3. Compute Engine -> VM instances
4. Add an instance name(lower case)
5. Region and zone
6. Select the hardware configuration - machine types
7. boot disk image. It contains a root file system and OS that will run on your instances.
8. Firewall - HTTP/HTTPS
9. Management, security, Network
10. Hit Create

**Choose machine types**

- Standard machine type
- High memory machine type
- High-CPU machine type
- Shared-core machine typ

**Boot Disk**

- A root persistent disk for instances
- It contains a root file system and OS that will run on your instances.

![image](./compupte-engine/gce1-region.PNG)
![image](./compupte-engine/gce2-machine-type.PNG)
![image](./compupte-engine/gce3-1-boot-disk-change.PNG)
![image](./compupte-engine/gce3-2-boot-disk.PNG)
![image](./compupte-engine/gce4-firewall.PNG)
![image](./compupte-engine/gce5-detail.PNG)
![image](./compupte-engine/gce5-1-network.PNG)
![image](./compupte-engine/gce5-2-network-2.PNG)
![image](./compupte-engine/gce5-3-security.PNG)
![image](./compupte-engine/region-zones.PNG)

<hr />

# Images in GCP

**Requirements/situations**

- In some situations, your applications might require you to build your own operating system or compile a custom kernel.
- Custom images are ideal for situations where you have created and modified a persistent boot disk or specific image to a certain state and need to save that state for creating VMs
- Solution - Use custom images for running a customized virtual
  machine

**2 Types**

- Public images are provided and maintained by Google, open source communities, and third-party vendors. By default, all Google Cloud projects have access to these images and can use them to create instances.
- Custom images are available only to your Cloud project. You can create a custom image from boot disks and other images. Then, use the custom image to create an instance.

![image](./compupte-engine/custom-image2.PNG)

**References:**

- https://cloud.google.com/compute/docs/images
- https://cloud.google.com/compute/docs/images/building-custom-os

# Persistent disk

- Persistent disk is high performance solid state and hard disk drive block storage that can be attached to instances running in Compute Engine or Kubernetes Engine.
- Standard persistent disk - HDD - low cost and best suited for large data

```js
gcloud compute disks create [DISK-Name] --size [size] --type [disk-type]
gcloud compute instances attach-disk [instance-name] ---disk [disk name]
```

- On the security front, persistent disks are automatically encrypted to protect your data.

## gcloud compute disks create

1. Use the gcloud compute disks create command to create the zonal persistent disk.

```js
gcloud compute disks create DISK_NAME \
  --size DISK_SIZE \
  --type DISK_TYPE
//or
gcloud compute disks create my-disk-1 my-disk-2 --zone=us-east1-a
```

2. After you create the disk, attach it to any running or stopped instance. Use the gcloud compute instances attach-disk command:

```js
gcloud compute instances attach-disk INSTANCE_NAME \
  --disk DISK_NAME
```

3. After you create and attach the new disk to a VM, you must format and mount the disk, so that the operating system can use the available storage space.

## Formatting the disk

1. List the disks

```js
  sudo lsblk
```

2. Format the disk using the mkfs tool

```js
 sudo mkfs.ext4 -m 0 -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/DEVICE_NAME
```

## Mounting the disk

1. Create a directory that serves as the mount point for the new disk on the VM

```js
sudo mkdir -p /mnt/disks/MOUNT_DIR
```

2. Use the mount tool to mount the disk to the instance, and enable the discard option:

```js
sudo mount -o discard,defaults /dev/DEVICE_NAME /mnt/disks/MOUNT_DIR
```

3. Configure read and write permissions on the disk.

```js
sudo chmod a+w /mnt/disks/MOUNT_DIR
```

![image](./compupte-engine/persist-format.PNG)

<hr />

# Quiz

**Q1**

To ensure that your application will handle the load even if an entire zone fails, what should you do?

1. Using Custom Images from GCP(correct)
2. Using Google Cloud Storage
3. Using Compute Engine (wrong)
4. Using Container Image (wrong)

> (#1) You can create a custom image from boot disks and other images and then, use it to create an instance
> (#2) Cloud Storage is a simple storage service to store data.
> (#3) Compute Engine delivers configurable virtual machines running in Google's data centers
> (#4) Container image is created by taking an operating system base image, and adding packages, libraries, and binaries needed for your application, built to deploy containers.

<hr />

**Q2**

You have a persistent disk which has static files for read only purpose. You want to make these files available for three different web applications running on three different GCP VM instances. Is it possible to share the persistent disk with all the three instances?

1. No. You cannot share the persistent disk with multiple VM instances
2. Yes. You can share the persistent disk with multiple VM instances since the files are read only
3. No. You cannot share the persistent disk with multiple VM instances
4. Yes. You can share the persistent disk with multiple VM instances if the disk is in read-only mode (correct)

```text
https://cloud.google.com/compute/docs/disks/sharing-disks-between-vms

- Share a disk in read-only mode between multiple VMs
- You can attach a non-boot persistent disk to more than one VM in read-only mode
```

<hr />

**Q3**
Your website administrator deployed a full-fledged LAMP stack instance in GCP and also updated the GCE instance with required utilities and configuration changes. Now he want the entire project team to use servers having the identical configuration for deploying their applications. Which among the given options can be used for this purpose?

1. GCP does not have the option to get an Image of an instance
2. Create snapshot of the instance
3. Create Private image of the instance
4. Create Public image of the instance (correct)

> You can share your custom images publicly with authenticated Compute Engine users

<hr />

References:

- [Create a Linux VM instance in Compute Engine](https://cloud.google.com/compute/docs/create-linux-vm-instance)
- https://cloud.google.com/compute/docs/disks/add-persistent-disk#gcloud
- https://cloud.google.com/persistent-disk
- https://www.youtube.com/watch?v=zovhVfou-DI
