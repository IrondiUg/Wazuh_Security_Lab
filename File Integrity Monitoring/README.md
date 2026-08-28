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
