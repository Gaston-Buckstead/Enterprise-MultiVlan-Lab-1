MultiVlan Static-Routing Lab
<img width="1091" height="461" alt="image" src="https://github.com/user-attachments/assets/f62fcf15-64f1-431b-a95f-4bce46371111" />
3 Tier Archetecture

This Project has 3 router with each router connected to to its own network. Static routes were manually configured to enable end to end connectivity across all networks.

IP Adressing Plan

Router 3: G0/2 interface Ip Address 192.168.12.1/30, G0/0 interface Ip Address 192.168.11.1

Vlan 3 Subnet Network: 192.168.3.0/24 | Gateway IP: 192.168.3.1

Vlan 4 Subnet Network: 192.168.4.0/24 | Gateway IP: 192.168.4.1

Vlan 5 Subnet Network: 192.168.5.0/24 | Gateway IP: 192.168.5.1

Multilayer Switch 3: G1/0/4 interface Ip Address 192.168.11.2/30

Router 4: G0/2 interface Ip Address 192.168.12.2/30, G0/1 interface Ip Address 192.168.18.2/30, G0/0 interface Ip Address 192.168.10.2/30

Vlan 6 Subnet Network: 192.168.6.0/24 | Gateway IP: 192.168.6.2

Multilayer Switch 2: G1/0/1 interface Ip Address 192.168.10.1/30

Router 5: G0/2 interface Ip Address 192.168.18.1/30, G0/0 interface Ip Address 192.168.19.1/30

Multilayer Switch 6: G1/0/1 interface Ip Address 192.168.19.2/30

Vlan 15 Subnet Network: 192.168.15.0/24 | Gateway IP: 192.168.15.1

Vlan 16 Subnet Network: 192.168.16.0/24 | Gateway IP: 192.168.16.1

Vlan 17 Subnet Network: 192.168.17.0/24 | Gateway IP: 192.168.17.1
