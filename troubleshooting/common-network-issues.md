# Network Troubleshooting Scenarios

## Scenario 1 – Host Cannot Reach Another VLAN

### Problem
A device in VLAN 10 cannot communicate with a device in VLAN 20.

### Troubleshooting Steps

1. Verify IP configuration on host:
ipconfig

2. Check default gateway configuration.

3. Verify router subinterfaces:
show ip interface brief

4. Confirm trunk configuration on switch:
show interfaces trunk

5. Check ACL rules:
show access-lists

### Resolution
Incorrect trunk configuration was preventing inter-VLAN routing. Trunk mode was enabled and connectivity restored.

---

## Scenario 2 – Host Not Receiving IP Address

### Problem
Device in VLAN 30 does not receive IP from DHCP.

### Troubleshooting Steps

1. Check DHCP pool:
show ip dhcp pool

2. Verify excluded addresses.

3. Confirm correct VLAN assignment on switch.

4. Ensure correct default gateway in DHCP pool.

### Resolution
Incorrect network statement in DHCP pool. Configuration corrected and lease successfully assigned.
