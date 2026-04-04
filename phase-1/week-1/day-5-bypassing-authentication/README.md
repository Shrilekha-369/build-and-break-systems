# 🔐 Day 5 — 2FA Simple Bypass

## 📌 Lab Overview
This lab demonstrates a critical flaw in two-factor authentication (2FA) implementation. Although the application generates and sends a verification code, it fails to enforce proper authorization when accessing protected resources.

---

## 🎯 Objective
- Bypass the 2FA mechanism
- Gain unauthorized access to another user's account (Carlos)

---

## 🧠 Key Concept
> 2FA must be enforced at the authorization level, not just during login.

---

## 🛠️ Attack Workflow

### 1. Login with Valid Credentials

wiener : peter


- Login is successful
- Application proceeds to 2FA step

---

### 2. Observe 2FA Code Delivery
The application sends a verification code via email.

![2FA Email](./images/2fa_code_email_interception.png)

---

### 3. Access Authenticated Session
Despite not completing 2FA, the session is already usable.

![Authenticated Session](./images/authenticated_session_wiener.png)

---

### 4. Inspect Request in Burp Suite
The request to `/my-account` confirms session-based access.

![Burp Request](./images/authenticated_wiener_burpsuite.png)

---

### 5. Exploit via Parameter Manipulation
Modify:

/my-account?id=wiener → /my-account?id=carlos


![Forced Browsing](./images/forced_browsing_account_switch.png)

---

## 🚨 Vulnerability
- Broken access control (IDOR)
- 2FA not enforced on protected endpoints
- Session not tied to verification state

---

## ✅ Impact
- Unauthorized account access
- Complete bypass of 2FA protection
- Exposure of sensitive user data

---

## 🧩 Key Takeaway
> Security controls like 2FA are ineffective if backend authorization checks are missing.
