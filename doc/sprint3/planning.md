RCOMP 2020-2021 Project - Sprint 3 planning
===========================================
### Sprint master: 1121224 ###
(This file is to be created/edited by the sprint master only)
# 1. Sprint's backlog #
* T.3.1-Update the campus.pkt layer three Packet Tracer simulation from the
  previous sprint, to include the described features in this sprint for
  building 1.


* T.3.2-Update the campus.pkt layer three Packet Tracer simulation from the
  previous sprint, to include the described features in this sprint for
  building 2.
  Final integration of each member’s Packet Tracer simulation into a
  single simulation.


* T.3.3-Update the campus.pkt layer three Packet Tracer simulation from the
  previous sprint, to include the described features in this sprint for
  building 3.



* T.3.4-Update the campus.pkt layer three Packet Tracer simulation from the
  previous sprint, to include the described features in this sprint for
  building 4.


# 2. Technical decisions and coordination #
In this section, all technical decisions taken in the planning meeting should be mentioned.
Most importantly, all technical decisions impacting on the subtasks implementation must be settled on this 		meeting and specified here.


* Backbone cable types to be used - CAT7 between layer 2 devices and outlets, optical fibre cords in every other connection
* VLAN IDs to be used - 325 - 345
* VTP domains - rcompdlg3
* WiFi channels - 1, 6, 9
* Application protocols outlining (further coordination may be required between members)
* IPv4 networks' addresses and  - 10.126.112.0/20 (10.126.112.0 until 10.126.127.255 4096 connections)
  *ISP routers' IPv4 node addresses - 120.57.201.208/30 (Network)
  120.57.201.209 (ISP)
  120.57.201.210 (Router-Campus)
  120.57.201.211 (Network Broadcast)

## IPv4 address space to be used (addresses block): 10.126.112.0/20 ##
* Network mask: (1111 1111).(1111 1111).(1111 0000).(0000 0000) = 255.255.240.0
* Broadcast address: 10.126.127.255
* Network’s first valid node address: 10.126.112.1
* Network’s last valid node address: 10.126.127.254

## ISP router IPv4 node address: 120.57.201.208/30 ##
* Network mask: (1111 1111).(1111 1111).(1111 1111).(1111 1100) = 255.255.255.252
* Broadcast address: 120.57.201.211
* Network’s first valid node address: 120.57.201.209
* Network’s last valid node address: 120.57.201.210


## Devices naming ##
* RT-Campus
* RT_ISP(internet)
* Router: Router_B[BUILDING]
* Main Cross-Connect: Main_Cross-Connect
* Intermediate Cross-Connect:Intermediate_Cross_Connect_[BUIDING]
* Horizontal Cross-Connect: Horizontal_Cross-Connect_Number(if needed)F[FLOOR]_B[BUIDING]
* Consolidation Point: Consolidation_Point_[ROOM]_[BUILDING]
* IP Phone: IP_Phone_[ROOM]_[BUILDING]
* PC: PC_[ROOM]_[BUILDING]
* Laptop: Laptop_[ROOM]_[BUILDING]
* Server: Server_F[FLOOR]_B[BUILDING]

## OSPF areas ids ##
* Backbone area: 0
* Buiding 1: 1
* Buiding 2: 2
* Buiding 3: 3
* Buiding 4: 4

## VoIP phone prefix digits schema ##
* Building 1 : 100**
* Building 2 : 200**
* Building 3 : 300**
* Building 4 : 400**

###SERVERS ###

                                   Building 1

**DNS**
* 10.126.115.2

**HTTP**
* 10.126.115.3

                                   Building 2

**DNS**
* 10.126.119.42

**HTTP**
* 10.126.119.41

                                   Building 3

**DNS**
* 10.126.112.1

**HTTP**
* 10.126.112.2

                                   Building 4

**DNS**
* 10.126.112.1

**HTTP**
* 10.126.112.2

# 3. Subtasks assignment #
(For each team member (sprint master included), the description of the assigned subtask in sprint 2)

**1121224** -T.3.1 - Update the campus.pkt layer three Packet Tracer simulation from the previous sprint, to include the described features in this sprint for building 1.

* VLAN IDs to be used - 327 , 329 , 336 , 337 , 343 , 344
* VTP domains - rcompdlg3
* IPv4 networks' addresses - 10.126.114.0/25  ; 10.126.115.0/25 ;   10.126.117.64/26 ;                                        10.126.117.128/26; 10.126.118.224/27 ; 10.126.119.0/27 ;
* IPv4 router node address: 10.126.114.2
* Local DNS domain name: rcomp-20-21-dl-g3
* Unqualified DNA name: ns.rcomp-20-21-dl-g3

**1181597**-3.2-Update the campus.pkt layer three Packet Tracer simulation from the
previous sprint, to include the described features in this sprint for
building 2.
Final integration of each member’s Packet Tracer simulation into a
single simulation.

* VLAN IDs to be used - 328 , 330 , 331 , 341 , 345
* VTP domains - rcompdlg3
* IPv4 networks' addresses - 10.126.114.128/25  ; 10.126.115.128/25 ;   10.126.116.0/26 ;                                      10.126.118.128/26;   10.126.119.32/28
* IPv4 router node address: 10.126.114.1
* Local DNS domain name: building-2.rcomp-20-21-dl-g3
* Unqualified DNA name: ns.building-2.rcomp-20-21-dl-g3

**1191421**-3.3-Update the campus.pkt layer three Packet Tracer simulation from the
previous sprint, to include the described features in this sprint for
building 3.

* VLAN IDs to be used - 325 , 332 , 335 , 338 , 339
* VTP domains - rcompdlg3
* IPv4 networks' addresses - 10.126.112.0/24  ;   10.126.116.64/26 ;  10.126.117.0/26;                                        10.126.117.192/26 ;  10.126.118.0/26
* IPv4 router node address:  10.126.114.3
* Local DNS domain name: building-3.rcomp-20-21-dl-g3
* Unqualified DNA name: ns.building-3.rcomp-20-21-dl-g3

**1200625**T.3.4-Update the campus.pkt layer three Packet Tracer simulation from the
previous sprint, to include the described features in this sprint for
building 4.

* VLAN IDs to be used - 326 , 333 , 334 , 340 , 342
* VTP domains - rcompdlg3
* IPv4 networks' addresses - 10.126.113.0/24  ; 10.126.116.128/26 ; 10.126.116.192/26;                                        10.126.118.64/26 ; 10.126.118.192/27
* IPv4 router node address: 10.126.114.4
* Local DNS domain name: building-4.rcomp-20-21-dl-g3
* Unqualified DNA name: ns.building-4.rcomp-20-21-dl-g3

# 3. Subtasks assignment #
* Every member should do the following on the assigned building.

1. Structured cable design.
2. VLAN devices configuration.
3. IPv4 addressing and routing configurations.
4. Network access policies enforcement.


