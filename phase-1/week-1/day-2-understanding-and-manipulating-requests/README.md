# Day 2 — Understanding & Manipulating HTTP Requests

## Objective
Move from passive observation → active control of HTTP requests.

---

## Key Idea

A request is not fixed.

It is a **set of controllable inputs** that directly influence server behavior.

---

## What I Did

- Intercepted requests using Burp Suite
- Sent requests to Repeater
- Modified headers manually
- Observed how the server responded to each change

---

## Key Experiments

### 1. Baseline Request
- Sent original request without modification
- Received `200 OK`

This established a **control response**

---

### 2. Modified User-Agent

Changed:

User-Agent: Mozilla/5.0 ...

To:

User-Agent: hacker-test

**Result:**
- Response still `200 OK`

**Insight:**
- User-Agent is not strictly validated
- Can often be spoofed

---

### 3. Removed Headers

Removed a non-critical header like:
- `Sec-Fetch-Site`

**Result:**
- Server still responded normally

**Insight:**
- Not all headers are required
- Some are optional metadata

---

### 4. Modified Host Header

Changed:

Host: www.google.com

To:

Host: evil.com

**Result:**
- Response changed to `404 Not Found`

**Insight:**
- Server routing depends on Host header
- Host header influences application behavior

---

## Key Insight

> Small changes in a request can lead to completely different server responses.

---

## Skills Built Today

- Using Repeater for controlled testing
- Understanding request structure
- Identifying critical vs non-critical headers
- Observing server-side validation behavior

---

## Why This Matters (Offensive Security)

If you can control the request:
→ You can influence the server  

If you can influence the server:
→ You can find vulnerabilities  

---

## Next Step

Move from modifying requests → crafting and replaying them deliberately.
