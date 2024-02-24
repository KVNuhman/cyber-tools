## TOOL USED HERE

### ETTERCAP

Ettercap is a comprehensive, open-source network security tool used for analyzing, monitoring, and manipulating network traffic in a computer network. Originally developed for Unix-like operating systems, it has since been adapted for Windows as well. Ettercap operates as a man-in-the-middle (MITM) attack tool, allowing cybersecurity professionals, penetration testers, and ethical hackers to inspect and modify data as it passes through a network.

### Familiarization with tool

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/c925e528-b037-416f-bbd9-e0d9f40a41e7)

So here we set the interface on which have to start sniffing and related attacks. Then we start sniffing on the interface.

## ARP Cache Poisoning

ARP spoofing is the process of linking an attacker’s MAC address with the IP address of a legitimate user on a local area network using fake ARP messages. As a result, data sent by the user to the host IP address is instead transmitted to the attacker.

### CAUSE OF ATTACK

The main cause of ARP spoofing attacks is the fundamental trust issue within the Address Resolution Protocol (ARP) itself. ARP is a network communication protocol that helps devices translate IP addresses, which are easy for humans to remember, into MAC addresses, which are the unique identifiers used by network devices.

### PREVENTION

We can prevent it by implementing the IDS(Intrusion detection system).
Using the Arp-spoof detecting software.

### PERFORMING THE ATTACK

First we discover all the hosts and choose the target on which we want to perform ARP spoofing attack.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/8abf25bb-0c56-488d-b871-3c4e8b0e35ce)

To find the Victim gateway.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/f23502a5-0775-4bcc-b02c-8f5a42c77964)

So here the target is 192.168.21.128 and the target gateway is 192.168.21.2

Then we perform the ARP poisoning attack

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/e62d5c8f-2abc-441d-b7c2-bb39c231ba25)

Now we can see that we are able to see the traffic. So our attack is successful.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/bed044a2-5029-4097-afa0-51c606d31cfb)

When analyze the Splunk reports we can see that http request was successful but there was no sign of showing ARP spoof.

## Perform Denial of Service (DoS) attacks using ARP Cache Poisoning attacks.

The DoS (Denial of Service) attack plugin in ettercap is used to overload a target system or network with traffic in order to prevent the system or network from operating normally. This attack aims to prevent authorised users from accessing the target system or network. The way the DoS attack plugin in ettercap operates is by flooding the target with a lot of network traffic. Requests sent over the network, such as HTTP or DNS inquiries, might be considered genuine traffic.

As like the previous steps,

Scan for hosts

Add hosts as target (only the target ip & not the gateway ip)

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/ffbc16e0-a668-4ec0-b365-e79879142357)

Start arp poisoning the victim.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/cd343bff-c91a-484b-a10a-059ef3c6db3d)

And now run the dos_attack plugin.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/4a1abc86-03a1-4974-9eb2-e394c7f68198)

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/0eb005c5-8a27-4b78-ac77-66795e514ed2)

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/ae79726c-674c-42aa-a9e5-ad6e2ef84f62)

IN victim Machine.

The victim becomes sluggish as soon as we enable the plugin since the target IP starts sending the victim a large number of packets. Therefore, the victim's web searches just never stop loading.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/0360470a-f9e1-45ce-ad88-7559d89af52b)

## Perform DNS Spoofing attack using ARP Cache Poisoning attacks

When the ettercap DNS spoofing plugin is activated, it eavesdrops on the victim's DNS queries and replies with a phoney DNS response that includes a phoney IP address. The attacker's computer IP address or any other IP address they want the victim to visit is this false IP address. The victim's DNS queries are picked up by the ettercap DNS spoofing plugin. After capturing a request, the plugin sends the victim's computer a fictitious DNS answer that includes the attacker's IP address or any other address they may have chosen.

First we need go to
`mousepad /etc/ettercap/etter.conf`
we need set the ec_uid = 0, ec_gid = 0

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/ea75098a-bc29-4cf7-86da-713382f774ab)

we have remove the hashes from linux category

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/59ce5dc3-be35-476d-a482-9b106b37b3d2)

then go to `mousepad /etc/ettercap/etter.dns`
and the domain that we need spoof and add the ip of the attcker system

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/822f819e-0458-4f3a-ae06-a23dc57db176)

after confguring both this file we need start our own apache server before that go to `cd /var/www/html` and modify index.html.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/b3a748db-f878-4890-969a-585c485a6ecc)

and then start apache server `service apache2 start`.And no go to `ettercap -G`.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/983d7851-a5f6-468c-92fd-3cd69e0aa2da)

after starting after few seconds we need to press the stop on the bottom left side.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/2493767e-066c-4d60-a429-90b944bde8a7)

after that we need scan for the network which means the connected device ans will display some host lists.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/2446906a-ba80-4367-8416-5bd2c5f0243b)

then we need go to the host list and we need all the hosts in target 1 or target2.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/ce5bcdda-7abd-4a3a-9bc8-1ffa82cb89ec)

and go to plugins and select mange plugins the click on dns spoffing and it will show activating it.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/267d6827-0eda-4081-aa34-0f43e41c5558)

then select arp spoffing and click ok.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/79b15e88-bc0f-426b-80cc-77b3374e8259)

and go to victims machine and check if the attack is sucessfull.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/74c36154-7a6d-403d-bd65-e587dec87e86)

IDENTIFY THE SOURCE OF THE ATTACK JUST BY USING SPLUNK LOGS

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/8205f5e5-a766-4df3-9c25-bdb394ac57b8)

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/e6778b1a-c93c-4bd4-b4b2-750fa9fabe27)

## ICMP redirect (ARP poisoning)

Now, open Ettercap and start host scanning then, add victim’s IP to target 1 and default gateway to
target 2

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/d4c90c7e-7de9-4813-87f4-d7dd9ac54dab)

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/5b9cd8ab-bd3a-443d-a19b-a2f336a871ff)

After adding the respective hosts as targets start Arp poisoning. And after starting ARP poisoning simultaneously run the Wireshark in the background.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/d787c234-fab6-48a8-97fb-5d436270d516)

Choose icmp redirect and add the mac address and ip address of the default gateway.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/bbb3ba83-0c82-48b7-a39f-a899df73bbe1)

As we can see , the redirected message displayed in wireshark.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/37f78c2e-63e4-4417-82b6-8e535415bb5f)
