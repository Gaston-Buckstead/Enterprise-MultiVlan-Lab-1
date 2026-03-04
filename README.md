MultiVlan Static-Routing Lab
<img width="1091" height="461" alt="image" src="https://github.com/user-attachments/assets/f62fcf15-64f1-431b-a95f-4bce46371111" />
3 Tier Archetecture

This Project has 3 routers with each router connected to its own network. Static routes were manually configured to enable end to end connectivity across all networks.

IP Adressing Plan

WAN Links Router to Router

Network 192.168.12.0/30

R3 G0/2 – 192.168.12.1

R4 G0/2 – 192.168.12.2

Network 192.168.18.0/30

R4 G0/1 – 192.168.18.2

R5 G0/2 – 192.168.18.1

Router-to-Distribution Links

Network 192.168.11.0/30

R3 G0/0 – 192.168.11.1

MLS3 G1/0/4 – 192.168.11.2

Network 192.168.10.0/30

R4 G0/0 – 192.168.10.2

MLS2 G1/0/1 – 192.168.10.1

Network 192.168.19.0/30

R5 G0/0 – 192.168.19.1

MLS6 G1/0/1 – 192.168.19.2

VLAN Networks:

On MLS3

VLAN 3 – 192.168.3.0/24 – Default Gateway 192.168.3.1

VLAN 4 – 192.168.4.0/24 – Default Gateway 192.168.4.1

VLAN 5 – 192.168.5.0/24 – Default Gateway 192.168.5.1

On MLS2

VLAN 6 – 192.168.6.0/24 – Default Gateway 192.168.6.2

On MLS6

VLAN 15 – 192.168.15.0/24 – Default Gateway 192.168.15.1

VLAN 16 – 192.168.16.0/24 – Default Gateway 192.168.16.1

VLAN 17 – 192.168.17.0/24 – Default Gateway 192.168.17.1

R3 Config.txt:

Building configuration...

Current configuration : 1223 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX1524F86R-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 192.168.11.1 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface GigabitEthernet0/2
 ip address 192.168.12.1 255.255.255.252
 duplex auto
 speed auto
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
ip route 192.168.12.0 255.255.255.252 192.168.12.2 
ip route 192.168.6.0 255.255.255.0 192.168.12.2 
ip route 192.168.5.0 255.255.255.0 192.168.11.2 
ip route 192.168.4.0 255.255.255.0 192.168.11.2 
ip route 192.168.3.0 255.255.255.0 192.168.11.2 
ip route 192.168.18.0 255.255.255.252 192.168.12.2 
ip route 192.168.15.0 255.255.255.0 192.168.12.2 
ip route 192.168.16.0 255.255.255.0 192.168.12.2 
ip route 192.168.17.0 255.255.255.0 192.168.12.2 
ip route 192.168.19.0 255.255.255.252 192.168.12.2 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end

R4 Config.txt: 

Building configuration...

Current configuration : 1239 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX15240657-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 192.168.10.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 192.168.18.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 ip address 192.168.12.2 255.255.255.252
 duplex auto
 speed auto
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
ip route 192.168.12.0 255.255.255.252 192.168.12.1 
ip route 192.168.6.0 255.255.255.0 192.168.10.1 
ip route 192.168.3.0 255.255.255.0 192.168.12.1 
ip route 192.168.4.0 255.255.255.0 192.168.12.1 
ip route 192.168.5.0 255.255.255.0 192.168.12.1 
ip route 192.168.18.0 255.255.255.252 192.168.18.1 
ip route 192.168.15.0 255.255.255.0 192.168.18.1 
ip route 192.168.16.0 255.255.255.0 192.168.18.1 
ip route 192.168.17.0 255.255.255.0 192.168.18.1 
ip route 192.168.19.0 255.255.255.252 192.168.18.1 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end


R5 Config.txt:

Building configuration...

