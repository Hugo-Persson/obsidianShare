1. What is the purpose of an ARP request?  
	Converting IP-adress to MAC adress 
2. What layer is ARP operating on?  
	Between 2 and 3
3. Does ARP use IP headers?  
	1. No
4. When a packet needs to be transmitted to a host on another subnet, what IP address will be used in the destination field of the IP header?  
	1. The recipients IP-adress
5. When a packet needs to be transmitted to a host on another subnet, what MAC address will be used in the destination field of the MAC header?  
	6. The default gateway
6. What MAC destination address is an ARP request ALWAYS sent to?  
	1. Broadcast, FF:FF...
7. What MAC destination address is an ARP reply sent to?  
	1. The MAC of the terminal that sent the ARP request
8. Exactly what information does an ARP request contain?  
	1. ![](https://i.imgur.com/nReHXnH.png)
9. Exactly what information does an ARP reply contain?  
	1. ![](https://i.imgur.com/nReHXnH.png)

10. What is the purpose of a DNS request?  
	1. To translate a domain like google.com to IP
11. When a DNS request is sent to a DNS server on another subnet, what IP destination address will be used in the IP header?  
	1. The DNS servers IP-adress
12. When a DNS reply is sent by a DNS server to host on another subnet, what IP destination address will be used in the IP header?  
	1. The host that sent the request
13. When a DNS reply is sent by a DNS server to a host on another subnet, what MAC destination address will be used in the MAC header?  
	1. The default gateway of the subnet DNS server is or the router that sent the message to the DNS server
14. What is the difference between a hub, a switch, and a router?  
	1. Hub outputs incoming frame on all ports except the port the frame came from
	2. Switch handlesEthernett frames and has a MAC table to decide what port a frame should be sent out of. If the switch has no info about the remote its mac table then it acts as an hub
	3. A router works on layer 3 and intelligently routes IP packages over the network
15. When a switch relays a packet, how will the destination MAC address be affected?  
	1. It will not be changed
16. When a router relays a packet, how will the destination MAC address be affected?  
	It will be changed to the next router in the path or the MAC of the recipient is on the local network
17. When a switch relays a packet, how will the destination IP address be affected?  
	1. It will not be changed
18. When a router relays a packet, how will the destination IP address be affected?  
	1. It will not changed
19. Describe the classful addressing method.  
	1. We have predefined routing blocks
	2. ![Pasted image 20221116172116.png]({{< ref "Pasted image 20221116172116.png" >}})
20. Describe the classless addressing method
	1. In classless we use netmasks to defined what part of IP adress is net and what part 