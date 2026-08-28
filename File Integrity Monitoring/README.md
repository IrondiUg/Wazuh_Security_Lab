### Wazuh File Integrity Monitoring (FIM)
The lab consists of: 
- A **Wazuh Manager** running on Ubuntu Server
- A **Windows endpoint** with a Wazuh Agent installed
- An **Ubuntu Desktop endpoint** with a Wazuh Agent installed
- The **Wazuh Dashboard** for security event monitoring and investigation .

The Wazuh agents were configured to monitor specific directories for file-system changes. 
The tests performed included: 
- File creation
- File modification
- File deletio
- File integrity/hash changes

Real-time monitoring The resulting events were forwarded from the endpoints to the Wazuh Manager and investigated through the Wazuh Dashboard.

### How FIM Works
File Integrity Monitoring is used to detect unauthorized or unexpected changes to files and directories.
In this implementation, the Wazuh Agent performs the monitoring directly on each endpoint.

When a monitored file changes:
```
                 FILE SYSTEM
                      │
                      ▼
              File is modified
                      │
                      ▼
              Wazuh Agent
              └── Syscheck
                      │
                      ▼
                  FIM Event
                      │
                      ▼
                Wazuh Manager
                      │
                      ▼
               Rule Analysis
                      │
                      ▼
                Alert Event
                      │
                      ▼
               Wazuh Dashboard
```

