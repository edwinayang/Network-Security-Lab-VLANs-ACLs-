# Network-Security-Lab-VLANs-ACLs-

This project simulates a secure enterprise network using Cisco Packet Tracer.
It focuses on implementing Access Control Lists (ACLs) to control traffic between departments.

The lab demonstrates how to restrict communication while maintaining necessary access, similar to real-world network security policies.

## Topology ##
Vlans (2).jpg
acl.jpg
ipinterfaces.jpg
ping-failed.jpg
ping-success.jpg
topology.jpg

##Network Design##

VLAN & Department Mapping
VLAN	Department	Network	Gateway
10	Admin	192.168.10.0/24	192.168.10.1
20	HR	192.168.20.0/24	192.168.20.1
30	IT	192.168.30.0/24	192.168.30.1
⚙️ Technologies Used
Cisco Packet Tracer
VLANs (10, 20, 30)
802.1Q Trunking
Router-on-a-Stick
Access Control Lists (ACLs)
Network Troubleshooting

ACL Security Implementation

An extended ACL was configured to enforce security policies between departments.

 Security Policy
 
HR (VLAN 20) cannot initiate ping to IT (VLAN 30)
IT (VLAN 30) can ping HR (VLAN 20)
Admin (VLAN 10) has full access to all networks

 ACL Configuration
 
access-list 100 deny icmp 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255 echo
access-list 100 permit icmp 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255 echo-reply
access-list 100 permit ip any any

interface g0/0.20
ip access-group 100 in

## Verification ##
Test Results
Source	Destination	Result
HR → IT	192.168.30.x	 Blocked
IT → HR	192.168.20.x	 Allowed
Admin → HR	192.168.20.x	 Allowed
Admin → IT	192.168.30.x	 Allowed

#### Key Concepts Demonstrated ###
VLAN segmentation
Inter-VLAN routing
ACL traffic filtering
ICMP control (echo vs echo-reply)
Network security policy enforcement

##### What I Learned ###

How to design and apply ACLs for network security
How traffic flow affects communication (request vs reply)
How to control inter-department access in a network
How to troubleshoot ACL-related issues

### Future Improvements ###

Implement port-based ACLs (HTTP, SSH filtering)
Add NAT for internet simulation
Expand to multi-router security design
Implement advanced firewall features


Edwin Ayang
