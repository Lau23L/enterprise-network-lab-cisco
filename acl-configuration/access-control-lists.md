# Access Control Lists (ACL)

## Objective

Restrict traffic between VLANs to simulate basic network security policies.

---

## Scenario

- Student VLANs should NOT access Server VLAN directly.
- Staff VLAN should have limited access to specific services.
- ISP simulation network should not access internal VLANs.

---

## Standard ACL Example

Block VLAN 10 from accessing VLAN 60 (Server VLAN):

access-list 10 deny 172.16.10.0 0.0.0.255
access-list 10 permit any

interface fastEthernet0/0.60
ip access-group 10 in

---

## Extended ACL Example

Restrict specific traffic:

access-list 110 deny ip 172.16.10.0 0.0.0.255 172.16.60.0 0.0.0.255
access-list 110 permit ip any any

interface fastEthernet0/0.10
ip access-group 110 in

---

## Verification

show access-lists
show ip interface

---

## Result

Traffic filtering was successfully applied between VLANs to simulate enterprise security segmentation.
