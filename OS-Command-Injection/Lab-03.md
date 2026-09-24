# 💉 OS-Command-Injection - Lab 03
 Blind OS command injection with output redirection

 ## 🎯 Objective
 To solve the lab, execute the whoami command and retrieve the output.

 ## 🔍 Vulnerability
 This lab contains a blind OS command injection vulnerability in the feedback function.

 ## 📝 Methodology
 The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. However, you can use output redirection to capture the output from the command. There is a writable folder at:

/var/www/images/
The application serves the images for the product catalog from this location. You can redirect the output from the injected command to a file in this folder, and then use the image loading URL to retrieve the contents of the file.

To solve this lab, intercept the request for feedback submission in Burp Suite and send it to the Repeater. Once in the Repeater, modify the email section and insert the command injection. In this case, the payload is |whoami>/var/www/images/output.txt|, which will execute the command and save the output to a file in the writable directory.
After making the changes and creating the file named output.txt, the next step is to open it.
To do this, intercept the request for opening the product image in Burp Suite, then modify the file name in the request to output.txt
