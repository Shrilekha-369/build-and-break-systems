# 📅 Day 4 — Replay the Real Request

---

## 🎯 Objective
Replay and manipulate real authentication requests to identify weaknesses in login logic and exploit them.

---

## 🛠 Tools Used
- Burp Suite (Proxy, Repeater, Intruder)
- Web Security Academy Lab

---

## 🧪 Lab
**Username Enumeration via Different Responses**

---

## 🔍 Execution Flow

### 1. Capture Real Request
Captured a valid login request using Burp Proxy.

📸 captured_login_request.png

---

### 2. Setup Username Enumeration
Configured Intruder (Sniper attack) on the `username` parameter.

📸 intruder_username_setup.png

---

### 3. Analyze Responses
Sent multiple usernames and compared responses.

📸 username_enumeration_results.png

---

### 4. Identify Valid Username
Observed a response change:
- `Invalid username` → `Incorrect password`

✔ Valid username discovered:

acceso


📸 valid_username_identified.png

---

### 5. Setup Password Attack
Performed second Intruder attack on `password` using the valid username.

📸 intruder_password_setup.png

---

### 6. Detect Successful Login
Observed key indicator:
- `HTTP 302 Found`
- Redirect to `/my-account`

📸 successful_login_302.png

---

### 7. Confirm Account Access
Successfully accessed authenticated user dashboard.

📸 lab_solved_account_access.png

---

## 🧠 Key Learnings

- Response differences can expose valid usernames  
- Authentication logic often leaks information  
- Intruder enables efficient brute-force workflows  
- HTTP status codes (e.g., 302) are critical success indicators  

---

## 🚀 Summary

This exercise demonstrates a complete attack chain:


Request Capture → Enumeration → Credential Attack → Account Access


A common real-world vulnerability pattern in web applications.

---

## 📌 Status
✅ Lab Solved
