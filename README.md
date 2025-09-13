# DVWA
In that identified the vulnerability such as SQL injection, XSS, and insecure login using DVWA

## 1. set up the environment
 Install the DVWA in the kali linux 
    sudo apt install dvwa

 Log in to dvwa 

 Set the security level

 ## 2.Execute the vulnerability exploitation
 
### a) SQL injection: 

SQL Injection (SQLi) is a code injection attack that exploits a web application's failure to properly validate and sanitize user input before it is incorporated into an SQL query

1.Access to login page

2.Intercept the Request: Enter a placeholder username (e.g., admin) and a password (e.g., password). Before you click "submit," configure Burp Suite to act as an intercepting proxy. Burp Suite will capture this HTTP request before it is sent to the web server.

3.Craft and Inject the Payload: Send the intercepted request to Burp Suite's Repeater tool. In the password field, replace the placeholder password with the SQLi payload: 
    ' OR 1=1 --
    
4.Analyze the Response

### b)Cross-Site Scripting (XSS)

The goal of this attack is to inject and execute malicious scripts. DVWA is vulnerable to both reflected and stored XSS attacks. 

1.Find a Target: Locate a page feature that reflects your input back to you, such as a search bar or a feedback form.

2.Inject the Payload: In the input field, type the simple, harmless payload: <script>alert(1)</script>.

3.Execute the Attack: Submit the request. The payload will be sent to the server, "reflected" back in the URL, and then executed by your browser. A JavaScript alert box will pop up on your screen, confirming the vulnerability. 

### c)Insecure login flows(Brute-force)

This attack exploits the lack of proper login flow controls, which allows for automated password guessing.

1.Test for Username Enumeration: A brute-force attack is more effective if you can first confirm which usernames are valid. On the DVWA login page, try logging in with a valid username like admin.

2.Launch the Brute-Force Attack:

Send to Intruder: Once you have a valid username, intercept a login request and send it to Burp Suite's Intruder tool.   

Define Payload Position: In the "Positions" tab within Intruder, highlight the password field and mark it as a "payload position".   

Load a Wordlist: In the "Payloads" tab, select a wordlist of common passwords, such as those found in your Kali Linux distribution.   

Start the Attack: Launch the attack. Burp Intruder will systematically try each password from your list. Monitor the responses. A successful login can be identified by a    

302 redirect status code or a different response length, indicating a successful login. 
  

    
 
