
# Cisco Agentless Deployment (Routers and Switches)

## Overview

This project documents the implementation of agentless monitoring for Cisco network devices using Wazuh.

The lab was built in a PNETLab environment with a Wazuh server running on Ubuntu Server and Cisco network devices acting as monitored infrastructure.

The monitoring approach uses Syslog rather than installing a Wazuh agent directly on the Cisco devices.

The project covers:

- Cisco router monitoring
- Cisco switch monitoring
- Wazuh Syslog configuration
- Cisco IOS log collection
- Cisco IOS log decoding
- Wazuh detection rules
- Security event monitoring
- Wazuh dashboard creation and fine-tuning
- Troubleshooting and verification
- Future Active Response implementation

---

## Objectives

The objectives of this project are to:

1. Understand agentless monitoring of network devices with Wazuh.
2. Configure Cisco routers and switches to forward Syslog messages.
3. Configure Wazuh to receive remote Syslog traffic.
4. Verify Syslog communication between Cisco devices and Wazuh.
5. Confirm Cisco IOS log decoding.
6. Monitor authentication, configuration, interface, and SSH events.
7. Create and fine-tune a Cisco security monitoring dashboard.
8. Develop custom detection rules for important Cisco security events.
9. Implement automated response mechanisms using Wazuh Active Response.

---

## Lab Environment

| Component | Details |
|---|---|
| Monitoring Platform | Wazuh |
| Wazuh Server | Ubuntu Server |
| Lab Platform | PNETLab |
| Router | Cisco IOS |
| Switch | Cisco IOSvL2 |
| Log Transport | Syslog |
| Protocol | UDP |
| Syslog Port | 514 |
| Cisco Decoder | cisco-ios |

---

## Architecture

The monitoring architecture is:

```
                    PNETLab
                       |
          +------------+------------+
          |                         |
          v                         v
     Cisco Router             Cisco Switch
          |                         |
          +------------+------------+
                       |
                    Syslog
                    UDP/514
                       |
                       v
               Ubuntu Wazuh Server
                       |
                       v
                Cisco IOS Decoder
                       |
                       v
                  Wazuh Rules
                       |
                       v
                  Wazuh Alerts
                       |
                       v
          Cisco Security Dashboard

```
---
## Cisco Syslog Configuration
Cisco devices were configured to send Syslog messages to the Wazuh server.
