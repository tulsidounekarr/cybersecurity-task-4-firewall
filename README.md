# Cybersecurity Internship - Task 4

## Setup and Use a Firewall on Windows

### Objective

The objective of this task was to configure and test basic Windows Firewall rules to allow or block network traffic. The task demonstrates how firewall rules can control inbound traffic based on protocols and ports.

### Operating Environment

- **Operating System:** Windows 11
- **Firewall:** Windows Defender Firewall
- **Tool:** Windows PowerShell
- **Protocol Tested:** TCP
- **Test Port:** 23 (Telnet)
- **Test Target:** Localhost

### Task Overview

The following activities were performed as part of the task:

1. Checked the status of Windows Firewall profiles.
2. Reviewed existing Windows Firewall rules.
3. Created a temporary inbound firewall rule to block TCP traffic on port 23.
4. Verified the configuration of the newly created firewall rule.
5. Tested connectivity to TCP port 23 using `Test-NetConnection`.
6. Confirmed that the TCP connection was unsuccessful while the blocking rule was active.
7. Removed the temporary firewall rule after completing the test.
8. Verified that the temporary firewall rule no longer existed.

### Firewall Status

The Windows Firewall profiles were checked using PowerShell:

```powershell
Get-NetFirewallProfile | Select-Object Name, Enabled
```

This command was used to verify whether the Domain, Private, and Public firewall profiles were enabled.

### Existing Firewall Rules

Existing Windows Firewall rules were reviewed using:

```powershell
Get-NetFirewallRule | Select-Object DisplayName, Direction, Action, Enabled
```

The command displays information such as:

- Firewall rule name
- Traffic direction
- Allow or Block action
- Rule status

### Firewall Rule Configuration

A temporary inbound firewall rule was created to block TCP traffic on port 23.

**Rule Name:**

`Cybersecurity Task 4 - Block Telnet 23`

**Configuration:**

| Setting | Value |
|---|---|
| Direction | Inbound |
| Protocol | TCP |
| Local Port | 23 |
| Action | Block |
| Enabled | True |

The rule was created using:

```powershell
New-NetFirewallRule -DisplayName "Cybersecurity Task 4 - Block Telnet 23" -Direction Inbound -Protocol TCP -LocalPort 23 -Action Block
```

The `New-NetFirewallRule` PowerShell cmdlet creates an inbound or outbound firewall rule and allows parameters such as direction, protocol, port, and action to define the traffic that the rule applies to.

### Rule Verification

The created rule was verified using:

```powershell
Get-NetFirewallRule -DisplayName "Cybersecurity Task 4 - Block Telnet 23" | Select-Object DisplayName, Direction, Action, Enabled
```

The expected configuration was:

```text
Direction : Inbound
Action    : Block
Enabled   : True
```

### Testing the Firewall Rule

The local TCP port was tested using:

```powershell
Test-NetConnection -ComputerName localhost -Port 23
```

The test produced:

```text
TcpTestSucceeded : False
```

This indicated that the TCP connection to port 23 was unsuccessful while the test blocking rule was active.

The test was performed against `localhost`, keeping the activity within the user's own computer.

### Rule Removal

After completing the test, the temporary firewall rule was removed using:

```powershell
Remove-NetFirewallRule -DisplayName "Cybersecurity Task 4 - Block Telnet 23"
```

The rule was then checked again to verify that it no longer existed.

```powershell
Get-NetFirewallRule -DisplayName "Cybersecurity Task 4 - Block Telnet 23" -ErrorAction SilentlyContinue
```

No matching rule was returned, confirming that the temporary test rule had been removed.

Microsoft documents `Remove-NetFirewallRule` as the cmdlet used to permanently remove a specified firewall rule from the local policy store.

### How a Firewall Filters Traffic

A firewall controls network traffic by applying configured rules to connections. Rules can specify characteristics such as:

- Inbound or outbound direction
- Protocol such as TCP or UDP
- Local or remote port
- Source or destination address
- Allow or Block action

In this task, an inbound rule was configured to block TCP traffic on local port 23. When the connection was tested, the TCP connection did not succeed.

Windows Firewall supports separate Domain, Private, and Public profiles, allowing firewall behavior to be configured according to the network profile.

### Security Significance of Port 23

Port 23 is commonly associated with Telnet. Telnet is an older remote-access protocol that does not provide the same level of security as modern encrypted remote-access protocols.

Blocking unnecessary or insecure services can reduce the attack surface of a system.

### Key Concepts Learned

- Windows Defender Firewall
- Firewall Profiles
- Inbound Traffic
- Outbound Traffic
- TCP
- Network Ports
- Firewall Rules
- Traffic Filtering
- Allow and Block Actions
- Telnet
- PowerShell Firewall Management
- Network Security

### Results

The firewall configuration and testing were completed successfully.

The task demonstrated that:

- Windows Firewall profiles can be inspected using PowerShell.
- Firewall rules can be created for specific traffic conditions.
- Inbound TCP traffic can be blocked for a specific port.
- Connectivity can be tested using `Test-NetConnection`.
- Temporary firewall rules can be removed after testing.

The temporary TCP port 23 blocking rule was removed after testing, restoring the previous firewall configuration.

### Screenshots

The `screenshots` directory contains evidence of the task:

1. **01-firewall-and-rule.png** — Firewall/rule configuration
2. **02-rule-removed.png** — Verification that the temporary rule was removed
3. **03-port-23-test.png** — TCP port 23 connectivity test showing `TcpTestSucceeded : False`

### Conclusion

This task provided practical experience with Windows Firewall configuration and network traffic filtering. A temporary inbound TCP port 23 blocking rule was created, tested locally, verified, and removed successfully.

The exercise demonstrated how firewall rules can be used to control network traffic and improve the security posture of a Windows system.

### Author

**Tulsi R. Dounekar**


Cyber Security Internship - Task 4

GitHub: [tulsidounekarr](https://github.com/tulsidounekarr)
