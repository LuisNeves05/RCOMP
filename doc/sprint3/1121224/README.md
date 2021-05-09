RCOMP 2020-2021 Project - Sprint 3 - Member 1121224 folder
===========================================
(This folder is to be created/edited by the team member 1121224 only)

# Building 1 #

## Technical decisions ##

### VLAN devices configuration ###
**VLAN IDs to be used: 327, 329, 336,337, 343, 344**

* VLAN for backbone: 327
* VLAN for all end-user outlets on the ground floor: 336
* VLAN for all end-user outlets on floor one of the building: 337
* VLAN for the Wi-Fi network (for all access-points’ outlets within the building): 343
* VLAN for the building DMZ(for servers,administration workstations,and industrial machines): 329
* VLAN for VoIP (for IP-phones): 344

### Router IPv4 node address ###

* *10.126.114.2*


#### End user outlets on the ground floor: 40 nodes ####
* Network in CIDR notation: 10.126.117.64/26
* Network’s first valid node address: 10.126.117.65
* Network’s last valid node address:  10.126.117.126
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192  
* Broadcast address: 10.126.117.127

#### End user outlets on floor one: 40 nodes ####
* Network in CIDR notation: 10.126.117.128/26
* Network’s first valid node address: 10.126.117.129
* Network’s last valid node address:  10.126.117.190
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192
* Broadcast address: 10.126.117.191

#### Wi-Fi network: 24 nodes ####
* Network in CIDR notation: 10.126.118.224/27
* Network’s first valid node address: 10.126.118.225
* Network’s last valid node address: 10.126.118.254 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1110 0000) = 255.255.255.224  
* Broadcast address: 10.126.118.255

#### Local servers, administration workstations, and machines (DMZ): 70 nodes ####
* Network in CIDR notation: 10.126.115.0/25
* Network’s first valid node address: 10.126.115.1
* Network’s last valid node address: 10.126.115.126
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1000 0000) = 255.255.255.128
* Broadcast address: 10.126.115.127

#### VoIP (IP-phones): 20 nodes ####
* Network in CIDR notation: 10.126.119.0/27
* Network’s first valid node address: 10.126.119.1
* Network’s last valid node address: 10.126.119.30
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1110 0000) = 255.255.255.224  
* Broadcast address: 10.126.119.31

#### Backbone: 120 nodes ####
* Network in CIDR notation: 10.126.114.0/25
* Network’s first valid node address: 10.126.114.1
* Network’s last valid node address: 10.126.114.127 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1000 0000) = 255.255.255.128  
* Broadcast address: 10.126.114.127

## CLI commands ##

### OSPF dynamic routing ###
* router ospf 1
* log-adjacency-changes
* network 10.126.114.0 0.0.0.127 area 0 
* network 0.0.0.0 255.255.255.255 area 0
* network 10.126.115.0 0.0.0.127 area 1
* network 10.126.117.64 0.0.0.63 area 1
* network 10.126.117.128 0.0.0.63 area 1
* network 10.126.118.224 0.0.0.31 area 1
* network 10.126.119.0 0.0.0.31 area 1
!

### DHCPv4 service ###
* ip dhcp pool B1_Backbone_120N
* network 10.126.114.0 255.255.255.128
* default-router 10.126.114.2
* dns-server 10.126.115.2
-----------------------------------------
* ip dhcp pool B1_DMZ_70N
* network 10.126.115.0 255.255.255.128
* default-router 10.126.115.10
* dns-server 10.126.115.2
-----------------------------------------
* ip dhcp pool B1_END_USER_F0_40N
* network 10.126.117.64 255.255.255.192
* default-router 10.126.117.75
* dns-server 10.126.115.2
 ----------------------------------------- 
* ip dhcp pool B1_END_USER_F1_40N
* network 10.126.117.128 255.255.255.192
* default-router 10.126.117.139
* dns-server 10.126.115.2
-----------------------------------------
* ip dhcp pool B1_WiFi_24N
* network 10.126.118.224 255.255.255.224
* default-router 10.126.118.235
* dns-server 10.126.115.2
-----------------------------------------
* ip dhcp pool B1_VoIP_20N
* network 10.126.119.0 255.255.255.224
* default-router 10.126.119.10
* option 150 ip 10.126.119.10
* dns-server 10.126.115.2
-----------------------------------------
**Excluded addresses**  
*  ip dhcp excluded-address 10.126.117.75
*  ip dhcp excluded-address 10.126.115.2
*  ip dhcp excluded-address 10.126.115.3
*  ip dhcp excluded-address 10.126.115.10
*  ip dhcp excluded-address 10.126.114.2
*  ip dhcp excluded-address 10.126.117.139
*  ip dhcp excluded-address 10.126.118.235
*  ip dhcp excluded-address 10.126.119.10

### DNS ###

![DNS.png](DNS.PNG)

### NAT ###

* interface FastEthernet0/0
* ip address 10.126.114.2 255.255.255.128
* ip nat outside

---------------------------
* interface FastEthernet0/0.2
* encapsulation dot1Q 329
* ip address 10.126.115.10 255.255.255.128
* ip nat inside
------------------------------------
* router rip
* !
* ip nat inside source static tcp 10.126.115.3 80 10.126.114.2 80
* ip nat inside source static tcp 10.126.115.3 443 10.126.114.2 443
* ip nat inside source static tcp 10.126.115.2 53 10.126.114.2 53
* ip nat inside source static udp 10.126.115.2 53 10.126.114.2 53 

### VOIP CONFIGURATIONS ###

**First Floor 11.2**
* interface FastEthernet1/1
* switchport mode access
* switchport voice vlan 344

**GroundFloor 10.3**
* interface FastEthernet1/1
* switchport mode access
* switchport voice vlan 344

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
* ip source-address 10.126.119.10 port 2000
* auto assign 1 to 2
* auto assign 1 to 20


* ephone-dn 1
* number 10001


* ephone-dn 2
* number 10002


* ephone 2
* device-security-mode none
* mac-address 00D0.97B2.EEAE
* type 7960
* button 1:2


* ephone 1
* device-security-mode none
* mac-address 00D0.BCAC.3A31
* type 7960
* button 1:1

### Servers ###
**DNS**
* 10.126.115.2

**HTTP**
* 10.126.115.3