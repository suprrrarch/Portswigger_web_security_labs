
# 💉 OS-Command-Injection - Lab 01

OS Command Injection , Simple case

## 🎯 Objective

To solve the lab, execute the whoami command to determine the name of the current user.

## 🔍 Vulnerability

This lab contains an OS command injection vulnerability in the product stock checker.

## 📝 Methodology
This lab is quite simple. In this task, besides using the usual command to fetch data, we will also add our own command to get the information we want.First, click on the Access Lab button. A new tab will open, where the lab environment will be available.When we start the lab, a simple website appears on the screen.

First, open the lab and select any product. Then, when you click on the “Check stock” button, intercept the request using Burp Suite. After that, send the captured request to the Repeater for testing.The request we captured had two parameters: productId and storeId.
We discovered that the storeId parameter was vulnerable. To test this, we added the payload ;whoami to the value of storeId. This command was executed successfully and returned the current system user, confirming the vulnerability.
