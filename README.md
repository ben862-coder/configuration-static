========================================
STATIC ROUTING - CISCO PACKET TRACER
========================================

TOPOLOGY
PC1 ---- R1 ---- R2 ---- PC2

IP ADDRESSING
----------------------------------------
PC1 : 192.168.1.10/24  GW 192.168.1.1
PC2 : 192.168.2.10/24  GW 192.168.2.1

R1 G0/0 : 192.168.1.1/24
R1 G0/1 : 10.10.10.1/30

R2 G0/0 : 10.10.10.2/30
R2 G0/1 : 192.168.2.1/24

========================================
ROUTER 1 CONFIGURATION
========================================
enable
configure terminal
hostname R1

interface g0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit

interface g0/1
 ip address 10.10.10.1 255.255.255.252
 no shutdown
exit

ip route 192.168.2.0 255.255.255.0 10.10.10.2

end
write memory

========================================
ROUTER 2 CONFIGURATION
========================================
enable
configure terminal
hostname R2

interface g0/0
 ip address 10.10.10.2 255.255.255.252
 no shutdown
exit

interface g0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
exit

ip route 192.168.1.0 255.255.255.0 10.10.10.1

end
write memory

========================================
TESTING
========================================
PC1> ping 192.168.2.10
