# Phishing Header Review

## Objective

Analyse an email header to determine how the sender was authenticated and whether the email should be trusted.

## Email Summary

| Field | Value |
|--------|-------|
| From | slumbertranq@dazzlingarena.com |
| Return Path | slumbertranq@dazzlingarena.com |
| Sending Domain | dazzlingarena.com |
| Sender IP | 5.225.156.10 |
| Subject | It's time to get a pillowcase... |

---

## Authentication Results

| Check | Result |
|--------|--------|
| SPF | Pass |
| DKIM | Pass |
| DMARC | Pass |

### Evidence

Authentication-Results header

<img width="589" height="371" alt="image" src="https://github.com/user-attachments/assets/adda45b2-e4f4-44a0-acd8-e9cf349f2aae" />

---

## Header Analysis

| Field | Observation |
|--------|-------------|
| Sender IP | 5.225.156.10 |
| Return Path | Matches From domain |
| Authentication Results | SPF, DKIM and DMARC all passed |

### Evidence

Email header

<img width="781" height="279" alt="image" src="https://github.com/user-attachments/assets/50a79999-b867-4cf8-928b-cb67a184b3cb" />


---

## Assessment

The sending server was authorised by SPF.

The DKIM signature was successfully verified.

DMARC aligned successfully.

The sender was authenticated.

Authentication alone does not prove an email is safe because a compromised legitimate mailbox can still pass SPF, DKIM and DMARC.

---

## Lessons Learned

SPF authorises sending infrastructure.

DKIM verifies message integrity using public key cryptography.

DMARC enforces authentication policy.

Authentication should always be evaluated alongside the message content, links, attachments and user context.
