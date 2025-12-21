# 12. Life of a Packet

## Network Topology

![image](https://github.com/psaumur/CCNA/assets/106411237/ec16b9fd-4d90-4b73-b930-cd825ff13b00)


Each interface on a network device has a unique MAC address.

In an IPv4 and IPv6 header, SOURCE IP ADDRESS comes before DESTINATION IP ADDRESS

while...

in an Ethernet header, DESTINATION MAC ADDRESS comes before SOURCE MAC ADDRESS

---

## Address Resolution Protocol (ARP)

- For this scenario, PC1 would like to communicate w/ PC4
-  PC1 sends an _**ARP Request**_ (containing source and destination addresses) to SW1, which broadcasts the request to all interfaces (except the interface it recieved the frame on)
- R1 sends an _**ARP Reply**_ to PC1 with its MAC address

![image](https://github.com/psaumur/CCNA/assets/106411237/5eb94811-32f3-47f6-884e-f45a71456e84)

- Now PC1 knows the MAC address of R1 (PC1's default gateway)
- PC1 encapsulates the packet w/ an Ethernet header
- The original packet in unchanged--only an Ethernet header (L2 header) is added
  - The destination IP address is still PC4's IP address
- PC1 sends the frame to R1

![image](https://github.com/psaumur/CCNA/assets/106411237/dc0d05cc-9b76-4921-895d-bfbe78ceb0a7)

- R1 recieves the frame, then removes the L2 header
- R1 looks up the destination IP in its routing table to find the next hop
- The routing table shows that the next hop is R2, but R1 doesn't know R2's MAC address
- R1 must send an **_ARP Request_** (via broadcast) to learn R2's MAC address

![image](https://github.com/psaumur/CCNA/assets/106411237/884f7113-21a9-407f-a38e-44489ae3b47e)

- R2 receives the **_ARP Request_**
- The destination IP address matches R2's own IP address on its `Gi0/0` interface
- R2 sends an **_ARP Reply_** to R1

![image](https://github.com/psaumur/CCNA/assets/106411237/36459aeb-e802-4347-b626-0c9cc168c624)

- Now, R1 knows R2's MAC address
- R1 encapsulates the packet w/ an Ethernet header
- The destination MAC address for the packet is now R2's MAC address
- R1 sends the frame to R2

![image](https://github.com/psaumur/CCNA/assets/106411237/163bfaf6-15c7-4f7d-9429-4c62a28f0292)

- R2 receives the frame, then removes the L2 header
-  

![image](https://github.com/psaumur/CCNA/assets/106411237/1f7e5683-00e6-4ce0-b52a-ca8fdb24c87b)


![image](https://github.com/psaumur/CCNA/assets/106411237/18d04c9d-3734-44e7-995d-b53ab3aaa2a1)


![image](https://github.com/psaumur/CCNA/assets/106411237/07c44007-a208-47a2-a0e8-ca289f86be75)


![image](https://github.com/psaumur/CCNA/assets/106411237/4bcbdba0-234a-4cfa-aa25-cbc3c3c061e1)


![image](https://github.com/psaumur/CCNA/assets/106411237/81c2e8ad-be55-487c-b9da-02540f70b0d9)


![image](https://github.com/psaumur/CCNA/assets/106411237/91cfe407-28b5-48e8-b5f8-a60b324e0706)


![image](https://github.com/psaumur/CCNA/assets/106411237/4bf8c10b-1240-4e7d-8db4-85ea5f3f619f)


![image](https://github.com/psaumur/CCNA/assets/106411237/f938e440-ebdb-444c-b4c7-705d8fd2a4e9)


![image](https://github.com/psaumur/CCNA/assets/106411237/1f236bda-d2cf-4252-af3b-bdc5ec5c2aca)


When a HOST sends a packet to another HOST, the SOURCE or DESTINATION IP doesn't change - even though ROUTERS may change the ETHERNET HEADER (SRC/DEST MAC ADDRESSES).
