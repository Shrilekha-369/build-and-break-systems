📅 Day 4 – Replay the Real Request

🎯 Objective  
Learn how to capture, replay, and exploit real HTTP requests to break authentication logic.

🛠 Tools Used  
- Burp Suite Community Edition (Proxy, Repeater, Intruder)
- Google Chrome

---

🔍 What I Did  

1️⃣ Captured Login Request  
- Intercepted POST /login request  
- Observed parameters:
  username, password  
- Identified cookies and headers used in authentication  

---

2️⃣ Sent Request to Intruder  
- Replayed captured request  
- Prepared it for automated testing  

---

3️⃣ Username Enumeration  
- Used Intruder with username wordlist  
- Kept password constant  

🔎 Observation:
- "Invalid username" → user does not exist  
- "Incorrect password" → VALID username  

✔ Identified valid username: `acceso`

---

4️⃣ Password Brute Force  
- Fixed username = acceso  
- Used password wordlist in Intruder  

🔎 Observation:
- 200 OK → login failed  
- 302 Found → login success  

✔ Identified password via response behavior  

---

5️⃣ Successful Authentication  
- Server returned:
  - 302 Redirect to /my-account  
  - Set-Cookie: session=...  

- Accessed user dashboard successfully  

---

🧠 Key Learnings  

- Authentication logic can leak information via responses  
- Status codes (200 vs 302) are critical indicators  
- Intruder enables automated attack execution  
- Session cookies represent authenticated identity  
- Real-world attacks rely on subtle response differences  

---

🚀 Summary  

This day focused on replaying and exploiting real HTTP requests.  
By combining enumeration and brute force techniques, I was able to:

✔ Identify a valid user  
✔ Discover the correct password  
✔ Gain authenticated access  

This demonstrates how weak authentication mechanisms can be exploited in real-world applications.
