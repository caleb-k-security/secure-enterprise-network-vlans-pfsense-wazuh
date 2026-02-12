# VLAN Segmentation and Firewall Enforcement Implementation Notes

## Overview

This document describes the implementation of network segmentation and firewall policy enforcement within a simulated enterprise environment. The objective was to design a structured internal network architecture using VLAN segmentation, inter-VLAN routing, and pfSense firewall controls to demonstrate practical network defense techniques used in real organizations.

The environment models three logical user groups — Admin, Staff, and Guest — each isolated using VLAN segmentation and controlled through firewall rules to enforce least-privilege communication.

---

## VLAN Design and Port Assignment

Three VLANs were created to logically separate network traffic:

| VLAN  | Purpose                | Example Subnet  |
| ----- | ---------------------- | --------------- |
| Admin | Administrative systems | 192.168.10.0/24 |
| Staff | Employee workstations  | 192.168.20.0/24 |
| Guest | Public/visitor network | 192.168.30.0/24 |

Switch ports were manually assigned to VLANs according to endpoint role. This segmentation ensures broadcast domains remain isolated and prevents unauthorized lateral communication between departments.

Segmentation is a foundational enterprise security control because it limits attack propagation and enforces network boundaries.

---

## Inter-VLAN Routing (Router-on-a-Stick)

Inter-VLAN routing was configured using a router-on-a-stick architecture.

In this design:

* A single router interface carries multiple VLAN networks
* Subinterfaces are created per VLAN
* Each VLAN receives a dedicated gateway IP
* Routing is centralized through the router

This allows controlled communication between VLANs while still preserving segmentation boundaries. Without router-based routing, VLANs would remain fully isolated.

---

## pfSense Firewall Deployment

A pfSense firewall was deployed inside a virtual machine to simulate enterprise network perimeter enforcement.

### Interface Configuration

Two network interfaces were configured:

| Interface | Role                        |
| --------- | --------------------------- |
| WAN       | External / upstream network |
| LAN       | Internal segmented network  |

Additional VLAN interfaces were then created within pfSense to match the internal VLAN design:

* Admin interface
* Staff interface
* Guest interface

---

## Alias Configuration

Network aliases were created to simplify firewall rule management. Aliases allow administrators to reference named networks instead of repeatedly typing IP ranges.

Defined aliases:

| Alias     | Network         |
| --------- | --------------- |
| ADMIN_NET | 192.168.10.0/24 |
| STAFF_NET | 192.168.20.0/24 |
| GUEST_NET | 192.168.30.0/24 |

Aliases improve maintainability and reduce configuration errors in large firewall rule sets.

---

## Firewall Rule Implementation

Firewall rules were applied to enforce traffic restrictions between network segments.

pfSense evaluates rules **top-down**, meaning rule order directly affects behavior. Block rules must always be placed above allow rules when enforcing restrictions.

### Rule 1 — Block Guest → Admin

* Interface: Guest
* Action: Block
* Source: GUEST_NET
* Destination: ADMIN_NET

Purpose: Prevent unauthorized guest systems from accessing administrative systems.

---

### Rule 2 — Block Staff → Admin

* Interface: Staff
* Action: Block
* Source: STAFF_NET
* Destination: ADMIN_NET

Purpose: Prevent staff endpoints from reaching administrative systems unless explicitly authorized.

---

### Rule 3 — Allow Staff → Internet

* Interface: Staff
* Action: Pass
* Source: STAFF_NET
* Destination: Any

Purpose: Allow normal internet access while still enforcing internal segmentation controls.

---

## Security Rationale

These rules demonstrate enterprise network defense principles:

* Least privilege access
* Segmentation enforcement
* Lateral movement prevention
* Internal attack surface reduction

By separating Admin resources from Staff and Guest networks, the design limits the impact of compromised endpoints.

---

## Validation and Testing Methodology

Multiple testing methods were used to confirm correct behavior.

### Connectivity Testing

Ping tests were executed from endpoints to verify expected connectivity:

* Allowed paths responded successfully
* Blocked paths timed out

---

### Firewall Log Verification

Firewall logs were reviewed within pfSense to confirm that denied traffic attempts were recorded. Logged entries proved that policy enforcement was functioning correctly.

---

### Diagnostic Testing

pfSense built-in diagnostic tools were used to validate rule effectiveness. Source interface testing confirmed that restricted VLANs could not access blocked destinations.

---

## Outcome

The network segmentation and firewall enforcement architecture functioned exactly as intended:

* VLAN isolation worked correctly
* Routing operated only where permitted
* Firewall rules enforced access control boundaries
* Logs confirmed policy enforcement

---

## Professional Significance

This implementation demonstrates core enterprise network security competencies:

* VLAN architecture design
* Firewall policy creation
* Access control enforcement
* Network segmentation strategy
* Security validation testing
* Documentation of security controls

These skills directly align with responsibilities performed by network security engineers and SOC analysts in production environments.
