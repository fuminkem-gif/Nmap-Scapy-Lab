# Nmap & Scapy Lab Documentation

## 1. Introduction

This project documents my hands-on lab exercises using Nmap and Scapy Lab for network scanning, service enumeration, host discovery, OS Fingerprinting, Port Scanning and packet sniffing. The activities were performed in a controlled internal network using the target IP: 10.6.6.23.

These exercises strengthen foundational skills used in ethical hacking, penetration testing, and network security analysis.

## 2. Lab Environment
Visual Machine: Kali Linux (Ethical Hacker Kali)

Tools Used:

. Nmap

. Scapy

. Wireshark

Target Machine: `10.6.6.23`

Network Range: `10.6.6.0/24`


## 🔍3. Nmap Practical Exercises

## 3.1 Host Discovery (Ping Sweep)

Command:

```bash
nmap -sn 10.6.6.0/24
```

Purpose: Identify active hosts in the network.

Result: Host 10.6.6.23 was detected as host is up

## 3.2 Operating System Detection

Command:

```bash
sudo nmap -o 10.6.6.23
```

Purpose: Determine the target’s operating system using TCP/IP fingerprinting.

Outcome: Nmap generated an OS guess based on response patterns.

## 3.3 FTP Service & Version Detection

Command:

```bash
nmap -p21 -sV -A -T24 10.6.6.23
```

Purpose: Perform service detection, version enumeration, and additional OS fingerprinting.

Result: FTP service discovered on port 21, including version details.

## 3.4 SMB Share Enumeration

Command:

```bash
nmap --script smb-enum-shares.nse -p445 10.6.6.23
```

Purpose: Identify accessible SMB shares and check for misconfigurations.

Outcome: Lists of SMB shares were retrieved successfully.

## 3.5 Testing SMB Anonymous Login

Command:

```bash
smbclient //10.6.6.23/print$ -N
```

Purpose: Test whether SMB allows anonymous authentication.

Result: Anonymous access was allowed — a potential security weakness.

Exit SMB client: Type `exit`

## 🔬 4. Scapy Practical Exercises

All commands were executed within the Scapy interactive shell.

## 4.1 Launch Scapy

Command:

```bash
udo su

scapy
```

## 4.2 Sniffing All Network Traffic

Command:

```bash
sniff()
```

Purpose: Captures live packets on the default interfaces.

Test Traffic: Open a second terminal and run:

```bash
ping google.com
```

Store results: Scapy captured TCP, UDP, ICMP and others.

```bash
paro = _ paro.summary()
```

## 4.3 Sniffing on a Specific Interface

Command:

```bash
sniff(iface="br-internal")
```

Purpose: Captures traffic on the internal bride network.

Triggered traffic:

Visitied: `http://10.6.6.23`

. Performed additional pings

Store results:

```bash
paro2 = _

paro2.summary()
```

## 4.4 Filtering ICMP Packets

Command:

```bash
sniff(iface="br-internal", filter="icmp", count=5)
```

Test Traffic:

```bash
ping 10.6.6.23
```

Captures 5 ICMP packets

Stored and inspect packets:

```bash
paro3 = _

paro3.summary()

paro3[3]
```

## 🧠 5. Key Takeaways

Nmap reveals live hosts, services, versions, and OS fingerprints.

SMB enumeration exposed anonymous access vulnerabilities.

Scapy provides powerful packet-sniffing and protocol analysis.

Filters and interface selection improve the precision of packet captures.

Hands-on tests reinforced practical penetration testing techniques.

## 🏁 6. Conclusion

This lab improved my practical understanding of reconnaissance using Nmap and packet inspection using Scapy.
Working with real network traffic and exploring the target 10.6.6.23 helped strengthen my penetration testing and network analysis skills.
