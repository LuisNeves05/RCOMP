RCOMP 2020-2021 Project - Sprint 1 - Member 1191421 folder
===========================================

## Building 3 ####
##### Luís Neves - 1191421 ###

###Building 3 - Ground Floor
![Building_2_groundfloor.jpg](floor0.jpg)

####Scale
```
 2cm -> 10 meters
 1cm -> 5 meters

 Area of room 
 1 --- 5
 measure --- x

<=> (x = measure * 5)/1
```

## Floor inventory

>#####For every length of cable calculated, it was taken into account the correct scale and necessary cable lenght inside telecomunication enclosures.


* ####Copper Cabble (T-568A)
>650 meters for the rest of the rooms on the ground floor
> #####13 950 meters total
* ####Fibre Cable
>Taking into consideration the redundacy needed to ensure safety and continuous signal to the building itself, twice the amount of fibre cable will be requested. 
>
>As so, to make every connection and keep them redundant, **190 meters** of fibre cable will be necessary.
* ####Floor Trunking
>This type of trunking should be rounded, to prevent accidents in the various rooms it is placed in.
>
>#####130 meters
* ####Dropped Ceiling Trunking
>On the contrary of the floor trunking, this can be a type of trunking to the client's choice, as it is going to remain hiden.
>
>#####50 meters
* ####Vertical Trunking
>Again, this type of trunking is to the client's taste, as it is meant to stay on the wall and should not cause much trouble.
>
>#####10 meters
* ####Access points
>The access points will be responsible for providing wireless internet coverage of the entire floor.
>
>The type of access point used provides a reach of 50 meters around it, as so, only 2 were necessary to cover the building. 
>However, it would be advised (for a stronger connection ground wide) to use more AP's with smaller but stronger connection power.
>
>#####Total = 2 Access Points
* ####Outlets
>Following the industry standards, for the big room on the right, the client will need 310 outlets.
>
>For the rest of the rooms on the ground floor the client will need to purchase 44 outlets for user use and one more for the Access Point.
>#####355 Outlets in total
* ####Telecomunication Enclosures
>For this floor, there will be 3 telecomunication enclosures.
>
>There are 2 Telecomunication Enclosures in room 30.5.
>
> **Number 1** will hold 4 devices (4 24 patch panels for the IC and HC's), so, it's size will be 6 * 4 U (S) = **24U**.
>
> **Number 2** will hold 7 devices (7 48 patch panels for the CP's), it's size will be 6 * 14 (patch panels with 48 entrances ocupy 2U) = **84U**.
>
>There is also a telecomunication enclosure in room 30.2, this one holds a single CP with a 48 patch panel.
>So it's size is 6 * 2 U = **12U**
>
>#####TE #1 -> 24U
>#####TE #2 -> 84U
>#####TE #3 -> 12U

###To sum up and explain every connection and decision made, 
This floor is made up of 1 IC, 3 HC's and 8 CP's. The first HC is directly connected to
the outlets, the second one outputs fiber cable and connects to the TE holding the 7 CP's
responsible for feeding the big and open room on the right, finally, the last HC connects to
the last CP in room 30.2 to power the outlets on that side of the building. 
Every fiber connection was made using redundancy to ensure good connection.


###Building 2 - Ground Floor
 ![Building_2_groundfloor.jpg](Building_2_groundfloor.jpg)
 
 ## Floor inventory

* ####Copper Cabble (T-568A)
>For all the rooms in the ground floor.
> #####1295 meters total
* ####Fibre Cable
>Taking into consideration the redundacy needed to ensure safety and continuous signal to the building itself, twice the amount of fibre cable will be requested. 
>
>As so, to make every connection and keep them redundant, **372 meters** of fibre cable will be necessary.
* ####Floor Trunking
>This type of trunking should be rounded, to prevent accidents in the various rooms it is placed in.
>
>#####148 meters

* ####Vertical Trunking
>Again, this type of trunking is to the client's taste, as it is meant to stay on the wall and should not cause much trouble.
>
>#####12 meters
* ####Access points
>The access points will be responsible for providing wireless internet coverage of the entire floor.
>
>The type of access point used provides a reach of 50 meters around it, as so, only 1 was necessary to cover the building. 
>However, it would be advised (for a stronger connection ground wide) to use more AP's with smaller but stronger connection power.
>
>#####2 Access Point
* ####Outlets
>Following the industry standards, for this floor 71 outlets are required, being that one of them is for the Access Point.
>#####60 Outlets in total
* ####Telecomunication Enclosures
>For this floor, there will be 3 telecomunication enclosures.
>
>**Number 1** (Room 20.2) will hold 3 devices (1 24 patch panel for the IC, 1 24 patch panel for the HC and 1 24 patch panel for the CP), so, it's size will be 6 * 3U (S) = **18U**.
>
>**Number 2** (Room 20.3) will hold 1 device (1 48 patch panels for the CP), it's size will be 6 * 2U (48 patch panels ocuppy 2U) = **12U**.
>
>**Number 3** (Room 20.4) will hold 1 device (1 48 patch panels for the CP), it's size will be 6 * 2U (48 patch panels ocuppy 2U) = **12U**.
>
>#####To sum up, 
>#####TE #1 -> 18U
>#####TE #2 -> 12U
>#####TE #3 -> 12U

###To sum up and explain every connection and decision made,
This floor is only requires outlets in some of the rooms, so its easy to route. smaller.Room 20.2 contains the IC, HC and a CP, which means it powers the entire floor. There are 2 Access Points, to provide full Wi-Fi support throughout all the floor's area.
Rooms 20.3 and 20.4 are quite outlet heavy, thus a 48 cp will be provided to each room to accomodate those necessities.

#Full inventory Building 2

####Copper Cable 
> ** 1255  meters of S/UTP protected cable**
>
> **40,50 meters of S/STP protected cable** 
####Fiber Cable
> **372 meters**
####Floor Trunking
> **148 meters**
####Vertical Trunking
> **12 meters**
####Access Points
> **2 Access Points**
####Outlets
> **71 outlets**
####Telecomunication Enclosures
> **3 total telecomunication enclosures**
>
>**Room 20.2 - TE 1 - 18U**  
>
>**Room 20.3 - TE 2 - 12U**  
>
>**Room 20.4 - TE 2 - 12U**
>


###Demonstration of calculations regarding the number of network outlets for each room

####Ground Floor
>**Room 30.1**
>   >1.3cm x 1.5cm
>   ><=>6.5 x 7.5 <=> 48,75 m2
>
>
>######9 Outlets

>**Room 30.2**
>   >1.3cm x 1.5cm
>   ><=>6.5 x 7.5 <=> 48,75 m2
>
>######9 Outlets


>**Room 30.3**
 >   >1.3cm x 1.5cm
 >   ><=>6.5 x 7.5 <=> 48,75 m2
 >
 >
 >######9 Outlets

>**Room 30.4**
 >   >1.6cm x 1.6cm
 >   ><=>8 x 8 <=> 64 m2
 >
 >
 >######12 Outlets

>**Room 30.5**
 >   >1.2cm x 1.5cm
 >   ><=>6 x 7.5 <=> 48,75 m2
 >
 >
 >######9 Outlets

>**Big Open Room**
 >   >11cm x 5.7cm
 >   ><=>55 x 28.5 <=> 1567.5 m2
 >
 >
 >######310 Outlets

####Ground Floor Building 2

>**20.2**
 >   >2cm x 3.5cm
 >   ><=>6.7 x 11.7 <=> 78.39 m2
 >
 >
 >######16 Outlets

>**20.3**
 >   >3cm x 4cm
 >   ><=>10 x 13.33 <=> 133.3 m2
 >
 >
 >######27 Outlets

>**20.4**
 >   >5.5cm x 2.5cm
 >   ><=>8.33 x 18.33 <=> 74.75 m2
 >
 >
 >######31 Outlets