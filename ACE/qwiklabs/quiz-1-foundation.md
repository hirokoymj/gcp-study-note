# Quiz: Interacting with Google Cloud

# Quiz: Virtual Networks

Your score: 66%, 100%

Q: What is one benefit of applying firewall rules by tag rather than by address?

- Tags on firewall rules control which ephemeral IP addresses VMs will receive.X
- Tags help organizations track firewall billing.
- When a VM is created with a matching tag, the firewall rules apply irrespective of the IP address it is assigned.\*\*
- Tags in network traffic help with network sniffing.X

Answer:

> When a VM is created the ephemeral external IP address is assigned from a pool. There is no way to predict which address will be assigned, so there is no way to write a rule that will match that VM's IP address before it is assigned. Tags allow a symbolic assignment that does not depend on order in the IP addresses. It makes for simpler, more general, and easier to maintain, firewall rules.

# Quiz: Virtual Machines

- Your score: 66%, 100%

Q: Which statement is true of persistent disks?

- Persistent disks are always HDDs (magnetic spinning disks).
- Once created, a persistent disk cannot be resized.
- Persistent disks are physical hardware devices connected directly to VMs. X
- Persistent disks are encrypted by default.\*\*

> Persistent Disks are not physical disks, they are a virtual-networked service. Each persistent disk remains encrypted either with system-defined keys or with customer-supplied keys.
