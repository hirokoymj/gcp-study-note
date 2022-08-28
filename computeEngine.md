# Compute Engine

## Virtual machine instances

An instance is a virtual machine (VM) hosted on Google's infrastructure. You can create an instance or create a group of managed instances by using the Google Cloud console, the Google Cloud CLI, or the **Compute Engine API**.

### Introduction

- Compute Engine instances can run the public images for Linux and Windows Server that Google provides.
- You can also deploy Docker containers, which are automatically launched on instances running the Container-Optimized OS public image.
- You can choose the machine properties of your instances, such as the number of virtual **CPUs** and the amount of **memory**

### Instances and projects

Each instance belongs to a Google Cloud console **project**, and a project can have one or more instances. When you create an instance in a project, you specify the **zone**, **operating system**, and machine type of that instance. When you delete an instance, it is removed from the project.

### Instances and storage options

By default, each Compute Engine instance has a small boot persistent disk that contains the operating system.

### Instances and networks

- Each network interface of a Compute Engine instance is associated with a subnet of a unique VPC network.

## Instance groups

- Compute Engine offers two kinds of VM instance groups, **managed** and **unmanaged**:
- A instance group is a collection of VM instances and it used to perform health checking and scaling across groups of Compute Engine instances.

### Managed instance groups

- **Auto scaling**
- **Auto healing**
- regional (multiple zone) deployment
- Instance template
- 2 types - zonal managed instance and Regional managed instance

### Unmanaged instance groups

- Do not offer AutoScaling
- No support instance template

## HOW TO CREATE INSTANCE GROUPS IN COMPUTE ENGINE?

### What is Instance Group?

Instance group is nothing but a group of virtual machine instances managed as a single entity. You can manage groups of similar VMs having a similar life cycle as one unit and you can create two types of Instance group in Compute Engine.

- Managed instance group
- Unmanaged Instance group

Instance group is the basis for Autoscaling group, Load balancers and Autohealing.

**References:**

- https://cloud.google.com/compute/docs/instances
- https://cloud.google.com/compute/docs/instance-groups
- https://www.easydeploy.io/blog/how-to-create-instance-groups-in-compute-engine/
