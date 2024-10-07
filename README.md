# Aspiring IT Professional 

## Certifications
- Studying for Cisco CCNA
- Google IT Support Certification
- DoD Cyber Awareness Challenge
- Google Cybersecurity Professional Certification

## Experience (Work in progress: this section will be continuously updated as more labs are completed)
1. Created a SIEM in Microsoft Azure using Sentinel. A virtual machine was spun up and exposed to the open internet on RDP port 3389 to act as a honeypot. Accesed the virtual machine to ensure events were being logged, and that logs were being aggregated to the SIEM correctly.
2. Created and configured an Active Directory server using VirtualBox.
3. Ran a SCAP compliance scan on a virtual machine using the SCC checksum tool provided by the DISA. Created a Windows 10 STIG checklist and imported the SCAP scan results to the STIG Viewer to review and automatically remediate Not Reviewed checks.
4. Various troubleshooting labs using Cisco Packet Tracer to simulate hardware and configuration issues:
   - A laptop is powered on but not connecting to the server.
        - The laptop is connected to APIPA IP Address 169.254.33.149. There's three network switches and an access point making up the rest of the topology. Starting with SW3, <code>show cdp neighbor</code>, <code>show int status</code>, and <code>show vlan br</code> were run to determine switch three's neighbors, which ports the server and switch 2 are connected to on switch 3, and whether VLAN is configured on switch 3. These commands showed no issue with connectivity.
        - Moving on to SW2, <code>show span vlan 10</code> was run to determine whether or not a VLAN10 spanning tree instance exists on switch 2 or not; no such instance existed on switch 2. <code>show vlan br</code> was run next, to confirm that VLAN10 was not configured on switch 2. After confirming that VLAN10 was not configured on switch 2, <code>conf t</code> and <code>vlan 10</code> were run in that order to configure VLAN10 on switch Next, <code>show cdp neighbor</code> was run to confirm VLAN 10 was running through switch 2 and 3.
        - Finally, moving on to SW1, <code>show span vlan 10</code> is run showing VLAN10 is not configured on switch 1. Next, <code>conf t</code> and <code>vlan 10</code> are run in that order to configure VLAN10 on switch <code>show vlan br</code> is run to confirm VLAN10 has been added to the switch's VLAN database, and <code>show span vlan 10</code> is run to show where the spanning tree BPDUs are going. That's been confirmed, and <code>show vdp neighbors</code> is run to confirm that switch 1 is connected to its neighboring devices correctly. Running <code>show vlan br</code> earlier showed that switch 1 had no access ports in VLAN10, meaning that while switch 1 might be properly connected to its neighboring devices, there's still no network connectivity running through the entire topology. <code>show int trunk</code> shows that the only trunk port on switch 1 is Fa/02, which connects to switch 2. The port the access point is connected to is an access port, but it is not in VLAN10. Running <code>show run | s interface</code> confirms this by showing connections between switch 1 and its neighbors; Fa/01, which connects switch 1 to the access point, shows no configuration, which would indicate it's at its default configuration, while Fa/02, which connects switch 1 to switch 2, is a trunk port. 
