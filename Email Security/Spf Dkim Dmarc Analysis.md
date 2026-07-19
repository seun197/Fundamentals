# SPF DKIM DMARC Analysis

## Objective

Understand how DNS and email authentication establish trust before an email is delivered.

## System Overview

Email authentication combines DNS, cryptographic signatures and policy enforcement to reduce domain spoofing.

The domain owner publishes DNS records.

The sending email server signs an outgoing email using a private key.

The recieving mail server retrieves the public key from the authorative DNS server and validates the email before deciding whether to accept it.

## Components

| Component | Purpose |
|----------|---------|
| Authoritative DNS Server | Stores the official DNS records for the domain |
| MX | Identifies the mail server that receives email |
| SPF | Lists authorised sending servers |
| DKIM | Uses public key cryptography to verify the email signature |
| DMARC | Applies policy based on SPF and DKIM alignment |
| Sending Mail Server | Sends and signs the email |
| Receiving Mail Server | Verifies authentication and decides how to handle the email |

## Communication Flow

```text
Domain Owner
      │
Publishes DNS Records
      │
      ▼
Authoritative DNS Server
      │
MX
SPF
DKIM Public Key
DMARC
      │
      ▼
Sending Mail Server
      │
Private DKIM Key
      │
Signs Email
      │
      ▼
Receiving Mail Server
      │
Checks SPF
Checks DKIM
Checks DMARC
      │
      ▼
Accept
Junk
Quarantine
Reject
```

## Lab

## powershell

Resolve-DnsName microsoft.com -Type MX

<img width="1089" height="514" alt="image" src="https://github.com/user-attachments/assets/7b6e3345-cc05-45ac-a8c0-677e69d3f6f6" />

Resolve-DnsName _dmarc.microsoft.com -Type TXT

<img width="1106" height="249" alt="image" src="https://github.com/user-attachments/assets/adf62941-9326-4c85-a0ca-89c6b64dd15c" />

nslookup -type=mx microsoft.com

<img width="977" height="342" alt="image" src="https://github.com/user-attachments/assets/1f039c3e-a33f-4317-b753-b07a318cb5d0" />
