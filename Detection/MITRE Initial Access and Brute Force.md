# Repeated Failed Authentication Investigation

## Query

```kusto
IdentityLogonEvents
| where ActionType != "LogonSuccess"
| summarize FailedAttempts = count() by AccountUpn, IPAddress
| order by FailedAttempts desc
```

## Objective

Identify accounts generating high volumes of failed authenticaton attemps and determine whether the activity represents a security threat or a legitimate authentication issue.

## What Looked Suspicious

This query identiified a user account that generated 15 failed authentication attempts from the same IP address.

A high number of failed sign ins is insusual due to legitimate users only generatre a small number of authentication failures can indicate password spraying, brute force activity, credential misuse, or a user repeatedly entering incorrect credentials.

## What Evidence Existed?

During Investigatio, I identified:

1. 15 failed authentication attempts within a 24 hour period
2. A successful authentication from the same IP address
3. Conditional Access policies were successfully enforced
4. The sign in location matched the users expeced location.
5. No unusual geographic activity observed
6. No immediate indicators of risky sign ins where identified


## What would the attacker do next?

If valid credentials had been obtained, the likely steps would inlude:

1. Accessing email and cloud resources
2. Accessing users onedrive
3. Discovering privilleged accounts
4. Searching for sensetive information
5. Attempting privillege escalation
6. Establishing persisitence within the tenant


## Assessment

Although the volume of failed authentication attempts initially appeared suspicious, the successful sign in originated from the same IP address and expected location, and Conditional Access controls were successfully applied.

Based on the available evidence, the activity appeared more consistent with a legitimate authentication issue than a confirmed account compromise.


## Key Takeaway

Authentication failures generate evidence, but they do not automatically indicate compromise. Context such as authentication success, location, Conditional Access outcomes, user behaviour, and post-authentication activity must be reviewed before reaching a conclusion.
