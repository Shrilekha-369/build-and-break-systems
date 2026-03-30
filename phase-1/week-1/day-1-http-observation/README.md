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

## Skills Built Today

- Packet-level observation mindset
- Understanding TCP handshake
- Recognizing TLS encryption boundary
- Differentiating HTTP vs HTTPS behavior

---

## Why This Matters (Offensive Security)

If you cannot see the request:
→ You cannot manipulate it  
→ You cannot exploit it  

So attackers:
- Intercept traffic (Burp Suite)
- Downgrade to HTTP (when possible)
- Or exploit client/server logic instead

---

## Next Step

Move from observing traffic → manipulating requests manually.
