RCOMP 2019-2020 Project - Sprint 2 - Member 1121224 folder
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

* 10.126.114.2 *


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
### VTP mode client ###
* enable
* configure terminal
* vtp mode client
### VTP mode server ###
* enable
* configure terminal
* vtp mode server

### Trunking and Access between layer 2 devices and end users ###
With all the switches defined as client or server, we now had access to the defined VLANs in every switch. As so, depending on the end user type, the Fast Ethernet cord was configured into Access mode and selected the correct VLAN for the end device.

Furthermore, between switches, to ensure that every switch knew every VLAN available, the connection between them was in trunk mode.
### Access Point Channels ###

Taking into consideration that **Building 1** had **2** total Access Points, different channels had to be configured for the 2.4Ghz port. 
As so, the first AP was assigned with channel **number 1** and the second with **number 9**

To ensure correct connection from the AP to the Wireless Laptops, the APs were organized and distributed acordingly on the Physical part of the project

### VoIP phones VLAN ###
* enable
* configure terminal
* interface fastEthernet (...)
* switchport mode access
* no switchport access vlan
* switchport voice vlan 344

### VTP domain name ###
* enable
* config t
* vtp domain rcompdlg3

### Sub-interfaces ###

#### Local servers, administration workstations, and machines (DMZ) ####
* enable
* configure terminal
* interface FastEthernet 0/0.2
* encapsulation dot1Q 244
* ip address 10.126.115.10 255.255.255.128
* no shutdown
* exit

#### End user outlets on the ground floor ####
* enable
* configure terminal	
* interface FastEthernet 0/0.3
* encapsulation dot1Q 336
* ip address 10.126.117.75 255.255.255.192
* no shutdown
* exit

#### End user outlets on floor one ####
* enable
* configure terminal
* interface FastEthernet 0/0.4
* encapsulation dot1Q 337
* ip address 10.126.117.139 255.255.255.192
* no shutdown
* exit

#### Wi-Fi network ####
* enable
* configure terminal
* interface FastEthernet 0/0.5
* encapsulation dot1Q 343
* ip address 10.126.118.235 255.255.255.224
* no shutdown
* exit


#### VoIP (IP-phones) ####
* enable
* configure terminal
* interface FastEthernet 0/0.6
* encapsulation dot1Q 344
* ip address 10.126.119.10 255.255.255.224
* no shutdown
* exit

## Structured cable design ##
### Ground Floor ###
| **Cabling Project** | **Network Simulation** |                                       
|:--------------------|:-----------------------|
|![B1GroundFloor.png](B1GroundFloorbuilding1floor1.png)    |![B1_GF.png](B1_GF.png)   |


### Floor one ###
| **Cabling Project** | **Network Simulation** |                                       
|:--------------------|:-----------------------|
|![building1floor1.png](building1floor1.png)    |![B1_1F.png](B1_1F.png)   |