Current configuration : 1223 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX15248JWO-
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 192.168.19.1 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface GigabitEthernet0/2
 ip address 192.168.18.1 255.255.255.252
 duplex auto
 speed auto
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
ip route 192.168.18.0 255.255.255.252 192.168.18.2 
ip route 192.168.15.0 255.255.255.0 192.168.19.2 
ip route 192.168.16.0 255.255.255.0 192.168.19.2 
ip route 192.168.17.0 255.255.255.0 192.168.19.2 
ip route 192.168.6.0 255.255.255.0 192.168.18.2 
ip route 192.168.12.0 255.255.255.252 192.168.18.2 
ip route 192.168.12.0 255.255.255.252 192.168.12.1 
ip route 192.168.5.0 255.255.255.0 192.168.18.2 
ip route 192.168.4.0 255.255.255.0 192.168.18.2 
ip route 192.168.3.0 255.255.255.0 192.168.18.2 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end


MLS3 Config.text:

Building configuration...

Current configuration : 1902 bytes
!
version 16.3.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
!
no ip cef
ip routing
!
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet1/0/1
 switchport trunk allowed vlan 3-5
 switchport mode trunk
!
interface GigabitEthernet1/0/2
 switchport trunk allowed vlan 3-5
 switchport mode trunk
!
interface GigabitEthernet1/0/3
 switchport trunk allowed vlan 3-5
 switchport mode trunk
!
interface GigabitEthernet1/0/4
 no switchport
 ip address 192.168.11.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/5
!
interface GigabitEthernet1/0/6
!
interface GigabitEthernet1/0/7
!
interface GigabitEthernet1/0/8
!
interface GigabitEthernet1/0/9
!
interface GigabitEthernet1/0/10
!
interface GigabitEthernet1/0/11
!
interface GigabitEthernet1/0/12
!
interface GigabitEthernet1/0/13
!
interface GigabitEthernet1/0/14
!
interface GigabitEthernet1/0/15
!
interface GigabitEthernet1/0/16
!
interface GigabitEthernet1/0/17
!
interface GigabitEthernet1/0/18
!
interface GigabitEthernet1/0/19
!
interface GigabitEthernet1/0/20
!
interface GigabitEthernet1/0/21
!
interface GigabitEthernet1/0/22
!
interface GigabitEthernet1/0/23
!
interface GigabitEthernet1/0/24
!
interface GigabitEthernet1/1/1
!
interface GigabitEthernet1/1/2
!
interface GigabitEthernet1/1/3
!
interface GigabitEthernet1/1/4
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan3
 mac-address 0003.e415.7901
 ip address 192.168.3.1 255.255.255.0
!
interface Vlan4
 mac-address 0003.e415.7902
 ip address 192.168.4.1 255.255.255.0
!
interface Vlan5
 mac-address 0003.e415.7903
 ip address 192.168.5.1 255.255.255.0
!
ip classless
ip route 0.0.0.0 0.0.0.0 192.168.11.1 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
!
end

MLS2 Config.txt:

Building configuration...

Current configuration : 1616 bytes
!
version 16.3.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
!
no ip cef
ip routing
!
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet1/0/1
 no switchport
 ip address 192.168.10.1 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/2
 switchport trunk allowed vlan 6
 switchport mode trunk
!
interface GigabitEthernet1/0/3
!
interface GigabitEthernet1/0/4
!
interface GigabitEthernet1/0/5
!
interface GigabitEthernet1/0/6
!
interface GigabitEthernet1/0/7
!
interface GigabitEthernet1/0/8
!
interface GigabitEthernet1/0/9
!
interface GigabitEthernet1/0/10
!
interface GigabitEthernet1/0/11
!
interface GigabitEthernet1/0/12
!
interface GigabitEthernet1/0/13
!
interface GigabitEthernet1/0/14
!
interface GigabitEthernet1/0/15
!
interface GigabitEthernet1/0/16
!
interface GigabitEthernet1/0/17
!
interface GigabitEthernet1/0/18
!
interface GigabitEthernet1/0/19
!
interface GigabitEthernet1/0/20
!
interface GigabitEthernet1/0/21
!
interface GigabitEthernet1/0/22
!
interface GigabitEthernet1/0/23
!
interface GigabitEthernet1/0/24
!
interface GigabitEthernet1/1/1
!
interface GigabitEthernet1/1/2
!
interface GigabitEthernet1/1/3
!
interface GigabitEthernet1/1/4
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan6
 mac-address 0004.9acd.8101
 ip address 192.168.6.2 255.255.255.0
