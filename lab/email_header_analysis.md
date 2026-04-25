# 📧 Email Header Analysis Report (Phishing Investigation)

## 🧠 Overview
This report documents the analysis of a suspicious email using header inspection techniques. The goal is to determine whether the email is legitimate or a phishing attempt by examining SMTP servers, IP addresses, and header inconsistencies.

---

## 🎯 Objectives
- Verify if the email was sent from a legitimate SMTP server  
- Compare **From** and **Reply-To / Return-Path** fields  
- Identify indicators of phishing  

---

## 🛠️ Tools Used
- Email Header Analyzer (LetsDefend Lab)
- MXToolbox (DNS lookup)
- Manual header inspection

---

## 📂 Lab Setup
- File Used: `Header-Challenge.zip`  
- Password: `infected`  
- Environment: LetsDefend Lab Machine  

---

# 🔍 Analysis

## 1️⃣ Checking Sender vs Reply-To Address

### 📌 Question:
Are the sender’s address and the address in the “Reply-To” area different?

### ✅ Answer:
**Y (Yes)**

### 🧾 Explanation:
- The **From** address represents the sender displayed to the recipient  
- The **Reply-To** address determines where replies are sent  
- In phishing attacks, attackers often manipulate the Reply-To field  

👉 In this case:
- The **From** address and **Reply-To** address are **different**
- This indicates a potential phishing attempt

 ![Q1](../screenshots/eq1.png)

---

## 2️⃣ Reply Destination Address

### 📌 Question:
If I reply to this email, which address will it be sent to?

### ✅ Answer:
**mrs.dara@daum.net**

### 🧾 Explanation:
- The Reply-To field overrides the sender’s email when replying  
- This is commonly used in phishing to redirect communication  
- The address is suspicious and unrelated to the claimed sender  

🚨 This is a **strong phishing indicator**

 ![Q2](screenshots/eq2.png)


## 3️⃣ Source IP Address Analysis

### 📌 Question:
What IP address was the email sent from?

### ✅ Answer:
**222.227.81.181**

### 🧾 Explanation:
- The **Received** header reveals the originating IP address  
- This IP can be verified against legitimate mail servers  
- If it does not match the domain's SMTP servers, it indicates spoofing  

🚨 In this case:
- The IP address is suspicious and likely not from a trusted mail server  

 ![Q3](screenshots/eq3.png)



---

# ⚠️ Key Findings

- ❌ Sender and Reply-To addresses do not match  
- ❌ Reply-To redirects to an unrelated external email  
- ❌ Suspicious originating IP address  
- ❌ Likely spoofed email  

---

# 🧩 Conclusion

> This email is **highly likely a phishing attempt**

The mismatch between sender and reply-to address, along with a suspicious originating IP, strongly indicates spoofing and malicious intent.

---

# 🧠 What I Learned

- How to analyze email headers  
- Importance of **Received**, **From**, and **Reply-To** fields  
- How attackers manipulate email metadata  
- How to validate SMTP servers using MX lookup tools  

---

# 🚀 Recommendations

- Do not reply to suspicious emails  
- Always verify sender domains  
- Check email headers before trusting emails  
- Use threat intelligence tools to validate IPs  

---
