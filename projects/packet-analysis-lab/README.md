Wireshark and tcpdump Lab – Detecting Reconnaissance

Project Summary:

This lab focuses on capturing and analyzing network traffic to identify early-stage attacker behavior. 
Using **tcpdump** and **Wireshark**, I generated and inspected traffic to simulate reconnaissance techniques such as endpoint probing and SYN scanning.
The idea for this lab stemmed from when I was studying for the ComptTIA Security+ exam and I the chapter on packet capturing stated most administrators use tcpdump to capture the packets and later use Wireshark to analyze.
So I decided to create a custom lab and my goal was to understand how attacker reconnaissance appears at the packet level and how to recognize it using practical analysis.

---

Tools & Environment

* Kali Linux (VirtualBox)
* tcpdump (packet capture)
* Wireshark (packet analysis)
* curl (HTTP traffic generation)
* Nmap (reconnaissance scanning)
* nc (port probing)

---

Lab Setup

* Local machine IP: `10.0.2.15`
* HTTP server: `127.0.0.1:8080`
* Network interface: `eth0`

A simple Python HTTP server was used to simulate a target application.

---

Methodology
-
1. Packet Capture

  - Traffic was initially captured using tcpdump:
  - 								sudo tcpdump -i eth0 -w threat-lab.pcap

  - When HTTP traffic was not initially visible, the capture interface was adjusted
  - 								sudo tcpdump -i any -w threat-lab-v2.pcap

---

2. Traffic Generation

	Traffic was intentionally generated to simulate normal and suspicious behavior:
- DNS lookup and ICMP (baseline connectivity)
- HTTP requests using curl
- Manual endpoint probing:
                    * `/admin`
                    * `/login`
                    * `/dashboard`

---

3. Protocol Misconfiguration Test

Attempting to connect to a plaintext HTTP server using HTTPS resulted in TLS errors and malformed requests, demonstrating protocol mismatch behavior and reinforcing the distinction between encrypted and unencrypted traffic.
I went back and reconfigured my curl request to use HTTP instead of HTTPS, allowing proper communication with the server.

---

4. HTTP Analysis in Wireshark

Filtered HTTP traffic and observed:
- Multiple GET requests to different endpoints
- Repeated `404 Not Found` responses
- Clear enumeration pattern of application routes

Putting what I was looking at into words:
          “A client at 10.0.2.15 is making an HTTP GET request to the /login endpoint using the curl command-line tool.”

---

5. Suspicious User-Agent Detection

  - Filter used:
  - 							http.user_agent contains "Recon-Bot"

  - Identified:
  - 							User-Agent: Recon-Bot/1.0
    * This indicated automated traffic rather than just a normal browser.

---

6. SYN Scan Detection (Nmap)

  - Filter used:
  - 							tcp.flags.syn == 1 and tcp.flags.ack == 0
Findings
  - Large number of SYN packets
  - Multiple destination ports targeted
  - No completed TCP handshakes

This behavior matches what would be seen in a:
	- *Nmap SYN scan (-sS)

---

Key Observations

* Endpoint enumeration via repeated HTTP requests
* Presence of a non-standard User-Agent (`Recon-Bot`)
* High volume of incomplete TCP connections
* "Conversation completeness: Incomplete"
* Evidence of active reconnaissance using SYN scanning

---

Analysis

  - The traffic captured in this lab reflects a typical attacker workflow:
1. Identify reachable services
2. Probe application endpoints
3. Scan for open ports

Strong indicators of recon activity:
  - abnormal User-Agent strings
  - repeated failed HTTP requests
  - incomplete TCP handshakes

---

Skills Demonstrated
* Packet capture with tcpdump
* Traffic analysis with Wireshark
* HTTP request inspection
* TCP flag analysis
* Identifying reconnaissance patterns
* Troubleshooting capture issues

---

Screenshots

All supporting screenshots are available in the `/screenshots` directory and demonstrate each stage of the analysis process.

---

Conclusion

  This lab was my first hands-on experience working with packet captures and network traffic analysis. Going through the process of generating traffic, troubleshooting capture issues, and interpreting what I saw in Wireshark helped me move beyond theory and start understanding how network activity actually looks in practice.

One of the biggest takeaways was learning how small details—like HTTP request patterns, User-Agent strings, and TCP flags—can reveal meaningful insights about behavior on a network. What initially looked like raw, unreadable data became much more structured once I applied the right filters and broke things down step by step.

This experience showed me that packet analysis isn’t just about reading packets, but about identifying patterns and connecting them to real-world activity, such as reconnaissance and scanning. It also reinforced the importance of troubleshooting and adapting when things don’t work as expected, which was a key part of completing this lab.

Overall, this project gave me a solid foundation in network traffic analysis and a better understanding of how attackers operate during the early stages of an intrusion.

