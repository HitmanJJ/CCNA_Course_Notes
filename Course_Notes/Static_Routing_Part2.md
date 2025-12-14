# 11. Static Routing: Part 2

## Review

- Switches forward traffic w/in LANs
- Routers forward traffic between LAN's
- **WAN (Wide Area Network)**: Network spread over a large area


### Connected and Local Routes

#### Configuring router ```R2``` (from part-1's example):

![image](https://github.com/psaumur/CCNA/assets/106411237/e44ac71c-91e3-4963-85da-ac07e475b248)

#### Configuring router ```R3```:

![image](https://github.com/psaumur/CCNA/assets/106411237/289212da-6c94-44fb-a1e3-1c066b56d79c)

#### Configuring router ```R4```:

![image](https://github.com/psaumur/CCNA/assets/106411237/f8f7d58b-89b7-412c-9cf6-c038338e105d)

---

## Default Gateway (Default Router)

![image](https://github.com/psaumur/CCNA/assets/106411237/63611407-719e-46d3-8331-a18533616285)

---

## Static Routes

![image](https://github.com/psaumur/CCNA/assets/106411237/10135afa-ace6-47f1-aada-1b73f243589b)

### Static-Route Configuration

![image](https://github.com/psaumur/CCNA/assets/106411237/d375a428-e171-4212-9698-2f2589878884)

#### Setting the Next-Hop IP Address Based on Destination Network

```R1(config)#ip route {destination_network_ip_add} {destination_netmask} {next_hop_ip_add}```  
  
↑ This command tells ```R1``` that--to send data to _```{destination_network_ip_add}```_ w/ a netmask of _```{destination_netmask}```_--forward the packet to _```{next_hop_ip_add}```_

![image](https://github.com/psaumur/CCNA/assets/106411237/012f4134-2667-421b-9b36-f449faebf423)


![image](https://github.com/psaumur/CCNA/assets/106411237/0a3ed6cb-c414-4365-aef4-754b4b82483e)


![image](https://github.com/psaumur/CCNA/assets/106411237/4379f8fb-a366-4279-a31c-ff2ba3f6fdb8)

The Source and Destination IP Addresses remain the same as the packet moves between networks via routers. Only the Source and Destination MAC addresses will change at each hop.

![image](https://github.com/psaumur/CCNA/assets/106411237/6fed6489-c53c-404e-b794-b71c2e9b8e4f)

---

#### Static-Route Configuration w/ ```exit-interface```

```R2(config)#ip route {destination_network_ip_add} {destination_netmask} {interface_name}```  
  
↑ This command tells ```R2``` that--to send data to _```{destination_network_ip_add}```_ w/ a netmask of _```{destination_netmask}```_--forward the packet out of the interface named _```{interface_name}```_

A next-hop and exit-interface can be specified together:

```R2(config)#ip route {destination_network_ip_add} {destination_netmask} {interface_name} {next_hop_ip_add}```  

![image](https://github.com/psaumur/CCNA/assets/106411237/dc93b5f9-791c-44fc-8b88-2053491183a9)

---

## Default Route

- **Default Route:** a network configuration that specifies the path for forwarding packets when no more specific route matches the destination IP address
  - Common default route is: ```0.0.0.0/0``` for IPv4, or ```::/0``` for IPv6
    - The least specific route possible--it includes every possible destination IP address 
    - For IPv6, the **unspecified address** is: ```0:0:0:0:0:0:0:0```, or ```::``` for short
- Configuration command: ```R1(config)#ip route 0.0.0.0 0.0.0.0 {destination_ip_add}```

![image](https://github.com/psaumur/CCNA/assets/106411237/a0eef93a-b40b-409b-8b51-6cdbace4ff45)
