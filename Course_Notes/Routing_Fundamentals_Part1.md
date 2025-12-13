# 11. ROUTING FUNDAMENTALS : PART 1




### What Is Routing?



**Routing** is the process that routers use to determine the path that IP packets should take over a network to reach their destination.

- Routers store routes to all their known destinations in a **routing table**
- When routers receive packets, they look in the **routing table** to find the best route to forward that packet.

There are two main routing methods (methods that routers use to learn routes):

- **Dynamic Routing**: Routers use Dynamic-Routing Protocols (ie: OSPF) to share routing information with each other automatically and build their routing tables.
- **Static Routing**: A Network Engineer/Admin manually configures routes on the router.

A **route** tells the router:

- to send a packet to destination ```X```, you should send the pack to the **next hop** (the next router in the path to the destination) ```Y```
- or if the destination is directly connected to the router, *send the packet directly to the destination.*
- or if the destination is the router’s own IP address, *receive the packet for yourself (don’t forward it).*

![image](https://github.com/psaumur/CCNA/assets/106411237/8ceefb10-d70d-4530-969d-40347ed34297)


**WAN (Wide Area Network)**: network that extends over a large geographic area.

### Configuring IP Addresses on a Router

![image](https://github.com/psaumur/CCNA/assets/106411237/b3555fdd-37a4-4bc8-b998-76e0b5455bb1)

### Routing Tables
- To show the routing table for router ```R1```: ```R1#show ip route```
  - A Codes legend appears at the top of the result → lists the different protocols that routers can use to learn routes.
  - Routes appear at the bottom 

![image](https://github.com/psaumur/CCNA/assets/106411237/99e75230-de1c-4f48-acd0-3482bba256af)

### Connected and Local Routes
- A connected and local route will be added automatically to a routing table when an IP address is configured on a router interface, and the interface face is enabled with the ```no shutdown``` command
- **Connected route**: a route to the <ins>**network**</ins> the interface is connected to
  - Provides a route to all hosts in that network
- **Local route**: a route to the <ins>**exact IP address**</ins> configured on the interface
  - A ```/32``` netmask (subnet mask) is used to specify the exact IP address on the interface 

### Connected-Route Example
![image](https://github.com/psaumur/CCNA/assets/106411237/13a77d5c-497d-49ca-9717-ea3bb4a560d0)

---
### Route Selection

The line ```192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks```:
  - Not a route
  - In the routing table, there are 2 routes to subnets that fit w/in the ```192.168.1.0/24``` Class C network, w/ 2 different netmasks (```/24``` and ```/32```)

![image](https://github.com/psaumur/CCNA/assets/106411237/6e3a2b3b-1590-4625-9bcf-cdaed95738d2)


### Summary
![image](https://github.com/psaumur/CCNA/assets/106411237/891fcfbe-7dc5-4fb2-9b02-c6905236761e)
