IP Addressing, CIDR, ARP, Routing, NAT and VLANs

## Objective

Understand how networks are divided, how traffic moves and why segmentation matters.

---

## Commands

```powershell
ipconfig /all
route print
arp -a
netstat -ano
Test-NetConnection microsoft.com -Port 443
```

---

## Evidence

### ipconfig /all

<img width="552" height="988" alt="image" src="https://github.com/user-attachments/assets/6f7b6db8-08b0-40af-a9f9-b673e4f25122" />


### route print

<img width="737" height="221" alt="image" src="https://github.com/user-attachments/assets/f84ebbc8-69d7-46cb-aa47-5383aa70b90f" />


### arp -a

<img width="622" height="499" alt="image" src="https://github.com/user-attachments/assets/aeacc113-7dbc-4cfe-a044-3ab0368e3608" />


### Test-NetConnection

<img width="411" height="126" alt="image" src="https://github.com/user-attachments/assets/46588254-2807-437e-b59d-857babb94fd2" />


---

## Findings

- Local IP: **192.168.0.17**
- Subnet: **192.168.0.0/24**
- Default Gateway: **192.168.0.1**
- DNS Server: **192.168.0.1**
- Active Connection: **192.168.0.17 → 150.171.109.214:443**
- Traffic Type: **Routed**

---

## Trust Boundary

User devices should be separated from domain controllers by a firewall to prevent unauthorised access and reduce lateral movement.

---

## Key Takeaways

- A host uses its subnet mask to determine whether traffic is local or remote.
- ARP resolves an IP address to a MAC address on the local network.
- The routing table determines where packets are sent.
- If no specific route matches, Windows uses the default route (0.0.0.0/0).
- NAT translates private IP addresses before they leave the local network.
- VLANs separate broadcast domains, while firewalls enforce security policies between them.
