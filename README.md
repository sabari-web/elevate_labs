1.Find Your Local IP Range: cmd -ipconfig
2. Run the Nmap Scan - nmap -sS 10.0.2.0/24 -oN task1.txt
3.Analyze with Wireshark -ip.addr == 10.0.2.4 ||tcp
4.open ports
(1)IP: 10.0.2.1
Open Port: 53/tcp
Service: domain (DNS)
(2) IP: 10.0.2.2
Open Ports:
135/tcp – msrpc
445/tcp – microsoft-ds (SMB)
912/tcp – apex-mesh
10.0.2.3 – No open ports (all filtered)
10.0.2.4 – No open ports (all closed)
5.Analyse the wireshark 
output is attached 
6.Research common services running on those ports.
7.Identify potential security risks from open ports.
Host: 10.0.2.1
Open Port: 53/tcp
Service: domain (DNS)
Common Use:
Port 53 is used by DNS servers to handle domain name lookups.
Potential Risks:
DNS Amplification Attacks if misconfigured.

Zone Transfers can leak internal records if allowed.

Can be abused for DNS tunneling 

Host: 10.0.2.2
Open Ports:

135/tcp - msrpc

445/tcp - microsoft-ds

902/tcp -iss-realsecure (or VMware remote console)

 Common Use:
135/tcp (MSRPC): Used by Windows RPC services.

445/tcp (Microsoft-DS): SMB file sharing in Windows.

902/tcp: Used by VMware for remote management.

Potential Risks:
135/tcp: Vulnerable to RPC DCOM exploits (e.g., used by malware/worms like Blaster).

445/tcp:

Target of many attacks (e.g., EternalBlue — WannaCry).

Can allow remote code execution or unauthorized file access.

902/tcp:

Can expose VMware services to attacks if not secured.

Might allow remote access or control of VMs.



