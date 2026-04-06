##### Link: [Intro to LAN](https://tryhackme.com/room/introtolan)
---
##### Task 1: Introducing LAN Topologies
1. What does LAN stand for?
	- `Local Area Network`
2. What is the verb given to the job that Routers perform?
	- `Routing`
3. What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?
	- `Switch`
4. What topology is cost-efficient to set up?
	- `Bus Topology`
5. What topology is expensive to set up and maintain?
	- `Star Topology`
6. Complete the interactive lab attached to this task. What is the flag given at the end?
	- Ring topology weakness: Cut the cable
		- ![](../../../Attachment/Pasted%20image%2020260406202248.png)
	- Bus topology weakness: Overwhelm network with traffic
		- ![](../../../Attachment/Pasted%20image%2020260406202318.png)
	- Star topology weakness: Disable the switch by smashing it
		- ![](../../../Attachment/Pasted%20image%2020260406202345.png)
	- Flag: `THM{TOPOLOGY_FLAWS}`
---
##### Task 2: A Primer on Subnetting
1. What is the technical term for dividing a network up into smaller pieces?
	- `Subnetting`
2. How many bits are in a subnet mask?
	- `32`
3. What is the range of a section (octet) of a subnet mask?
	- `0-255`
4. What address is used to identify the start of a network?
	- `Network Address`
5. What address is used to identify devices within a network?
	- `Host Address`
6. What is the name used to identify the device responsible for sending data to another network?
	- `Default Gateway`
---
##### Task 3: ARP
1. What does ARP stand for?
	- `Address Resolution Protocol`
2. What category of ARP Packet asks a device whether or not it has a specific IP address?
	- `Request`
3. What address is used as a physical identifier for a device on a network?
	- `MAC Address`
4. What address is used as a logical identifier for a device on a network?
	- `IP Address`
---
##### Task 4: DHCP
1. What type of DHCP packet is used by a device to retrieve an IP address?
	- `DHCP Discover`
2. What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?
	- `DHCP Request`
3. Finally, **what is the last** DHCP packet that is sent to a device from a DHCP server?
	- `DHCP ACK`
---
##### Task 5: Continue Your Learning: OSI Model
1. Join the "OSI Model" room.
	- `No answer needed`
---
