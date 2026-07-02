## System Preparation

## Cowrie Honeypot Deployment
Unlike a traditional SSH server, Cowrie intentionally emulates a vulnerable Linux system. Successful logins are accepted to encourage attacker interaction and generate valuable threat intelligence. A honeypot is not designed to block attacks—it is designed to make them visible.

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


## Demonstration of Successful Honeypot Compromise


## Lab Environment

| System | Role | IP Address |
|----------|----------|----------|
| Kali Linux | Attacker | 10.0.2.15 |
| Cowrie Honeypot | SSH Honeypot | 10.0.2.5 |
| Splunk Enterprise | Log Analysis Platform | Internal Network |


### Objective

Validate that the Cowrie SSH honeypot captures and records attacker activity following a successful authentication attempt.

### Attack Simulation

Using the Kali Linux attacker machine, an SSH connection was initiated to the Cowrie honeypot listening on TCP port 2222.

```bash
ssh root@10.0.2.5 -p 2222

<img width="685" height="385" alt="image" src="https://github.com/user-attachments/assets/b57dc531-b22f-4b70-87dd-46555f9c57f0" />

The attacker attempted authentication using commonly abused credentials:

```text
Username: root
Password: password
```

Cowrie intentionally accepted the credentials and presented a realistic Linux shell environment to encourage attacker interaction and collect post-authentication telemetry.

---

## Authentication Event Captured

The following log entry confirmed successful authentication:

```text
[cowrie.ssh.userauth.HoneyPotSSHUserAuthServer#debug]
b'root' authenticated with b'password'
```

<img width="1025" height="153" alt="image" src="https://github.com/user-attachments/assets/2d7572eb-1b0a-4ed0-b878-057009f7e818" />

## Session Establishment

Following authentication, Cowrie established an interactive SSH session and presented a simulated Linux shell.

```text
[cowrie.ssh.transport.HoneyPotSSHTransport#debug]
starting service b'ssh-connection'

[cowrie.ssh.connection.CowrieSSHConnection#debug]
got channel b'session' request

[twisted.conch.ssh.session#info]
Getting shell
```

These events confirm the attacker progressed beyond authentication and was granted access to a controlled environment designed for telemetry collection and behavioral analysis.

---

<img width="1098" height="270" alt="image" src="https://github.com/user-attachments/assets/102232d2-5b32-401d-b411-0f3ecb962eba" />

## MITRE ATT&CK Mapping

### Initial Access

**T1078.001 – Valid Accounts: Default Accounts**

The attacker authenticated using common credentials (`root/password`) and gained access to the honeypot.

### Execution

**T1059.004 – Command and Scripting Interpreter: Unix Shell**

A simulated Linux shell was provided following successful authentication.

### Discovery

**T1082 – System Information Discovery**

Attackers commonly perform system reconnaissance immediately after obtaining shell access.

### Discovery

**T1083 – File and Directory Discovery**

Attackers frequently enumerate files and directories to understand the target environment.
