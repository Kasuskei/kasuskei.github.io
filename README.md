# Aspiring IT Professional 

## Certifications
- Studying for Cisco CCNA
- Google IT Support Certification
- DoD Cyber Awareness Challenge
- Google Cybersecurity Professional Certification

## Experience
1. Created a SIEM in Microsoft Azure using Sentinel. A virtual machine was spun up and exposed to the open internet on RDP port 3389 to act as a honeypot. Accesed the virtual machine to ensure events were being logged, and that logs were being aggregated to the SIEM correctly.
2. Created and configured an Active Directory server using VirtualBox.
3. Ran a SCAP compliance scan on a virtual machine using the SCC checksum tool provided by the DISA. Created a Windows 10 STIG checklist and imported the SCAP scan results to the STIG Viewer to review and automatically remediate Not Reviewed checks.
4. Various troubleshooting labs using Cisco Packet Tracer to simulate hardware and configuration issues:
   - A laptop is powered on but not connecting to the server. The laptop is connected to APIPA IP Address 169.254.33.149. There's three network switches and an access point making up the rest of the topology. Starting with SW3, <code>show cdp neighbor</code>, <code>show int status</code>, and <code>show vlan br</code> were run to determine switch three's neighbors, which ports the server and switch 2 are connected to on switch 3, and whether VLAN is configured on switch 3. These commands showed no issue with connectivity. Moving on to SW2, <code>show span vlan 10</code> was run to determine whether or not a VLAN10 spanning tree instance exists on switch 2 or not; no such instance existed on switch 2. <code>show vlan br</code> was run next, to confirm that VLAN10 was not configured on switch 2. After confirming that VLAN10 was not configured on switch 2, <code>conf t</code> and <code>vlan 10</code> were run in that order to configure VLAN10 on switch 2.
