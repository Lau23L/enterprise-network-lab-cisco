# DHCP Configuration

## Objective

Automatically assign IP addresses to devices within each VLAN using a centralized DHCP service on the router.

---

## Network Design

Each VLAN receives dynamic IP configuration from a dedicated DHCP pool.

The router acts as the DHCP server.

---

## DHCP Pool Configuration Example

enable
configure terminal

ip dhcp excluded-address 172.16.10.1 172.16.10.10

ip dhcp pool VLAN10
network 172.16.10.0 255.255.255.0
default-router 172.16.10.254
dns-server 8.8.8.8

Example for another VLAN:

ip dhcp pool VLAN20
network 192.16.1.0 255.255.255.0
default-router 192.16.1.254
dns-server 8.8.8.8

---

## Verification

show ip dhcp binding
show ip dhcp pool

---

## Result

Devices across multiple VLANs successfully received IP configuration dynamically, simulating real enterprise network deployment.
