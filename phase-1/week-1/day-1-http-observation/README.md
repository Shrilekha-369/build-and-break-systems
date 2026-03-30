# Day 1 — Seeing the Web: Raw HTTP vs Encrypted Traffic

## Objective
Understand what actually happens when a browser makes a request — at the packet level.

---

## Key Observation

Most modern traffic is **NOT HTTP**.

Instead, it follows this flow:

1. TCP 3-way handshake  
2. TLS handshake (Client Hello, Server Hello)  
3. Encrypted application data (TLS)  

---

## What I Expected
- Plain HTTP requests (GET / POST)  
- Visible headers and parameters  

---

## What I Actually Saw
- TLSv1.2 / TLSv1.3 traffic  
- Encrypted payloads (Application Data)  
- No readable HTTP content  

---

## Key Insight

> HTTPS = HTTP inside TLS → You cannot see application data without interception.

---

## Breakthrough Moment

After switching to HTTP (port 80), I observed:

- GET request  
- HTTP response (200 OK)  
- Raw headers and data  

---

## 📸 Evidence

### 1. TCP Connection Behavior

![TCP Retransmissions](./images/tcp-retransmissions.png)

**Observations:**
- Multiple SYN packets sent to port 80  
- Repeated TCP retransmissions  
- Delayed SYN-ACK responses  

**Analysis:**
- Indicates packet loss or delayed responses during connection setup  
- TCP retries connections when acknowledgments are not received  
- Shows reliability mechanisms in action  

---

### 2. HTTP Request Visibility

![HTTP GET Request](./images/http-get.png)

**Observations:**
- HTTP GET request to `neverssl.com`  
- Full headers visible (Host, User-Agent, Accept, etc.)  
- Server response: `HTTP/1.1 200 OK`  

**Analysis:**
- Traffic is transmitted in **cleartext (unencrypted)**  
- Entire request/response is visible in packet capture  
- Demonstrates why HTTP is insecure  

---

## 🔗 Connection Flow Insight

Multiple TCP retransmissions occurred before a successful handshake.  
Once established, the HTTP request was transmitted and a valid response was received.

---

## Skills Built Today

- Packet-level observation mindset  
- Understanding TCP handshake behavior  
- Recognizing TLS encryption boundaries  
- Differentiating HTTP vs HTTPS traffic  

---

## Why This Matters (Offensive Security)

If you cannot see the request:  
→ You cannot manipulate it  
→ You cannot exploit it  

So attackers:
- Intercept traffic (e.g., proxy tools)
- Attempt protocol downgrades (when possible)
- Or target application logic instead  

---

## Next Step

Move from observing traffic → manipulating requests manually.
