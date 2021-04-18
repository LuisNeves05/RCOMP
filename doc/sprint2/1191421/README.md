RCOMP 2020-2021 Project - Sprint 2 - Member 1191421 
===========================================

# Building 3 #

## Technical decisions ##

### VLAN devices configuration ###
**VLAN IDs to be used: 325 - 255**

* VLAN for the building DMZ (for servers, administration workstations, and industrial machines) (B3_DMZ_250N): **325**
* VLAN for the Wi-Fi network (for all access-points’ outlets within the building) (B3_WIFI_60N): **332** 
* VLAN for all end-user outlets on floor one of the building (B3_END_USER_F1_44N): **335**
* VLAN for all end-user outlets on the ground floor (B3_END_USER_F0_40N): **338**
* VLAN for VoIP (for IP-phones) (B3_VoIP_40N): **339**

### Router IPv4 Address ###

The router belongs to the backbone VLAN 

It's IP address is **10.126.114.3**

### ISP router IPv4 node address ###

* 120.57.201.209/30

#### Local servers, administration workstations, and machines (DMZ): 250 nodes ####
* Network in CIDR notation: 10.126.112.0/24
* Network’s first valid node address: 10.126.112.1
* Network’s last valid node address: 10.126.112.254 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(0000 0000) = 255.255.255.0
* Broadcast address: 10.126.112.255

#### Wi-Fi network: 60 nodes ####
* Network in CIDR notation: 10.126.116.64/26
* Network’s first valid node address: 10.126.116.65
* Network’s last valid node address: 10.126.116.126 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192
* Broadcast address: 10.126.116.127

#### End user outlets on floor one: 44 nodes ####
* Network in CIDR notation: 10.126.117.0/26
* Network’s first valid node address: 10.126.117.1
* Network’s last valid node address: 10.126.117.62 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192 
* Broadcast address: 10.126.117.63

#### End user outlets on the ground floor: 40 nodes ####
* Network in CIDR notation: 10.126.117.192/26
* Network’s first valid node address: 10.126.117.193
* Network’s last valid node address: 10.126.117.254 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192  
* Broadcast address: 10.126.117.255

#### VoIP (IP-phones): 40 nodes ####
* Network in CIDR notation: 10.126.118.0/26
* Network’s first valid node address: 10.126.118.1
* Network’s last valid node address: 10.126.118.62 
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1100 0000) = 255.255.255.192  
* Broadcast address: 10.126.118.63

## Device Configuration using CLI ##
### VTP domain name ###
Configuration was used in every switch
* enable
* configure terminal
* vtp domain rcompdlg3




### VTP mode Client ###

In the individual project building, this config was used from the IC below (HCs and CPs). On the other hand, in the campus global project, this config was used for every switch below the MC (ICs, HCs and CPs)

* enable
* configure terminal
* vtp mode client

### VTP mode Server ###

In the individual project building, this config was used on the IC. 
On the other hand, in the campus global project, this config was used for the MC, making the subsequent ICs become a client
* enable
* configure terminal
* vtp mode server

### Trunking and Access between layer 2 devices and end users ###
With all the switches defined as client or server, we now had access to the defined VLANs in every switch. As so, depending on the end user type, the Fast Ethernet cord was configured into Access mode and selected the correct VLAN for the end device.

Furthermore, between switches, to ensure that every switch knew every VLAN available, the connection between them was in trunk mode.
### Access Point Channels ###

Taking into consideration that **Building 3** had **3** total Access Points, different channels had to be configured for the 2.4Ghz port. 
As so, the first AP was assigned with channel **number 1**, the second with **number 6** and the last with **number 9**

To ensure correct connection from the AP to the Wireless Laptops, the APs were organized and distributed acordingly on the Physical part of the project
### VoIP phones VLAN ###

Since the VoIP phones were not a big focus in this sprint, only a basic configuration was made.

* enable
* configure terminal
* interface fastEthernet [...]
* switchport mode access
* no switchport access vlan
* switchport voice vlan 339

### Sub-interfaces ###

This configuration was put into the router connected to the building IC so that when a packet is being transmited between end users from different VLANs, the packet comes to the router and is sent on it's way to the end user from the second VLAN

In hindsight, for organization purposes, the IPs chosen for the router Sub-interfaces could have been done a bit differently. The current ones are simply random available IPs from the network and, if decided earlier, the first network IP could have been chosen.

####Local servers, administration workstations, and machines (DMZ)  ####
* enable
* configure terminal	
* interface FastEthernet 0/0.1
* encapsulation dot1Q 325
* ip address 10.126.112.50 255.255.255.0
* no shutdown
* exit

#### Wi-Fi network ####
* enable
* configure terminal
* interface FastEthernet 0/0.2
* encapsulation dot1Q 332
* ip address 10.126.116.68 255.255.255.192
* no shutdown
* exit

#### End user outlets on floor one ####

* enable
* configure terminal
* interface FastEthernet 0/0.3
* encapsulation dot1Q 335
* ip address 10.126.117.3 255.255.255.192
* no shutdown
* exit


#### End user outlets on the ground floor ####
* enable
* configure terminal
* interface FastEthernet 0/0.4
* encapsulation dot1Q 338
* ip address 10.126.117.203 255.255.255.192
* no shutdown
* exit

#### VoIP (IP-phones) ####
* enable
* configure terminal
* interface FastEthernet 0/0.5
* encapsulation dot1Q 339
* ip address 10.126.118.1 255.255.255.192
* no shutdown
* exit