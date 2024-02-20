## Use the tool NMAP [Command line only]to perform the below task. Run Wireshark in the background and capture only the necessary packets to showcase for the corresponding question.
a) Explain the subnet and use the NMAP Command to scan the services for the whole subnet.
A subnet, short for subnetwork, is a logical subdivision of an IP network. It allows for the division of a larger network into smaller, manageable parts. Subnetting is primarily used to improve network performance, security, and organization. Each device on a network is assigned an IP address, and subnetting helps in efficient routing of data packets within the network.

Command to scan entire subnet `nmap -sV <subnet/CIDR notation>`

Victim Machine

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/7cda7c05-25e9-4208-9ab9-ae38673bc415)

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/146e5958-f0c2-4f38-9996-e173d9bd4c82)



b) What is a firewall,andmention its types. Use the NMAP command to detect that a firewall protects the host.
Firewall
A firewall is a type of network security appliance that keeps an eye on and regulates inbound and outgoing network traffic in accordance with pre-established security rules. Its main goal is to defend devices and networks from malicious activity, assaults, and unauthorised access. It is possible to deploy firewalls using hardware, software, or a combination of the two. They function by looking at network traffic packets and comparing them to the administrator's preset rules or policies.

A packet is permitted to get across the firewall if it matches a rule. If it doesn't fit any of the rules, it's either rejected or forwarded to another place for more examination.

firewall types
Software firewall.
Hardware firewall.
Packet filtering firewall.
Circuit-level gateway.
Proxy service application firewall.
The NMAP command to detect if a host is protected by a firewall. Here’s an example of how you might do this:
`nmap -sS -p- <target-ip>`

In this command:

`-sS` option tells NMAP to perform a SYN scan, which is a type of stealth scan. -p- option tells NMAP to scan all 65535 ports. This command will send a TCP SYN packet to each port on the target host. If the port is open, the target will respond with a SYN/ACK packet. If the port is closed, the target will respond with a RST packet. If there is no response, or the packet is dropped, it’s likely that a firewall is protecting the host.

Victim Machine when firewall is on

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/b59deea9-7a0e-490f-b4ab-af474857cb39)

Attacker Machine

There is no response. So it’s likely that a firewall is protecting the host
`need to add image`

Victim Machine when firewall is off
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/4f1f809d-f044-4919-8a65-a449dc3cd946)

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/4b853148-4b7b-4501-84fb-32c2b53a59fa)

c) Use the NMAP command to scan a network and determine which devices are up and running.
Command - nmap -sn <ip>/<CIDR> 

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/c37a3e67-8b40-4ab7-9f14-0577fe7b2648)

d) What are vertical and horizontal scanning?
`Horizontal scanning`  sends requests to the same port on different hosts. Attackers use horizontal scanning to prepare for a mass attack.
Vertical scanning` sends requests to different ports on the same host. Attackers typically use vertical scanning to look for vulnerabilities in a preselected target.
e) Use the NMAP command to scan multiple hosts. [HINT: Add hosts into a file and scan it].
Attacker Machine

WE need to add the ip address of the Victim Machine `192.168.213.130` to `/etc/hosts file`.
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/49506d0c-9d4e-41d3-8770-1454d8499e68)

f) Use NMAP commands to export the output in XML format.
Attacker Machine

Use the `nmap -sV <target-ip> -oX name.xml`

