# Network Layer

The Network layer determines the routing of our packets from our source host to a destination host. Fortunately in our example, our packet is only traveling within the same network, but the Internet is made up of many networks. These smaller networks that make up the Internet are known as subnets. All subnets connect to each other in some way, which is why we are able to get to www.google.com even though it's on its own network. I won't go into detail as we have a whole course dedicated to subnets, but for now in regards to our Network layer, know that the IP addresses define the rules to travel to different subnets. 

In the network layer, it receives the segment coming from the transport layer and encapsulates this segment in an IP packet then attaches the IP address of the source host and the IP address of the destination host to the packet header. So at this point, our packet has information about where it is going and where it came from. Now it sends our packet to the physical hardware layer.

## Quiz Questions 

Click the right arrow to view the answers

<details>
<summary>What are smaller networks that make up the Internet called?</summary>
subnets
</details>
