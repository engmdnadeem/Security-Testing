**Student Name: Mohammed Nadeem**

**Student ID: MOH22609030**

**Lab: Security testing**

**Date: Jan 25 2024**

**Requirement 1 : Setup security testing environment****

1. **Deployed an OWASP Juice Shop server with the virtual machine specifications as below**
2. Username: student
3. Password:Student1
4. IP Address: 192.168.123.55
 ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/7c00a0ee-c7f1-4382-a839-bacf6f4cff57)
 
6. Deployed a Security Testing workstation with below specifications
7. Workstation: Kali
8. Username:Kali
9. Password:Kali
10. IP Address: 192.168.123.5

 ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/6e4d5c61-8090-40b8-94d8-394bcd75d4e5)


**Requirement 2 : OWASP Juice Shop Functionality Testing**
1. What are the features and functions of the OWASP Juice Shop application?
2. Open Web Application Security Project(OWASP) is a frontend application just like a food ordering website.
3. It has many features such as: Menu,Search Bar,Account,Language.
4. Some of the key functions of the OWASP Juice shop application are project development, educational purposes.

**Requirement 3. Exploit a Cross-Site Scripting vulnerability**
**Client-side XSS:**
1. In this XSS we have to enter our payload by the client side.
2. Create the new user account before submitting the form turn on the intercept and capture the request in Burp suite.
![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/a9407466-2ea1-4fa9-8852-63386a1ad1eb)
3. Send the request to repeater and in place of email  insert the payload <iframe src="javascript:alert(`xss`)">
4. As in the email section we have the double quotes in there so in order to overcome this error just use back slash in the payload
   <iframe src=\"javascript:alert(`xss`)\">

![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/48fdbff2-059d-42be-be28-b7f9e6f979d9)

**Requirement 4. Exploit a SQL injection vulnerability.**
**User Credentials:**
1. Load the OWASP juice shop page and turn on the interceptor and search anything in the juice shop
2. The request is captured in Burp Suite
3. Now send the request to repeater and check the responses
4. As you give a value to search as q='))-- it will show all the items provided in the juice shop.
5. Now i know that the search fun ction is vulnerable.
6. I tried to get the user credentials using this vulnerability by inserting the SQL Injection.
7. i tried inserting the UNION query UNION%20SELECT%201,2,3,4,5,6,7,8,9%20FROM%20sqlite_master--
 
  ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/628c7205-e8d5-48f7-bb78-4cbf1b026c2c)

9. I got into the data of the page,in order to get entire schema of the database i would type just sql in place of 1.
   
  ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/baf2b9e1-a898-419e-af0f-7283d3ef47d7)

11. Now i need the user credentials so just replace the sql with email,2 with password and sqlite_master with Users.
12. Now i have accessed all user credentials with hashed password with that i can decode the hashed passwords and get into the accounts.

 ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/cda48183-ff14-4f87-9f1e-5b0cd3b9f1cb)

14. I have successfully completed the challenge.

 ![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/f69da014-3792-4269-8ff3-315289dc7145)

**Requirement 5. Exploit a Broken Access Control vulnerability.**

**Find Easter Egg**:
1. Log on to the ftp server as URL 192.168.123.55:3000/ftp
2. The list of files will appear in which i have eastere.gg but when tried to open it gives an error as only .md and .pdf files can be opened

![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/c942479f-8e1d-4428-bf78-84623a7e8e88)
4. In order to by pass the blocking use a NULL byte in the path as %2500 and give extension as .md
5. URL as 192.168.123.55:3000/ftp/eastere.gg%2500.md
6. Now i have found the hidden easter egg successfully. 

![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/5a8a6926-60b9-4435-a985-01970993efb0)


**Requirement 6. Exploit an Authentication Bypass vulnerability.**

**CHANGE BENDER'S PASSWORD:**
1. I tried to login with bender account with the SQL Injection
2. Email: **bender@juice-sh.op'--** (' means close bracket in SQL Injection and -- means comment out ) Password:**Anything some** 
3. After successfully logging in go on to the change password page and turn on the intercept.
4. Send the login request to the burp suite it appears as below

![burp suite 1](https://github.com/engmdnadeem/Security-Testing/assets/152322481/0ade1403-3a58-4bf6-950e-3fcd384bdc4d)

6. Now send the request to repeater and remove the current password
7. I got a lot of failed attempts in this as everytime i made a mistake of not turning off the interceptor. 
8. Do not forget to turn off the interceptor and click on send it will change the password

![change benders password ](https://github.com/engmdnadeem/Security-Testing/assets/152322481/786b6994-0f9c-4f79-b96f-89711d517898)


**Requirement 7. Exploit an Improper Input Validation vulnerability.****

**Poison Null Byte:**

1. The word means that in order to bypass the error path which could be a improper file validation,some NULL byte is used.
2. Go on to the FTP server and open any of the files.
3. For example open the easter egg file but due to improper file extension it throws an error as only .pdf and .md files are allowed.
4. This is where the NULL byte acts so in order to Bypass the error just add %2500.md to the URL which gives an access to the document.
5. Now i can solved this challenge.

 ![easter egg](https://github.com/engmdnadeem/Security-Testing/assets/152322481/8b7af924-569d-49a8-9f9b-c52917c12532)


**Requirement 8. Exploit a Sensitive Data Exposure vulnerability**

**Access a developer's forgotten backup file.**:
1. Go on to the ftp server as 192.168.123.55:3000/ftp
2. You can see the list of files in those the developer file is package.json
3. Click on to the file in order to open it but it throws an 403 error as only .pdf and .md files are allowed

![image](https://github.com/engmdnadeem/Security-Testing/assets/152322481/b1603f81-2f18-427f-b439-d58f3e64e9ba)

5. In order to access the file we use a NULL byte in the path of URL as %2500 to encode.
6. Just type the URL as 192.168.123.55:3000/ftp/package.json%2500.md
7. Now the file is successfully downloaded and opened.

 ![forgotten developer file](https://github.com/engmdnadeem/Security-Testing/assets/152322481/3bbe8beb-7758-4b97-a855-2f1fdc472f8c)


