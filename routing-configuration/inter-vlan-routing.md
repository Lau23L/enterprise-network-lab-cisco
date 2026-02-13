# Inter-VLAN Routing (Router-on-a-Stick)

## Objective

Enable communication between different VLANs using a single physical router interface with subinterfaces.

---

## Network Design

The core router connects to the main switch using a trunk link.

Each VLAN is assigned a subinterface using IEEE 802.1Q encapsulation.

---

## Subinterface Configuration Example

enable
configure terminal

interface fastEthernet0/0
no shutdown

interface fastEthernet0/0.10
encapsulation dot1Q 10
ip address 172.16.255.254 255.255.255.0

interface fastEthernet0/0.20
encapsulation dot1Q 20
ip address 192.16.1.254 255.255.255.0

interface fastEthernet0/0.30
encapsulation dot1Q 30
ip address 192.16.2.254 255.255.255.0


---

## Trunk Configuration (Switch)

interface fastEthernet0/1
switchport mode trunk

---

## Verification

show ip interface brief
show vlan brief
show interfaces trunk

---

## Result

Inter-VLAN communication was successfully enabled through the router using 802.1Q tagging.
