# Packet Capture Analysis — Day 1

## 1. TCP Handshake

Example:

[SYN] → Client initiates connection  
[SYN, ACK] → Server acknowledges  
[ACK] → Connection established  

This confirms:
- Reliable connection setup
- Sequence number synchronization

---

## 2. TLS Handshake (HTTPS Traffic)

Observed:

- Client Hello (SNI: login.microsoftonline.com)
- Server Hello
- Certificate exchange
- Encrypted Application Data

### Key Insight

After handshake:
→ All payloads are encrypted

Example:
TLSv1.3 Application Data (Unreadable)

---

## 3. HTTP Traffic (Port 80)

Observed:

GET / HTTP/1.1

Response:
HTTP/1.1 200 OK

### Key Difference

| Feature        | HTTP (80) | HTTPS (443) |
|----------------|----------|------------|
| Visibility     | Full     | Encrypted  |
| Headers        | Visible  | Hidden     |
| Payload        | Visible  | Hidden     |

---

## 4. Retransmissions

Multiple:

[TCP Retransmission] SYN

### Interpretation:
- Packet loss OR
- Delayed ACK OR
- Network instability

---

## 5. Connection Lifecycle

- SYN → SYN-ACK → ACK
- Data transfer
- FIN / ACK (graceful close)

---

## Final Mental Model

Browser Request Flow:

Browser → TCP → TLS → HTTP → Server → Response → Render

---

## Security Insight

Encryption protects data in transit,
but NOT:
- Endpoints
- Application logic
- Misconfigurations
