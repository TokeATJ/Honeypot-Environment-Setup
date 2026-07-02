## System Preparation

## Cowrie Honeypot Deployment

Successfully deployed a Cowrie SSH honeypot on Ubuntu Server to simulate a vulnerable SSH service and collect attacker telemetry.

Before deploying the honeypot, a dedicated service account was created and granted administrative privileges. The Ubuntu host was renamed to `cowrie-honeypot` to separate it from the existing Splunk infrastructure and provide a clean environment for cyber deception activities.

<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/3f0e445f-272f-4838-a5f1-8af8146a29e6" />

Validated Cowrie successfully installed on port 2222

<img width="1365" height="879" alt="image" src="https://github.com/user-attachments/assets/1cae3772-8703-429b-9266-97ab5b3f9959" />


### Key Activities

- Created dedicated `cowrie` service account
- Renamed host to `cowrie-honeypot`
- Configured Python virtual environment
- Installed Cowrie from source
- Resolved dependency and configuration issues
- Initialized Cowrie configuration
- Started honeypot service
- Validated SSH listener on TCP 2222

### Skills Demonstrated

- Linux Administration
- Python Environment Management
- Open Source Security Tool Deployment
- Cyber Deception Engineering
- Troubleshooting & Configuration Management
