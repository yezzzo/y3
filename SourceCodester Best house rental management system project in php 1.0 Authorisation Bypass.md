# SourceCodester Best house rental management system project in php 1.0 Authorisation Bypass

## NAME OF AFFECTED PRODUCT

- Best house rental management system project in php

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

- Authorisation Bypass

### Root Cause

- An Authorisation Bypass vulnerability was found in the "admin_class.php" file of the "Best house rental management system project in php" project. The cause of this issue is that the attacker injects malicious code from the parameter "username" and logs in to another person's account without verification. This allows the attacker to construct input values, thereby manipulating other people's accounts and performing unauthorized operations.

![image-20240616173045573](https://github.com/yezzzo/y3/assets/75334106/0ef2adad-ff43-4088-818a-3b254dfe4c15)


### Impact

- Attackers can use this Authorisation Bypass vulnerability to achieve unauthorized account access, sensitive data leakage, and data tampering, posing a serious threat to system security and user privacy.

## DESCRIPTION

- Due to insufficient user input validation for the "username" parameter, a serious Authorisation Bypass vulnerability was found in the login function of "Best house rental management system project in php", allowing an attacker to inject malicious SQL statements. As a result, an attacker can gain unauthorized access to another person's account without knowing their account password, modify or delete data, and access sensitive information. Immediate remediation is required to ensure system security and protect data integrity.


## Vulnerability details and POC

### Vulnerability type

- Authorisation Bypass

### Vulnerability location

- 'username' parameter in "admin_class.php"

### Payload

- 111' or 1=1 limit 1#

![T6 Y9 @MLOIKH6~L%L){XX0](https://github.com/yezzzo/y3/assets/75334106/033146ea-3a72-4d15-9351-3373e4a4c050)

Enter the payload in the account and enter the password at will. Click Login and we can find that we are logged in to the website and we are the admin account (because the first row in the database is admin)


![image](https://github.com/yezzzo/y3/assets/75334106/0c0dd597-f78c-4303-8c32-2c844039592c)


## Suggested repair

1. **Use prepared statements and parameter binding:**
   Preparing statements can prevent SQL injection as they separate SQL code from user input data. When using prepare statements, the value entered by the user is treated as pure data and will not be interpreted as SQL code.
2. **Input validation and filtering:**
   Strictly validate and filter user input data to ensure it conforms to the expected format.
3. **Minimize database user permissions:**
   Ensure that the account used to connect to the database has the minimum necessary permissions. Avoid using accounts with advanced permissions (such as' root 'or' admin ') for daily operations.
4. **Regular security audits:**
   Regularly conduct code and system security audits to promptly identify and fix potential security vulnerabilities.
