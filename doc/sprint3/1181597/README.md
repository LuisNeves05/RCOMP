RCOMP 2020-2021 Project - Sprint 2 - Member 1181597 folder
===========================================
(This folder is to be created/edited by the team member 1181597 only)

# Building 2 #

## Technical decisions ##

### VLAN devices configuration ###
**VLAN IDs to be used: 328 , 330 , 331 , 341 , 345**

* 
* VLAN for all end-user outlets on the ground floor: 331
* VLAN for all end-user outlets on floor one of the building: 330
* VLAN for the Wi-Fi network (for all access-points’ outlets within the building): 328
* VLAN for the building DMZ(for servers,administration workstations,and industrial machines): 345
* VLAN for VoIP (for IP-phones): 341


#### End user outlets on the ground floor: 6 nodes ####
* Network in CIDR notation: 10.126.116.0/26
* Network’s first valid node address: 10.126.116.1
* Network’s last valid node address:  10.126.116.62
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192
* Broadcast address: 10.126.116.63

#### End user outlets on floor one: 70 nodes ####
* Network in CIDR notation: 10.126.115.128/25
* Network’s first valid node address: 10.126.115.129
* Network’s last valid node address:  10.126.115.254
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1000 0000) = 255.255.255.128
* Broadcast address: 10.126.115.255

#### Wi-Fi network: 100 nodes ####
* Network in CIDR notation: 10.126.114.128/25
* Network’s first valid node address: 10.126.114.129
* Network’s last valid node address: 110.126.114.254
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1000 0000) = 255.255.255.128  
* Broadcast address: 110.126.114.255

#### Local servers, administration workstations, and machines (DMZ): 12 nodes ####
* Network in CIDR notation: 10.126.119.32/28
* Network’s first valid node address: 10.126.119.33
* Network’s last valid node address: 10.126.119.47
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1111 0000) = 255.255.255.240
* Broadcast address: 10.126.119.48

#### VoIP (IP-phones): 35 nodes ####
* Network in CIDR notation: 10.126.118.128/26
* Network’s first valid node address: 10.126.118.129
* Network’s last valid node address: 10.126.118.190
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192  
* Broadcast address: 10.126.118.191

### Trunking and Access between layer 2 devices and end users ###
With all the switches defined as client or server, we now had access to the defined VLANs in every switch. As so, depending on the end user type, the Fast Ethernet cord was configured into Access mode and selected the correct VLAN for the end device.

Furthermore, between switches, to ensure that every switch knew every VLAN available, the connection between them was in trunk mode.
### Access Point Channels ###

Taking into consideration that **Building 3** had **3** total Access Points, different channels had to be configured for the 2.4Ghz port.
As so, the first AP was assigned with channel **number 1**, the second with **number 6** and the last with **number 9**

To ensure correct connection from the AP to the Wireless Laptops, the APs were organized and distributed acordingly on the Physical part of the project

## CLI commands ##
### OSPF dynamic routing ###
* router ospf 1
* log-adjacency-changes
* network 10.126.116.0 0.0.0.63 area 2
*  network 10.126.115.128 0.0.0.127 area 2
*  network 10.126.114.128 0.0.0.127 area 2
*  network 10.126.119.32 0.0.0.15 area 2
*  network 10.126.118.128 0.0.0.63 area 2

### DHCPv4 service ###
* ip dhcp pool B2_DMZ_12N
* network 10.126.119.32 255.255.255.240
* default-router 10.126.119.33
* dns-server 10.126.119.42
-----------------------------------------
* ip dhcp pool B2_END_USER_F0_60N
* network 10.126.116.0 255.255.255.192
* default-router 10.126.116.1
* dns-server 10.126.119.42
-----------------------------------------
* ip dhcp pool B2_END_USER_F1_70N
* network 10.126.115.128 255.255.255.128
* default-router 10.126.115.129
* dns-server 10.126.119.42
 ----------------------------------------- 
* ip dhcp pool B2_WiFi_100N
* network 10.126.114.128 255.255.255.128
* default-router 10.126.114.129
* dns-server 10.126.119.42
-----------------------------------------
* ip dhcp pool B2_VoIP_35N
* network 10.126.118.128 255.255.255.192
* default-router 10.126.118.129
* option 150 ip 10.126.118.129
* dns-server 10.126.119.42
-----------------------------------------

**Excluded addresses**
* ip dhcp excluded-address 10.126.116.1
* ip dhcp excluded-address 10.126.115.129
* ip dhcp excluded-address 10.126.114.129
* ip dhcp excluded-address 10.126.118.129
* ip dhcp excluded-address 10.126.119.41
* ip dhcp excluded-address 10.126.119.42
* ip dhcp excluded-address 10.126.114.1
* ip dhcp excluded-address 10.126.119.33

### DNS ###

![DNS.png](DNS.PNG)

### NAT ###

* interface FastEthernet0/0
* ip address 10.126.114.1 255.255.255.128
* ip nat outside

---------------------------
* interface FastEthernet0/0.5
* encapsulation dot1Q 345
* ip address 10.126.119.33 255.255.255.240
* ip nat inside
------------------------------------
* router rip
* !
*  ip nat inside source static tcp 10.126.119.41 80 10.126.114.1 80
*  ip nat inside source static tcp 10.126.119.41 443 10.126.114.1 443
*  ip nat inside source static tcp 10.126.119.42 53 10.126.114.1 53
*  ip nat inside source static udp 10.126.119.42 53 10.126.114.1 53

### VOIP CONFIGURATIONS ###

**Consolidation_Point_1.1**
* interface FastEthernet3/1
* switchport mode access
* switchport voice vlan 341

**Consolidation_Point_2.1**
* interface FastEthernet3/1
* switchport mode access
* switchport voice vlan 341

--------------------------
* dial-peer voice 1 voip
* destination-pattern 200..
* session target ipv4:10.126.118.129


* dial-peer voice 2 voip
* destination-pattern 300..
* session target ipv4:10.126.118.1

* dial-peer voice 3 voip
* destination-pattern 400..
* session target ipv4:10.126.118.222


* dial-peer voice 4 voip
* destination-pattern 100..
* session target ipv4:10.126.119.10

--------------
**telephony-service**
* max-ephones 2
* max-dn 20
* ip source-address 10.126.118.129 port 2000
* auto assign 1 to 2
* auto assign 1 to 20


* ephone-dn 1
* number 20001


* ephone-dn 2
* number 20002

* ephone 1
* device-security-mode none
* mac-address 00E0.F7DE.6777
* type 7960
* button 1:1


* ephone 2
* device-security-mode none
* mac-address 00E0.F704.EC06
* type 7960
* button 1:2
-----------------
### Servers ###
**DNS**
* 10.126.119.42
  
**HTTP**
* 10.126.119.41