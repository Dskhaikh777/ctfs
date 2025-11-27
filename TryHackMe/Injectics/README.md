# Injectics

## IP: 10.65.185.75

First, I grabbed the machine's IP address and ran an Nmap scan to see which ports were open. It was a great way to check what was available!

## **Nmap Result:**

```python
Nmap scan report for 10.65.185.75
Host is up (0.26s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.11 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41
Service Info: Host: ip-10-65-185-75.ec2.internal; OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

I also gave Gobuster a try to uncover the hidden directories.

![gobuster.png](gobuster.png)

However, I do not have access to this directory. From the /Vendor directory, I confirmed that the application is using the Twig template engine and that the version is disclosed.

I opened my browser, pasted the IP in the search bar, and the webpage loaded up. Then, I checked out the page source, and I found a nice green commented line!

![page_source.png](page_source.png)

I received the mail.log file from the comment, where all the emails are stored. I thought it might contain some interesting information!

## **Mail.log file content:**

To add an extra layer of safety, I have configured the `service to automatically insert default credentials into the users table if it is ever deleted or becomes corrupted.`  ←- This line indicates the application may be vulnerable to SQLi.

This ensures that we always have a way to access the system and perform necessary maintenance. I have scheduled the service to run every minute.

Here are the default credentials that will be added:

| Email | Password |
| --- | --- |
| superadmin@injectics.thm | superSecurePasswd101 |
| dev@injectics.thm | devPasswd123 |

After checking out the mail.log file, I figured out how to get started with the initial access. I went to the login page and used Burp to intercept the request. I tested it with a single quote and confirmed it was vulnerable to SQL injection. Then, I sent the request to the intruder and tried out various payloads to bypass the login. And guess what? I managed to gain initial access as a Dev user!

![sql_intruder.png](sql_intruder.png)

![login_dev.png](login_dev.png)

As a dev user, I have the ability to modify scores. I intercepted the request using Burp Suite and attempted to delete the users table through SQL injection. The mail.log file indicates that if the users table gets corrupted or deleted, we can use the default credentials found in the log to log in as an admin.

![users_table.png](users_table.png)

![users_del.png](users_del.png)

After successfully deleting the users table, I can now log in as an admin using the default credentials. After logging in as an admin, I obtained the first flag.

![admin_flag.png](admin_flag.png)

On the admin home page, there is a section called "Profile." When I navigate to that page, I see several fields where I can input data. I discovered that any name I enter in the name field gets reflected on the admin home page. Since the application uses Twig, I tested for Server-Side Template Injection (SSTI) by using a simple payload like `{{7*7}}`, which resulted in 49. This indicates that the application is vulnerable to SSTI, allowing me to execute commands through Remote Code Execution (RCE). After traversing the directories, I found the second flag. Additionally, I can use a reverse shell to gain shell access.

![final_ssti.png](final_ssti.png)

![final_flag.png](final_flag.png)

![completion.png](completion.png)

In the same section of the admin profile, I checked the name input field for other vulnerabilities and found that it is also susceptible to HTML injection and XSS.

![htmli.png](htmli.png)

![html_out.png](html_out.png)

![xss.png](xss.png)

![strored_xss_out.png](strored_xss_out.png)