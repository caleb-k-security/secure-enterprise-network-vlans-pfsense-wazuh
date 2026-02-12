# Wazuh Security Monitoring Deployment Report

**Author:** Caleb Kamau Kimani
**Domain:** Network Security / SOC Monitoring
**Project Type:** Enterprise Security Monitoring Deployment Lab
**Date:** 29 November 2025

---

## Executive Summary

This project demonstrates the structured deployment and validation of a Wazuh-based Security Operations Center (SOC) monitoring environment. The lab simulates how enterprise security teams implement centralized logging, endpoint monitoring, and real-time alert visibility across networked systems.

A Wazuh server was deployed on an Ubuntu virtual machine to function as the monitoring core. A Windows workstation was configured as a monitored endpoint using the Wazuh agent. The system was validated by confirming service health, secure connectivity, log ingestion, and dashboard accessibility.

The objective of this lab was not only to deploy tools, but to demonstrate operational SOC readiness through verification procedures, monitoring validation, and evidence-based reporting.

---

## Project Objectives

The implementation focused on validating real-world SOC deployment tasks:

* Deploy the Wazuh Manager, Indexer, and Dashboard services
* Verify operational status of all core monitoring components
* Enable remote analyst dashboard access
* Register and onboard a monitored endpoint
* Confirm secure communication between agent and manager
* Produce documented evidence of system functionality

---

## Environment Overview

### Monitoring Server

* Platform: Ubuntu Server (Virtual Machine)
* Function: Hosts Wazuh Manager, Indexer, and Dashboard
* Access Method: Secure web dashboard
* Service Control: Managed via systemctl service manager

---

### Analyst Workstation

* Platform: Windows system
* Role: Monitoring console + endpoint telemetry source
* Function: Sends logs and security events to Wazuh server

---

### Network Architecture

* Private virtual network environment
* Communication enabled between endpoint and server
* VirtualBox networking configured using NAT or bridged mode
* Internal addressing sanitized for security documentation

---

## Deployment Procedures

### 1. Enable Services at Boot

To ensure monitoring persistence across reboots, all Wazuh services were configured to start automatically:

```
sudo systemctl enable wazuh-indexer
sudo systemctl enable wazuh-manager
sudo systemctl enable wazuh-dashboard
```

This step ensures SOC monitoring capability remains active even after system restarts.

---

### 2. Validate Service Health

System status verification confirmed that all Wazuh components were running properly:

```
systemctl status wazuh-indexer
systemctl status wazuh-manager
systemctl status wazuh-dashboard
```

All services reported:

```
Active: active (running)
```

This indicates a fully operational monitoring stack.

---

### 3. Dashboard Access Validation

The Wazuh dashboard was accessed remotely from the analyst workstation via secure browser connection:

```
https://192.168.x.x:5601
```

Validation steps included:

* Secure connection established
* Certificate warning acknowledged
* Successful authentication
* Dashboard interface loaded

This confirmed remote monitoring capability from an analyst perspective.

---

### 4. Endpoint Agent Deployment

A Windows endpoint was enrolled to simulate enterprise endpoint monitoring.

Deployment steps:

1. Navigated to **Agents → Deploy New Agent** inside dashboard
2. Selected configuration:

   * Operating system: Windows
   * Server address: 192.168.x.x
   * Agent name: WindowsAgent01
   * Group: Windows
3. Downloaded agent installer
4. Installed agent on endpoint
5. Started agent service:

```
net start wazuh-agent
```

After activation, the endpoint appeared in the dashboard under:

```
Agents → All Agents
```

This confirmed successful registration and communication.

---

## Validation Results

All validation checks confirmed successful deployment:

* Wazuh monitoring stack installed and operational
* Endpoint agent successfully enrolled
* Dashboard accessible remotely
* Services confirmed running
* Log transmission verified
* Environment ready for detection and monitoring operations

---

## Evidence Collected

Supporting validation evidence included screenshots of:

* Successful dashboard login
* Dashboard overview interface
* Service status confirmation
* Endpoint agent connection

These artifacts demonstrate proof of deployment and system functionality.

---

## Operational Significance

This lab reflects real SOC operational processes used in enterprise environments:

* Monitoring infrastructure deployment
* Endpoint onboarding
* Service health validation
* Secure analyst access
* Centralized telemetry collection
* Documentation for audit and verification

---

## Conclusion

The Wazuh SOC monitoring environment was successfully designed, deployed, and validated. The system now supports centralized logging, real-time event monitoring, and structured alert visibility.

This project demonstrates practical SOC competencies essential for entry-level and junior security analyst roles:

* Infrastructure verification
* Endpoint monitoring deployment
* Monitoring platform validation
* Secure access configuration
* Evidence-based reporting

The completed environment reflects how production SOC monitoring platforms are implemented and verified in real enterprise networks.
