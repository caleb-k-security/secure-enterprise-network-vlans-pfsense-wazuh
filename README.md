# secure-enterprise-network-vlans-pfsense-wazuh
Enterprise-style network segmentation (VLANs), firewall enforcement (pfSense), and centralized security monitoring using Wazuh SIEM.

# Design and Implementation of a Secure Enterprise Network with VLAN Segmentation, pfSense Firewall Enforcement, and Wazuh SIEM Monitoring

## Overview
This project demonstrates the design and deployment of a secure enterprise-style network environment. The lab includes VLAN segmentation (Admin/Staff/Guest), inter-VLAN routing, firewall policy enforcement using pfSense, and centralized security monitoring using Wazuh SIEM.

The goal was to implement realistic network security controls and validate SOC operational readiness through service health checks, agent onboarding, and evidence-based reporting.

## Objectives
- Build a segmented enterprise network using VLANs and inter-VLAN routing
- Enforce security boundaries using pfSense firewall rules and aliases
- Deploy Wazuh SIEM (Manager/Indexer/Dashboard) for centralized monitoring
- Onboard a Windows endpoint using the Wazuh agent
- Validate SOC operational health and document evidence (screenshots + report)

## Architecture (High-Level)
- **Network Segmentation:** VLANs for Admin / Staff / Guest
- **Firewall Enforcement:** pfSense (WAN/LAN + VLAN interfaces, rule evaluation)
- **SIEM Monitoring:** Wazuh server on Ubuntu (Manager + Indexer + Dashboard)
- **Endpoint Visibility:** Windows endpoint enrolled as Wazuh agent
- **Delivery:** VirtualBox + Packet Tracer (lab simulation)

## What I Implemented
### 1) VLAN Segmentation (Packet Tracer)
- Designed topology with router + switches + endpoints
- Created Admin, Staff, and Guest VLANs
- Configured inter-VLAN routing (router-on-a-stick)
- Validated connectivity and segmentation behavior

### 2) pfSense Firewall Enforcement
- Deployed pfSense with WAN + LAN interfaces
- Created VLAN interfaces (Admin/Staff/Guest)
- Built aliases for clean reusable firewall policy
- Implemented and tested rules such as:
  - Block Guest → Admin access
  - Restrict Staff access to prevent Admin VLAN access while allowing internet

### 3) Wazuh SIEM Monitoring Deployment
- Deployed Wazuh stack (Manager/Indexer/Dashboard) on Ubuntu
- Verified services running and enabled at boot
- Accessed dashboard securely from analyst workstation
- Deployed and confirmed Windows agent enrollment

## Evidence Included
- Lab report (executive summary + objectives + results)
- Screenshots: dashboard access, service status, agent connected
- Diagrams: Wazuh architecture and log/alert flow (sanitized)

## Professional Note
This repository excludes sensitive artifacts (credentials, installers, binaries). Documentation uses placeholders where appropriate to prevent exposing internal details.

## Author
**Caleb Kamau Kimani** - SOC Analyst (Tier-1) / Network Security & SIEM Monitoring