!
ip classless
ip route 0.0.0.0 0.0.0.0 192.168.10.2 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
!
end

MLS6 Config.txt:

Building configuration...

Current configuration : 2546 bytes
!
version 16.3.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
!
no ip cef
ip routing
!
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree vlan 15-16 priority 4096
spanning-tree vlan 17 priority 8192
!
!
!
!
!
!
interface Port-channel1
 switchport trunk native vlan 99
 switchport trunk allowed vlan 15-17
 switchport mode trunk
!
interface GigabitEthernet1/0/1
 no switchport
 ip address 192.168.19.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/2
 switchport trunk allowed vlan 15-17
 switchport mode trunk
!
interface GigabitEthernet1/0/3
 switchport trunk allowed vlan 15-17
 switchport mode trunk
!
interface GigabitEthernet1/0/4
 switchport trunk allowed vlan 15-17
 switchport mode trunk
!
interface GigabitEthernet1/0/5
 switchport trunk native vlan 99
 switchport trunk allowed vlan 15-17
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/6
 switchport trunk native vlan 99
 switchport trunk allowed vlan 15-17
 switchport mode trunk
 channel-group 1 mode active
!
interface GigabitEthernet1/0/7
!
interface GigabitEthernet1/0/8
!
interface GigabitEthernet1/0/9
!
interface GigabitEthernet1/0/10
!
interface GigabitEthernet1/0/11
!
interface GigabitEthernet1/0/12
!
interface GigabitEthernet1/0/13
!
interface GigabitEthernet1/0/14
!
interface GigabitEthernet1/0/15
!
interface GigabitEthernet1/0/16
!
interface GigabitEthernet1/0/17
!
interface GigabitEthernet1/0/18
!
interface GigabitEthernet1/0/19
!
interface GigabitEthernet1/0/20
!
interface GigabitEthernet1/0/21
!
interface GigabitEthernet1/0/22
!
interface GigabitEthernet1/0/23
!
interface GigabitEthernet1/0/24
!
interface GigabitEthernet1/1/1
!
interface GigabitEthernet1/1/2
!
interface GigabitEthernet1/1/3
!
interface GigabitEthernet1/1/4
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan15
 mac-address 0090.21b3.de01
 ip address 192.168.15.1 255.255.255.0
 standby 15 ip 192.168.15.2
 standby 15 priority 110
 standby 15 preempt
!
interface Vlan16
 mac-address 0090.21b3.de02
 ip address 192.168.16.1 255.255.255.0
 standby 16 ip 192.168.16.2
 standby 16 priority 110
 standby 16 preempt
!
interface Vlan17
 mac-address 0090.21b3.de03
 ip address 192.168.17.1 255.255.255.0
 standby 17 ip 192.168.17.2
 standby 17 preempt
!
ip classless
ip route 0.0.0.0 0.0.0.0 192.168.19.1 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
!
end

Verification:

Ping from VLAN 3 Host 192.168.3.3 to VLAN 17 Host 192.168.17.15 which confirms that inter-VLAN routing is functioning and static routes between routers are configured correctly.

<img width="308" height="516" alt="image" src="https://github.com/user-attachments/assets/3af7bee7-73fc-437c-8e69-ea76a8496364" />


Trouble-Shooting Situation

<img width="363" height="416" alt="image" src="https://github.com/user-attachments/assets/79c688be-aeb0-4ea8-9c4a-8aa1d452d579" />

This image is a failed ping to 192.168.19.1 from a PC in Vlan 3

SOLUTION:

<img width="374" height="233" alt="image" src="https://github.com/user-attachments/assets/a0443de6-1586-4c0d-a309-93545ee5a826" />

Result:

<img width="315" height="509" alt="image" src="https://github.com/user-attachments/assets/234685cf-858b-4cb4-ac36-b406df3f0490" />

