# DNS Resolution Analysis Using Wireshark

## Objective

Observe how DNS resolves a domain name into an IP address and understand nthe trust relationship involved in DNS communication.


# Tools Used

1.  Wireshark
2.  Windows Powershell

# Commands Used

```powershell
ping google.com
tracert google.com
nslookup firefox.com
Test-NetConnection firefox.com -Port 443
```

---

# Wireshark Filter

```text
dns
```

---

# Findings

## Queried Domain

```text
firefox.com
```

Standard query requested the DNS A record for firefox.com.

---

## Returned IP Address

```text
35.190.14.201
```

DNS returned the IPv4 address for firefox.com.

---

## Protocol Involved

```text
DNS
```

DNS translated the domain name into an IP address.

---

## Resolution Summary

| Item | Value |
|--------|--------|
| Domain Queried | firefox.com |
| Returned IP Address | 35.190.14.201 |
| DNS Server | fd6f:9f0e:a913:6:681:9bff:fe36:7be |
| Destination Port | 443 (HTTPS) |
| Connectivity Succeeded | Yes (`TcpTestSucceeded : True`) |

## Trust Statement

The client trusted the DNS server to provide the correct IP address for firefox.com and then used that IP address to establish communication over HTTPS.

## Trust Statement

The client trusted the DNS server to provide the correct IP address for firefox.com and then used that IP address to establish communication over HTTPS.


---

## Trust Relationship

1. Client requested DNS record for firefox.com
2. DNS server responded with IP address
3. Client trusted the DNS response
4. Browser used returned IP for communication

---

# Security Relevance

DNS is a trust system.

Attackers abuse DNS through:
1. DNS spoofing
2. Phishing
3. Malware callbacks
4. Command-and-control traffic

---

## Key Lesson

DNS does not verify the truth.

The client trusts that the DNS server provides the correct IP address. If that trust relationsip is compromised for any reason, users will be redirected to malicious infrastructure without realising it.

Understanding DNS is ultimately fundamntal to networking, security engineering, System engineering and Zero Trust artitectures.

---

## Screenshots

DNS Query and Response

<img width="1427" height="255" alt="image" src="https://github.com/user-attachments/assets/ac3eba89-e8ba-4291-a9de-369ea89eafad" />

DNS Resolution

<img width="422" height="95" alt="image" src="https://github.com/user-attachments/assets/3f2e7015-966d-4276-a182-785e549a6001" />

Connectivity Test

<img width="484" height="131" alt="image" src="https://github.com/user-attachments/assets/439dc26f-6570-4740-b079-9c61af293013" />


