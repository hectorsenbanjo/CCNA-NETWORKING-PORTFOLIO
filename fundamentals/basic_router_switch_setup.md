1️⃣ Topology

Router R1

Switch S1

PC1 connected to Switch S1

PC1 ---- S1 ---- R1


PC1: 192.168.10.10/24, Gateway 192.168.10.1

R1 (G0/0): 192.168.10.1/24

2️⃣ Router Configuration (R1)

R1> enable
R1# configure terminal
R1(config)# hostname R1

! Secure privileged access

R1(config)# enable secret cisco123

! Configure console password

R1(config)# line console 0
R1(config-line)# password class
R1(config-line)# login
R1(config-line)# exit

! Configure vty (telnet/ssh) password

R1(config)# line vty 0 4
R1(config-line)# password class
R1(config-line)# login
R1(config-line)# exit

! Set IP address on interface

R1(config)# interface g0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit

! Save configuration

R1# write memory

3️⃣ Switch Configuration (S1)
S1> enable
S1# configure terminal
S1(config)# hostname S1

! Secure privileged access

S1(config)# enable secret cisco123

! Console password

S1(config)# line console 0
S1(config-line)# password class
S1(config-line)# login
S1(config-line)# exit

! vty password

S1(config)# line vty 0 4
S1(config-line)# password class
S1(config-line)# login
S1(config-line)# exit

! Management VLAN interface

S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.10.2 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit

! Default gateway for switch management

S1(config)# ip default-gateway 192.168.10.1

! Save configuration

S1# write memory

4️⃣ Verification

On R1:

R1# show ip interface brief
Interface   IP-Address     OK? Method Status Protocol
Gig0/0      192.168.10.1   YES manual up     up


On S1:

S1# ping 192.168.10.1
Success rate is 100 percent (5/5), round-trip min/avg/max = 10/15/20 ms


On PC1:

C:\> ping 192.168.10.1   ✅ Gateway reachable
C:\> ping 192.168.10.2   ✅ Switch reachable


✅ Story Recap

We gave devices hostnames → makes configs easier to read.

We set passwords → improves security.

We assigned IP addresses → enables connectivity.

We verified with ping and show commands.

This is the foundation of all CCNA labs. Every bigger lab builds on these steps.
