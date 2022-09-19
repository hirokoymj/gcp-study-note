# Expand a subnet (Demo)

### Four reserved addresses

- the first and second addresses in the range 0, 1 -> reserved for the network and subnetwork's gateway.
- second-to-last: broadcast address
- /29
- 29/8=3...5
- 1111100 -> 128, 64, 32, 16, 8, 4, 4, 2, 1
- 128+64+32+16+8=248
- /29 ==> **248**

### Available ips for /29

- 256-248=8
- 8-4 = **4**

## Demo

1. /29 mask provides you with 8 addresses but 4 are reserved(first two and last two ips ) and 4 VM instances already created.
2. Created 5th instance and it failed.
3. Extend a subnet from /29 to /23 in Subnet details page
4. Then created 5th instance again and it was done successfully.
5. Note that a subnet can extend **WITHOUT** stopping currently running the instances.
