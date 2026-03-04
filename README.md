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
