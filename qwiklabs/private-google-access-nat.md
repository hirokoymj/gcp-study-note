# Private Google Access and Cloud Nat

### Task 1. Create the VM instance

1. Create a VPC network and firewall rules

> Note: In order to connect to your private instance using SSH, you need to open an appropriate port on the firewall. IAP connections come from a specific set of IP addresses (35.235.240.0/20). Therefore, you can limit the rule to this CIDR range.

2. Create the VM instance with no public IP address
3. SSH to vm-internal to test the IAP tunnel

> This should **not** work because vm-internal has no external IP address!

### Task 2. Enable Private Google Access

Create a Cloud Storage bucket
Copy an image file into your bucket
Access the image from your VM instance
This should work because Cloud Shell has an external IP address!

> This should not work: vm-internal can only send traffic within the VPC network because Private Google Access is disabled (by default).

Enable Private Google Access

> Note: Enabling Private Google Access is as simple as selecting On within the subnet!

### Task 3. Configure a Cloud NAT gateway

Try to update the VM instances
Configure a Cloud NAT gateway
Verify the Cloud NAT gateway

### Task 4. Configure and view logs with Cloud NAT Logging

Enabling logging
NAT logging in Cloud Operations
Generating logs
Viewing Logs

### Task 5. Review

<hr />

# Creating Virtual Machines

**Task 1. Create a utility virtual machine**

1. Create a VM

> Select None for External IP.

2. Explore the VM details

> Note: Notice that you cannot change the machine type, the CPU platform, or the zone.

> You can add network tags and allow specific network traffic from the internet through firewalls. Some properties of a VM are integral to the VM, are established when the VM is created, and cannot be changed. Other properties can be edited.

> You can add additional disks and you can also determine whether the boot disk is deleted when the instance is deleted.

> Normally the boot disk defaults to being deleted automatically when the instance is deleted. But sometimes you will want to override this behavior. This feature is very important because you cannot create an image from a boot disk when it is attached to a running instance.

> So you would need to disable Delete boot disk when instance is deleted to enable creating a system image from the boot disk.

> Note: You cannot convert a non-preemptible instance into a preemptible one. This choice must be made at VM creation. A preemptible instance can be interrupted at any time and is available at a lower cost.

> If a VM is stopped for any reason, (for example an outage or a hardware failure) the automatic restart feature will start it back up. Is this the behavior you want? Are your applications idempotent (written to handle a second startup properly)?

> During host maintenance, the VM is set for live migration. However, you can have the VM terminated instead of migrated.

> If you make changes, they can sometimes take several minutes to be implemented, especially if they involve networking changes like adding firewalls or changing the external IP.

3. Explore the VM logs

**Task 2. Create a Windows virtual machine**

1. Create a VM

| Property                         | Value                               |
| -------------------------------- | ----------------------------------- |
| Public Images > Operating system | Windows Server                      |
| Version                          | Windows Server 2016 Datacenter Core |

2. Set the password for the VM

> Note: When the VM is running, notice that the connection option in the far right column is RDP, not SSH. RDP is the Remote Desktop Protocol. You would need the RDP client installed on your local machine to connect to the Windows desktop.

> Note: You will not connect to the Windows VM during this lab. However, the process would look something like the following (depending on the RDP client you installed). The RDP client shown can be installed for Chrome from the Chrome webstore. On the VM instances page, you would click RDP for your Windows VM and connect with the password copied earlier.

**Task 3. Create a custom virtual machine**

| Property     | Value                 |
| ------------ | --------------------- |
| Machine type | Windows Server Custom |
