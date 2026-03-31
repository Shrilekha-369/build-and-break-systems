# 📅 Day 2 – Understanding and Manipulating HTTP Requests

## 🎯 Objective

Learn how HTTP requests work and how modifying them affects server responses using Burp Suite.

---

## 🛠 Tools Used

* Burp Suite Community Edition
* Google Chrome

---

## 🔍 What I Did

### 1️⃣ Captured a Normal Request

* Intercepted a request to `https://www.google.com`
* Observed standard headers and structure
* Response: **200 OK**

![HTTP History](images/01-http-history-original-request.png)

---

### 2️⃣ Added Custom Header

* Added:

  ```
  X-Day-2-Test: working
  ```
* Sent request via Repeater

🔎 Result:

* Received **400 Bad Request**

![400 Bad Request](images/02-custom-header-400-bad-request.png)

---

### 3️⃣ Resent Request (Fixed)

* Sent request again after correcting/modifying it

🔎 Result:

* Response returned to **200 OK**

![200 OK](images/03-repeater-success-200-ok.png)

---

### 4️⃣ Modified User-Agent

* Changed:

  ```
  User-Agent: hacker-test
  ```

🔎 Result:

* Server still returned **200 OK**

![User-Agent Modification](images/04-user-agent-modification.png)

---

### 5️⃣ Removed Header

* Removed:

  ```
  Sec-Fetch-Site
  ```

🔎 Result:

* Request still worked (**200 OK**)

![Header Removal](images/05-header-removal-sec-fetch-site.png)

---

### 6️⃣ Changed Host Header

* Modified:

  ```
  Host: evil.com
  ```

🔎 Result:

* Received **404 Not Found**

![Host Header](images/06-host-header-manipulation.png)

---

## 🧠 Key Learnings

* HTTP requests are sensitive to certain headers
* Some headers are optional, others are critical
* Improper modifications can break requests
* The **Host header** is crucial for routing
* Burp Suite Repeater allows precise manual testing

---

## 🚀 Summary

This day focused on understanding how web servers react to modified requests.
These skills are essential for:

* Web security testing
* Bug bounty hunting
* Understanding real-world vulnerabilities

---
