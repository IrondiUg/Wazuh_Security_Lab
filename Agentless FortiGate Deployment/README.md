### Agentless FortiGate Deployment
A PNETLab-based security monitoring lab demonstrating how to monitor a FortiGate firewall using Wazuh without installing a Wazuh agent on the firewall.

The project uses two monitoring methods:
- SSH-based Wazuh agentless monitoring
- FortiGate Syslog forwarding to Wazuh

The collected data is then made available through Wazuh Discover and can be used to build dashboards and security alerts.

### Project Overview
The goal of this project was to integrate a FortiGate firewall into Wazuh using agentless monitoring.
Because a Wazuh agent cannot be installed directly on the FortiGate, Wazuh connects to the firewall remotely over SSH and periodically executes commands to collect system information.
For security and traffic events, the FortiGate forwards Syslog messages to the Wazuh server.

This provides both:
1. Agentless system/configuration monitoring
2. Centralized firewall event monitoring

### Lab Environment

| Device | IP Address | Role |
|---|---|---|
| Wazuh Server | `192.168.100.154` | SIEM / Monitoring Server |
| FortiGate | `192.168.100.164` | Firewall |
| PNETLab | - | Network Emulation |


## Architecture

```
                    PNETLab
                       |
                       |
              +----------------+
              |    FortiGate   |
              | 192.168.100.164 |
              +-------+--------+
                      |
             +--------+--------+
             |                 |
            SSH              Syslog
             |              UDP/514
             |                 |
             v                 v
       +----------------------------+
       |       Wazuh Server         |
       |      192.168.100.154       |
       |                            |
       |  wazuh-agentlessd          |
       |  wazuh-remoted             |
       +-------------+--------------+
                     |
                     v
              Wazuh Indexer
                     |
                     v
              Wazuh Dashboard
                     |
              +------+------+
              |             |
           Discover     Dashboards
```

