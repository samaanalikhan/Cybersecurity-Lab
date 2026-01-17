# Lab 01: Network Reconnaissance with Nmap

## Objective
To identify open ports, services, and potential vulnerabilities on a target host using Nmap, while understanding the underlying TCP handshake logic.

## Technical Concept
- **Protocol:** TCP/IP
- **Scan Type:** SYN Scan (-sS)
- **Logic:** The "Half-Open" scan. We send a SYN, wait for a SYN-ACK, and then send a RST. This identifies the port as 'Open' without establishing a full connection.

## Execution (Commands)
1. **Basic Discovery:** `nmap <target_ip>`
2. **Service Version Detection:** `nmap -sV <target_ip>`
   - *Why:* To see if the version of software (like FTP 2.3.4) has known exploits.
3. **Aggressive Scan:** `nmap -A <target_ip>`

## Findings & Observations
- Found **Port 21 (FTP)** open. 
- **Risk:** FTP transmits credentials in cleartext. 
- **Next Step:** Attempt anonymous login or credential sniffing.

## Defensive Perspective (SOC)
An analyst would see a "Port Scan Detected" alert in the SIEM. The mitigation is to **Rate Limit** or **Blacklist** the source IP at the Firewall level.
