## Ex. No: 3  DHCP Configuration Using a Router
Date: 27/10/2026
________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
<img width="1915" height="1015" alt="Screenshot 2026-10-27 173749" src="https://github.com/user-attachments/assets/e09f009d-c36d-409e-b27c-9b2c7bde3d58" />

________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
•	DHCP IP configuration shown in PC0 and PC1<br>

<img width="957" height="577" alt="Screenshot 2026-10-27 174057" src="https://github.com/user-attachments/assets/6404b818-84e8-4fa0-8c59-66f12385201b" />

<img width="1846" height="811" alt="Screenshot 2026-10-27 174236" src="https://github.com/user-attachments/assets/387158db-f380-4a30-9559-e2a4d393bbc5" />

•	Router configuration screen<br>

<img width="1517" height="931" alt="Screenshot 2026-10-27 174946" src="https://github.com/user-attachments/assets/62135919-18d4-4839-a420-4c745d174768" />

•	Successful ping test between the two PCs<br>

<img width="1515" height="788" alt="Screenshot 2026-10-27 174631" src="https://github.com/user-attachments/assets/e36fa1dc-cd4d-4cac-8046-3dea02f2aa23" />

________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
