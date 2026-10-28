## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
<img width="1919" height="1079" alt="Screenshot 2026-10-28 185118" src="https://github.com/user-attachments/assets/3ef9e812-9034-442f-8395-c58f3ffe27cf" />

<img width="1919" height="1079" alt="Screenshot 2026-10-28 185125" src="https://github.com/user-attachments/assets/9688a9cf-7493-4837-acc6-ee1699feab49" />


•	PC IP settings<br>
<img width="1905" height="1076" alt="image" src="https://github.com/user-attachments/assets/d68b15d6-78aa-403d-bc3c-b141333dcea5" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2fa8d771-9672-4d3e-8d9b-f8f72ae09761" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e2036898-a178-483e-b46b-248e04f31953" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8afa9355-ba22-42fb-a9a6-943542918f32" />





•	Successful ping between PCs in the same VLAN<br>
<img width="1919" height="1079" alt="Screenshot 2026-10-28 184826" src="https://github.com/user-attachments/assets/db282e05-166e-44d7-878f-168ee0ed7cad" />


•	Failed ping between PCs in different VLANs<br>
<img width="1919" height="1079" alt="Screenshot 2026-10-28 184909" src="https://github.com/user-attachments/assets/8c433fec-3799-408a-9c51-14073b664a01" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

