## Virtual Router Implementation - ARP, ICMP, and RIP

### Overview

This project is a part of Lab 3 for CS640 Fall 2022 at the University of Wisconsin - Madison. The objective of this lab is to enhance a virtual router by implementing support for ARP, ICMP, and RIP protocols. The modifications will enable the virtual router to generate and respond to ICMP messages, dynamically populate the ARP cache, and build a routing table using distance vector routing.

### Learning Outcomes

- Write code that constructs and deconstructs packets containing multiple layers of protocols.
- Explain how the Address Resolution Protocol (ARP) and distance vector (DV) routing work.

### Project Structure

- **src/**: Contains all the Java source files for the virtual switch and router.
- **README**: This file.

### Part 1: Getting Started

1. Use the same environment and code base as Lab 2.
2. Create a copy of your entire Lab 2 directory and name it Lab 3:
   ```
   cp -r ~/lab2 ~/lab3
   ```

### Part 2: Implement ICMP

You need to add support for generating and responding to the following ICMP messages:

1. **Time Exceeded**: Sent when the TTL field of a packet is zero.
2. **Destination Net Unreachable**: Sent if there is no matching entry in the route table.
3. **Destination Host Unreachable**: Sent if the MAC address cannot be resolved using ARP.
4. **Destination Port Unreachable**: Sent if the router receives a TCP or UDP packet destined for one of its interfaces.
5. **Echo Reply**: Sent in response to an ICMP echo request (ping).

### Part 3: Implement ARP

You need to implement ARP to dynamically populate the ARP cache.

1. **ARP Replies**: Generate ARP replies in response to received ARP requests.
2. **ARP Requests**: Generate ARP requests and handle the queueing of packets while waiting for a reply.
3. **Receive ARP Replies**: Update the ARP cache and process queued packets upon receiving ARP replies.

### Part 4: Implement RIP

You need to implement distance vector routing to dynamically build and update the router's route table using the RIP protocol.

1. **Starting RIP**: Add entries for directly reachable subnets and send RIP requests and responses.
2. **RIP Packets**: Encapsulate RIP packets in UDP packets with source and destination ports set to 520.
3. **RIP Operation**: Send RIP requests on initialization and unsolicited RIP responses every 10 seconds.
4. **RIP Timeout**: Time out route table entries that haven't been updated for more than 30 seconds.

### Submission Instructions

You must submit a single tar file containing the `src` directory with the Java source files for your virtual switch and router. To create the tar file, run the following command, replacing `username1` and `username2` with the CS username of each group member:
```
tar czvf username1_username2.tgz src
```
or
```
tar czvf username1.tgz src
```

Upload the tar file to the Lab3 tab on the course's Canvas page.

### References

- [ICMP Protocol](http://www.networksorcery.com/enp/protocol/icmp.htm)
- [ARP Protocol](http://www.networksorcery.com/enp/protocol/arp.htm)
- [RIP Protocol](http://www.networksorcery.com/enp/protocol/rip.htm)
- [RFC2453 - RIPv2](https://datatracker.ietf.org/doc/html/rfc2453)

### Assumptions

- The virtual router environment is set up correctly according to the instructions provided.
- The router's initial setup and basic packet forwarding functionality are working as expected from Lab 2.
