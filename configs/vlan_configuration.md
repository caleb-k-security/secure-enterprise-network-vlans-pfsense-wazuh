# VLAN Configuration Summary

## VLAN Structure

Admin VLAN — 192.168.10.0/24  
Staff VLAN — 192.168.20.0/24  
Guest VLAN — 192.168.30.0/24  

Each VLAN was assigned to switch ports based on device role.

## Routing

Inter-VLAN routing implemented using router-on-a-stick architecture.

Each VLAN configured with its own gateway interface.
