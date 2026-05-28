# Identity Security Investigation

## Objective

Understand how Microsoft Entra decides whether a login should be trusted or blocked.

---

# What Happened?

A user attempted to access clients Microsoft platform from a country that has been blocked using their mobile.

Microsoft Entra analysed the sign in before allowing access

---

# What Microsoft Checked

Microsoft evaluated:

1. Location
2. Device
3. Browser
4. Risk detections
5. Conditional Access policies

---

What Made the Login Risky?

The login triggered:

1. Atypical travel
2. Unfamiliar sign in properties
3. Unmanaged device
4. Non Compliant device

Hence the sign in looked unusual comparted to the user's normal behaviour.

---

# Why was Access Blocked?

The sign-in matched a Conditional Access poliy configured to block access from the selected country which the user IP locationb dected.

The policy evaluated the sign in and denied access before authtication completed.

---

Security Lesson

Modern security does not automatically trust users after a password is entered.

The system continously evaluates:

- Location
- Device trust
- Behaviour
- Risk
- Security policies

before deciding whether access should be allowed.

---

# Important

Authentication proves who the user claims to be

Conditional Access (Authortisation) decides whether the user shhould actually receives access.

# Summary

A risky Microsoft Teams sign in from a blocked location using an unmanaged devicewas detected by Microsoft Entra and blocked by Conditonal Access before access was granted. 














