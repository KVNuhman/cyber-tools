# Learn the basic working of Wi-Fi and its types with various types of attacks on it.

## Basic Working of WiFi

Radio Signals:Radio waves are used to transport data in WiFi networks. Within a WiFi network, devices exchange radio signals with one another.

Wi-Fi connections are centralised around Access Points (APs). They transfer data to other devices on the network after receiving it from linked devices.

Network Identification: The name of the network, or Service Set IDentifier (SSID), is how WiFi networks are recognised.

Authentication and Encryption: When a device connects to a WiFi network, it undergoes an authentication process to verify its identity. WiFi protocols such as WPA2 or WPA3 are used to secure data transmissions over the network.

# Types of WiFi

802.11 b/g/n: These are older WiFi standards operating primarily in the 2.4 GHz frequency band. They offer relatively slower speeds compared to newer standards.

802.11 ac: Also known as WiFi 5, this standard operates in both the 2.4 GHz and 5 GHz bands, providing faster speeds and improved performance compared to older standards.

802.11 ax: Also referred to as WiFi 6, this is the latest WiFi standard offering even higher speeds, lower latency, and improved efficiency, especially in high-density environments.

# Types of WiFi Attacks

Eavesdropping (Passive Attacks): Attackers can intercept WiFi signals to capture sensitive information such as passwords or financial data without actively engaging with the network.

Man-in-the-Middle (MITM) Attacks: In this type of attack, the attacker intercepts communication between two parties, potentially altering or eavesdropping on the data being transmitted.

Brute Force Attacks: Attackers attempt to crack WiFi passwords by systematically trying all possible combinations until they find the correct one.

Evil Twin Attacks: Attackers set up rogue access points with the same SSID as a legitimate network, tricking users into connecting to it and potentially exposing their data.

Denial of Service (DoS) Attacks: Attackers flood a WiFi network with an overwhelming amount of traffic, causing it to become unavailable to legitimate users.

WPS Vulnerabilities: WiFi Protected Setup (WPS) is a feature that simplifies the process of connecting devices to a WiFi network, but it can also introduce security vulnerabilities if not properly configured, allowing attackers to gain unauthorized access.

# Connect the wireless adapter

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/4cd624ad-18f4-4a3a-86c2-d0d10b643360)


> We enable monitor mode in the adapter in the adapter.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/7a6109ee-e692-4e69-aa48-1715f2918152)

## Perform Wi-Fi fingerprinting

### Wifite 

> we swtich to `sudo` user and start wifite and scan the wifi network the around the area

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/40887588-5320-4fba-a655-bda03a21ebeb)

> So we can see it shows all the available networks and how many clients are connected to it.

# Create an Access point with any Wi-Fi encryption standard and start testing the security of that connection using any Wi-Fi security testing tools, which should include (Aircrack-Ng, Wifite, not limited). Try to capture the 4-way handshake using these methods.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/f66f3059-2e99-4f22-80c7-ce59f8454ecb)

> So our target here `Target ` so we will be attacking this network and it's using the `wpa-p`

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/da0be388-5c81-452b-8c40-f457c19b906f)

> So it 1 deauthenticate the clients in that is connected to target network try to capture the handshake.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/a64ac71c-bcd5-4b92-8c4b-15cac0e921e4)

> It saves it as a pcap file and try to crack the password using the specified wordlist and we can see the key after cracking the i.e `12345678`.

> So we try analyze the wireshark pcap that is saved along with this we can see that the 4 hand shake was captured.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/4b88ed9e-522d-4eb1-b123-385a4a407bdb)

## Also you have to create your dictionary file for cracking the passwords.

To generate a wordlist, we can use the crunch command.

`crunch 8 12 012345678abcdefghijklmnopqrstuvwxyz -o wordlist.txt`

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/50dee5a4-377c-40ea-a397-2a1adef4382b)

# Use Rouge AP (WifiPhisher) to create an Evil twin, perform a basic phishing attack using this rouge AP, and document the difference between the two attacks you have performed.

> We have install `WifiPhisher`. `sudo apt install WifiPhisher`

 When run `WifiPhisher` we have to select which wifi fake have to create.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/ce3690ef-c263-4de0-9d6d-95ed8099820b)


> We have to select what phishing we have to perform i have select auth login

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/5810c07b-44f8-4f94-b598-5a12fa6c9d21)

> So with help of `WifiPhisher` we created fake Amrita wifi and we will try to connect ot it.

![image](https://github.com/ananthan05/Cyber-Security-/assets/140697378/953a21d2-1666-4f9c-9efd-c771a39ff9a4)


> So as soon as the andriod device is connected it shows in the screen.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/012f5357-2be8-4100-97de-26f3d69ce0fa)

> And in the andriod device we are getting web page asking for password.

![WhatsApp Image 2024-02-24 at 21 06 42_2854b01c](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/917fd153-a0a7-40df-948e-100826445616)

> And we enter the password in the website it reflected back when we close the tool.

![image](https://github.com/anandurdas11/Exploring_Cyber_security/assets/83402050/ed620ff2-629e-494b-abb6-ccea7ae5e9b4)


# Learn the protocol level working of WPA3 and how it differs from WPA2.
WiFi Protected Access 3 (WPA3) is the security protocol for WiFi networks succeeding WPA2. It enhances the security features and addresses some of the security vulnerabilities provided by WPA2.

Key Establishment and Authentication
WPA3 introduced a handshake protocol called Simultaneous Authentication of Equals (SAE), which is based on DragonFly Key Exchange Protocol. This mitigated the vulnerabilities present in WPA2's four way handshake, hence making the WPA3 resistant to offline dictionary attacks and password guessing attacks.

Encryption
WPA3 introduced support for Galois Counter Mode (GCMP). This offers similar security to Chaining Message Authentication Code Protocol (CCMP) but is more efficient in terms of processing power, which can improve battery life of the devices.

Protection against Brute Force Attacks
WPA3 incorporated stronger protections against brute force attacks through the use of hash to group feature in the DragonFly handshake protocol. This made it significantly harder for attackers to guess the passphrase by making repeated brute force attempts.

Forward Secrecy
WPA3 offers perfect forward secrecy ensuring that even if an attacker were to compromise the network's security key in the future, they would not be able to decrypt past data transmitted in the network.
