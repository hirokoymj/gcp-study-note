# VPC networking

## Example 1

| Name        | Zone           | Internal IP | External IP    | Network   |
| ----------- | -------------- | ----------- | -------------- | --------- |
| mynet-us-vm | us-central1-c  | 10.132.0.2  | 104.199.77.240 | mynetwork |
| mynet-eu-vm | europe-west1-c | 10.128.0.2  | 34.67.18.18    | mynetwork |

**Open SSH on mynet-us-vm**

```js
student-00-b76f433189bd@mynet-us-vm:~$ ping -c 3 10.132.0.2
PING 10.132.0.2 (10.132.0.2) 56(84) bytes of data.
64 bytes from 10.132.0.2: icmp_seq=1 ttl=64 time=105 ms
64 bytes from 10.132.0.2: icmp_seq=2 ttl=64 time=103 ms
64 bytes from 10.132.0.2: icmp_seq=3 ttl=64 time=103 ms

--- 10.132.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 102.743/103.339/104.522/0.836 ms


student-00-b76f433189bd@mynet-us-vm:~$ ping -c 3 35.187.168.172
PING 35.187.168.172 (35.187.168.172) 56(84) bytes of data.
64 bytes from 35.187.168.172: icmp_seq=1 ttl=53 time=105 ms
64 bytes from 35.187.168.172: icmp_seq=2 ttl=53 time=103 ms
64 bytes from 35.187.168.172: icmp_seq=3 ttl=53 time=103 ms

--- 35.187.168.172 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 102.883/103.471/104.610/0.805 ms
```

```js
// Try ping using the instance name
ping -c 3 mynet-eu-vm
64 bytes from mynet-eu-vm.c.qwiklabs.gcp-95cc58a3f1725472.internal (10.132.0.2) : icmp_seq=1 ttl=64 time=103 ms
64 bytes from mynet-eu-vm.c.qwiklabs.gcp-95cc58a3f1725472.internal (10.132.0.2) : icmp_seq=2 ttl=64 time=103 ms
64 bytes from mynet-eu-vm.c.qwiklabs.gcp-95cc58a3f1725472.internal (10.132.0.2) : icmp_seq=3 ttl=64 time=103 ms

--- mynet-eu-vm.c.qwiklabs.gcp-95cc58a3f1725472.internal ping statistics ---
3 packets transmitted, 3 received, 0%, packet loss, time 2002ms
```

**Open SSH on mynet-eu-vm**

```js
ping -c 10.128.0.2
// ping works

ping -c 34.67.18.18
// ping works
```

> Note: You can SSH because of the allow-ssh firewall rule, which allows incoming traffic from anywhere (0.0.0.0/0) for tcp:22. The SSH connection works seamlessly because Compute Engine generates an SSH key for you and stores it in one of the following locations:
> By default, Compute Engine adds the generated key to project or instance metadata.
> If your account is configured to use OS Login, Compute Engine stores the generated key with your user account.
> Alternatively, you can control access to Linux instances by creating SSH keys and editing public SSH key metadata.

> Note: You can SSH to mynet-us-vm and ping mynet-eu-vm's internal and external IP addresses as expected. Alternatively, you can SSH to mynet-eu-vm and ping mynet-us-vm's internal and external IP addresses, which also works.

## Quiz

Which firewall rule allows the ping to mynet-eu-vm's external IP address?

1. mynetwork-allow-ssh
2. mynetwork-allow-rdp
3. mynetwork-allow-custom
4. mynetwork-allow-icmp (a)

## Answer

- mynetwork-allow-icmp
- https://cloud.google.com/vpc/docs/firewalls

| Rule name          | Direction | Priority | Source ranges | Action | Protocols and ports | Description                      |
| ------------------ | --------- | -------- | ------------- | ------ | ------------------- | -------------------------------- |
| default-allow-icmp | ingress   | 65534    | 0.0.0.0/0     | allow  | icmp                | Lets you use tools such as ping. |

mynetwork 22 1460 Custom
None

Note: Converting an auto mode network to a custom mode network is an easy task, and it provides you with more flexibility. We recommend that you use custom mode networks in production.
