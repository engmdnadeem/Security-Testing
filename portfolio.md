**Student Name: Mohammed Nadeem
Student ID: MOH22609030
Lab: Security testing
Date: Jan 25 2024**

**Requirement 1 : Setup security testing environment**
1. Deployed an OWASP Juice Shop server with the virtual machine specifications as below 
Username: student
Password:Student1
IP Address: 192.168.123.55
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/7c00a0ee-c7f1-4382-a839-bacf6f4cff57)

2. Deployed a Security Testing workstation with below specifications 
Workstation: Kali
Username:Kali
Password:Kali
IP Address: 192.168.123.5
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/6e4d5c61-8090-40b8-94d8-394bcd75d4e5)


**Requirement 2 : OWASP Juice Shop Functionality Testing**
1. What are the features and functions of the OWASP Juice Shop application?
Open Web Application Security Project(OWASP) is a frontend application just like a food ordering website.
It has many features such as:
1. Menu
2.Search Bar
3.Account
4.Language
Some of the key functions of the OWASP Juice shop application are project development, educational purposes.

**Requirement 5. Exploit a Broken Access Control vulnerability.**

**Find Easter Egg**:
1.Log on to the ftp server as URL 192.168.123.55:3000/ftp
2.The list of files will appear in which i have eastere.gg but hwen tried to open it gives an error as only .md and .pdf files can be opened
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/c942479f-8e1d-4428-bf78-84623a7e8e88)
3.In order to by pass the blocking use a NULL byte in the path as %2500 and give extension as .md
4.URL as 192.168.123.55:3000/ftp/eastere.gg%2500.md
5.Now i have found the hidden easter egg successfully. 
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/5a8a6926-60b9-4435-a985-01970993efb0)


**Requirement 6. Exploit an Authentication Bypass vulnerability.**

**CHANGE BENDER'S PASSWORD:**
1.I tried to login with bender account with the SQL Injection
Email: **bender@juice-sh.op'--** (' means close bracket in SQL Injection and -- means comment out )
Password:**Anything some** 
2.After successfully logging in go on to the change password page and turn on the intercept.
3.Send the login request to the burp suite it appears as below
![burp suite 1](https://github.com/engmdnadeem/Security-Testing/assets/152322481/0ade1403-3a58-4bf6-950e-3fcd384bdc4d)
4. Now send the request to repeater and remove the current password
5.I got a lot of failed attempts in this as everytime i made a mistake of not turning off the interceptor. 
5. Do not forget to turn off the interceptor and click on send it will change the password
![change benders password ](https://github.com/engmdnadeem/Security-Testing/assets/152322481/786b6994-0f9c-4f79-b96f-89711d517898)

**Requirement 8. Exploit a Sensitive Data Exposure vulnerability**

**Access a developer's forgotten backup file.**:
1. Go on to the ftp server as 192.168.123.55:3000/ftp
2. You can see the list of files in those the developer file is package.json
3. Click on to the file in order to open it but it throws an 403 error as only .pdf and .md files are allowed
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/b1603f81-2f18-427f-b439-d58f3e64e9ba)
4. In order to access the file we use a NULL byte in the path of URL as %2500 to encode.
5. Just type the URL as 192.168.123.55:3000/ftp/package.json%2500.md
6. Now the file is successfully downloaded and opened.
7. ![forgotten developer file](https://github.com/engmdnadeem/Security-Testing/assets/152322481/3bbe8beb-7758-4b97-a855-2f1fdc472f8c)


