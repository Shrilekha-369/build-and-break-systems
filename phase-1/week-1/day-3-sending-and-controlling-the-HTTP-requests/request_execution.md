# 📄 Day 3 – Request Execution & Analysis

## 🎯 Goal
Understand how to manually send and manipulate HTTP requests using Burp Suite Repeater and observe server behavior.

---

## 🔬 Experiment 1: Base Request Execution

### Request

GET / HTTP/2
Host: www.example.com


📸 Evidence:  
![Base Request](images/base-request.png)

### Observation
- Response: **200 OK**
- Server returned expected HTML content

### Insight
- Repeater can successfully replicate browser-generated requests
- Confirms correct request structure

---

## 🔬 Experiment 2: Path Manipulation

### Request

GET /test HTTP/2
Host: www.example.com


📸 Evidence:  
![Path Manipulation](images/path-change.png)

### Observation
- Response: **404 Not Found**

### Insight
- Server routing depends on the request path
- Invalid endpoints return 404
- Confirms application-level routing behavior

---

## 🔬 Experiment 3: Host Header Manipulation

### Request

GET / HTTP/2
Host: fake.com


📸 Evidence:  
![Host Manipulation](images/host-421.png)

### Observation
- Response: **421 Misdirected Request**

### Insight
- Server strictly validates Host header
- Likely behind CDN/reverse proxy (e.g., Cloudflare)
- Prevents misrouting and host header abuse

---

## 🔬 Experiment 4: Protocol Behavior

### Action
- Attempted to change HTTP/2 → HTTP/1.1

### Observation
- Response still returned as **HTTP/2**

### Insight
- Protocol is negotiated during TLS handshake (ALPN)
- Cannot be changed from request editor alone

---

## 🔬 Experiment 5: Header Manipulation

### Actions
- Modified `User-Agent`
- Removed `Sec-Fetch-Site`
- Added custom header

### Observation
- Response remained **200 OK**

### Insight
- These headers are not critical for server processing
- Server prioritizes:
  - Method
  - Path
  - Host

---

## 🧠 Overall Understanding

### Critical Components
- Method
- Path
- Host header

### Non-Critical (in this scenario)
- User-Agent
- Sec-Fetch-* headers
- Custom headers

---

## 🔁 Repeater Workflow (Core Skill)

1. Capture request  
2. Send to Repeater  
3. Modify request  
4. Send again  
5. Analyze response  

### Why it matters
- Fast iteration
- No browser dependency
- Full control over requests

---

## 🚨 Key Takeaway

Day 3 establishes the ability to:

> Fully control and replay HTTP requests manually

This is essential for:
- Security testing
- Bug bounty workflows
- Understanding server behavior

---

## 🔚 Conclusion

This day marks the transition from observing requests to actively manipulating them. Repeater enables precise control, making it a powerful tool for deeper web security testing.
