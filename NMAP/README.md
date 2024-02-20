## Use the tool NMAP [Command line only]to perform the below task. Run Wireshark in the background and capture only the necessary packets to showcase for the corresponding question.

### a) Explain the subnet and use the NMAP Command to scan the services for the whole subnet.

A subnet, short for subnetwork, is a logical subdivision of an IP network. It allows for the division of a larger network into smaller, manageable parts. Subnetting is primarily used to improve network performance, security, and organization. Each device on a network is assigned an IP address, and subnetting helps in efficient routing of data packets within the network.

Command to scan entire subnet `nmap -sV <subnet/CIDR notation>`

Victim Machine

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/9485c422-cf7b-470c-9fa9-e402b9931bbf)

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/d648ca15-c1c6-4d59-810f-009703687a28)

### b) What is a firewall,andmention its types. Use the NMAP command to detect that a firewall protects the host.

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

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/2843b316-e77e-4a08-9cd0-a13d73cfd631)

Attacker Machine

There is no response. So it’s likely that a firewall is protecting the host
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/3e74a3d7-a37d-47b3-9130-a4761bb680c6)

Victim Machine when firewall is off
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/e7c27784-f6e1-4866-a8fa-d82b429cb0a1)

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/d86c44a8-aa22-4dbf-921e-aaead8001543)

### c) Use the NMAP command to scan a network and determine which devices are up and running.

Command - `nmap -sn <ip>/<CIDR>`

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/8af1bb5d-3a0e-4c16-a616-25778747cf95)

### d) What are vertical and horizontal scanning?

`Horizontal scanning` sends requests to the same port on different hosts. Attackers use horizontal scanning to prepare for a mass attack.
`Vertical scanning` sends requests to different ports on the same host. Attackers typically use vertical scanning to look for vulnerabilities in a preselected target.

### e) Use the NMAP command to scan multiple hosts. [HINT: Add hosts into a file and scan it].

Attacker Machine

WE need to add the ip address of the Victim Machine `192.168.213.130` to `/etc/hosts file`.
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/b787df91-e6dd-4f47-823a-b31419f40be8)

### f) Use NMAP commands to export the output in XML format.

Attacker Machine

Use the `nmap -sV <target-ip> -oX name.xml`

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/b79a7a1a-d205-4287-b9bd-79b3d1b47bff)

g) Use the NMAP command to get OS information about a host.
Attacker Machine

`nmap -O <target-ip>`

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/dc595014-873e-4718-9a98-b5d6386af4fd)

### h) Explain ping sweeping and Perform ping sweeping using Nmap

Ping Sweep
A method of network reconnaissance called "ping sweeping" is used to find out which IP addresses are active and reachable within a network. To find out which IP addresses are reachable and available, it entails sending a string of ICMP echo request messages, or pings, to a variety of addresses, usually in a sequential manner.

Network administrators frequently use ping sweeping to map the network and find active hosts.

Nmap command to perform ping sweep - `nmap -sn <network address>/<CIDR>`.

Attacker Machine

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/8af1bb5d-3a0e-4c16-a616-25778747cf95)

## Try these below questions after completing the above commands.

### 1. What is a web application firewall? How do you use Nmap to detect a WAF? Perform WAF fingerprint detection using NMAP.

A Web Application Firewall (WAF) is a security tool designed to protect web applications from various attacks, such as SQL injection, cross-site scripting (XSS), and other common web exploits. WAFs monitor and filter HTTP traffic between a web application and the Internet, identifying and blocking malicious requests before they reach the application.

To detect a WAF using Nmap, you can use its HTTP WAF fingerprinting feature. This feature sends specially crafted HTTP requests to the target web server and analyzes the responses to identify patterns that indicate the presence of a WAF.

sudo nmap --script http-waf-fingerprint <target>

Victim Machine when firewall is on

![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/2843b316-e77e-4a08-9cd0-a13d73cfd631)

Attacker Machine
![image](https://github.com/KVNuhman/cybersecurity-tools/assets/46161259/7df7b3f0-28b4-49f9-ab40-de8606304c86)
