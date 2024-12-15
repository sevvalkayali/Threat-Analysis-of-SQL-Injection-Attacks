# SQL Injection Penetration Testing Report

## Project Overview
This report demonstrates a comprehensive **SQL Injection** penetration testing project. The objective of the experiment was to test the effectiveness of SQL Injection protections at different security levels in **DVWA (Damn Vulnerable Web Application)**, using a combination of **Kali Linux**, **Burp Suite**, and **FoxyProxy**. 

The experiment aimed to:
- Identify SQL Injection vulnerabilities.
- Test the effectiveness of security mechanisms at Low, Medium, and High levels in DVWA.
- Capture network traffic using Burp Suite and FoxyProxy.
- Analyze server responses to determine if protections were successfully bypassed or blocked.

## Tools & Environment

1. **VirtualBox**:  
   The experiment was conducted within a **VirtualBox** environment, running **Kali Linux** as the attack machine.

2. **Kali Linux**:  
   Kali Linux, a penetration testing distribution, was used as the testing environment. It provided all necessary tools to conduct the SQL Injection tests.

3. **DVWA (Damn Vulnerable Web Application)**:  
   DVWA was set up as a vulnerable web application to simulate a real-world web server susceptible to SQL Injection. The application was hosted on the Kali Linux virtual machine.

4. **Burp Suite**:  
   **Burp Suite** was used as the main tool for intercepting and manipulating HTTP requests and responses. It allowed the tester to inject malicious SQL payloads and observe the server's behavior.

5. **FoxyProxy**:  
   **FoxyProxy** was installed as a browser extension to route all web traffic through **Burp Suite**, enabling easy interception of HTTP requests from the browser.

## Experiment Setup

1. **Virtual Environment**:  
   The penetration testing environment was configured with Kali Linux running inside **VirtualBox**, with DVWA hosted locally on the Kali machine.  
   - Kali Linux Version: [insert version].  
   - DVWA was configured to run with different security levels (Low, Medium, High).

2. **Burp Suite Configuration**:  
   Burp Suite was set up to intercept traffic from the browser. Using **FoxyProxy**, the browser's HTTP requests were routed through Burp Suite, allowing the attacker to inspect and modify requests.

3. **Testing Methodology**:  
   The main goal was to test SQL Injection payloads on the DVWA SQL Injection page. The following SQL Injection payloads were used:
   - Basic payload: `1' OR '1'='1 --`
   - Union-based payload: `1' UNION SELECT user,password FROM users --`

4. **Security Levels Tested**:  
   - **Low Security**: No protection mechanism is applied. SQL Injection can be executed successfully.
   - **Medium Security**: Basic input validation is applied. SQL Injection might still succeed if crafted correctly.
   - **High Security**: Advanced protections are enabled (e.g., escaping characters, parameterized queries), and SQL Injection should be blocked.

## Key Findings

- **Low Security**:  
   SQL Injection succeeded, allowing the attacker to retrieve sensitive information such as usernames and passwords from the **users** table.
  
- **Medium Security**:  
   Some filtering was implemented, but crafted payloads could still bypass protections. The response sometimes included error messages revealing database structure.

- **High Security**:  
   SQL Injection attempts were blocked, and no sensitive data was exposed. Protection mechanisms, such as input sanitization and query parameterization, effectively blocked the attack.


## Conclusion
This experiment demonstrated how SQL Injection vulnerabilities can be exploited at different security levels of DVWA. It also highlighted the effectiveness of web application security mechanisms in preventing SQL Injection attacks.

## Resources
- [DVWA Official Website](https://github.com/ethicalhack3r/DVWA)
- [Burp Suite Official Website](https://portswigger.net/burp)
- [FoxyProxy Official Website](https://getfoxyproxy.org/)
