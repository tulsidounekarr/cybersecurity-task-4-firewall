# Cybersecurity Internship - Task 4

## Setup and Use a Firewall on Windows



### Objective



Configure and test basic Windows Firewall rules to allow or block network traffic.



### Tools Used



- Windows 11

- Windows PowerShell

- Windows Defender Firewall



### Task Performed



1. Checked the status of Windows Firewall profiles.

2. Reviewed existing Windows Firewall rules.

3. Created a temporary inbound firewall rule to block TCP port 23 (Telnet).

4. Verified that the rule was enabled and configured to block inbound traffic.

5. Tested TCP port 23 locally using `Test-NetConnection`.

6. The connection test returned `TcpTestSucceeded : False`, confirming that the connection to port 23 was unsuccessful while the blocking rule was active.

7. Removed the temporary firewall rule after testing.

8. Verified that the temporary rule no longer existed.



### Firewall Configuration



A temporary inbound rule was created to block TCP traffic on port 23.



**Rule Name:**



`Cybersecurity Task 4 - Block Telnet 23`



**Configuration:**



- Direction: Inbound

- Protocol: TCP

- Local Port: 23

- Action: Block

- Enabled: True



### Commands Used



#### 1. Check Firewall Status



powershell

Get-NetFirewallProfile | Select-Object Name, Enabled

