# Day 2 — Understanding HTTP Requests

## Objective
Break down HTTP requests and understand how browsers communicate with servers.

---

## What I Did

- Intercepted live traffic using Burp Suite
- Analyzed raw HTTP requests
- Observed server responses
- Identified key headers and their roles
- Experimented with modifying requests

---

## Key Learning

An HTTP request is made up of:

- Method (GET / POST)
- Path (/)
- Protocol (HTTP/1.1 or HTTP/2)
- Headers (Host, User-Agent, etc.)
- Body (optional)

---

## Evidence

### HTTP History View
![HTTP History](images/img1-http-history.png)

---

### Raw Request Captured
![Original Request](images/img2-original-request.png)

---

### Server Rejecting Request (400 Bad Request)
![400 Error](images/img3-400-bad-request.png)

---

### Successful Request via Repeater
![200 OK](images/img4-repeater-success.png)

---

### Header Modification (User-Agent)
![Header Change](images/img5-header-modification.png)

---

### Host Header Manipulation
![Host Header](images/img6-host-header-change.png)

---

## Key Insight

> The server does not trust the browser — it trusts the HTTP request.

If you control the request → you control how the server behaves.

---

## Skills Built

- Reading raw HTTP requests
- Understanding headers and their purpose
- Observing server responses
- Identifying request structure
- Basic request manipulation

---

## Next Step

Move from understanding requests → actively sending and manipulating them (Day 3).
