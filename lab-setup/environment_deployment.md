# Lab Environment Deployment

## Virtualization Platform
VirtualBox was used to simulate enterprise infrastructure.

## Systems Deployed

Ubuntu Server VM
- Hosts Wazuh Manager, Indexer, Dashboard

Windows Endpoint
- Wazuh agent installed for telemetry

pfSense Firewall
- Enforces VLAN traffic policies

## Resources

Ubuntu VM
RAM: 4GB
CPU: 2 cores
Disk: 30GB+

pfSense VM
RAM: 2GB
CPU: 2 cores
Disk: 20GB

## Purpose

The environment replicates a small enterprise SOC-monitored network for security testing and monitoring validation.
