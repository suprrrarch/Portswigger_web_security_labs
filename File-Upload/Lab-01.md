## 📤 File-Upload vulnerability lab-01
Remote Code Execution via web shell upload


## 🎯 Objective
To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file /home/carlos/secret. 
Submit this secret using the button provided in the lab banner.

## 🔍 Vulnerability
This lab contains a vulnerable image upload function. 
It doesn’t perform any validation on the files users upload before storing them on the server’s filesystem.

## 📝 Methodology
First, click on the Access Lab button.
A new tab will open, where the lab environment will be available.
When we start the lab, a simple website appears on the screen.

We go to Proxy > HTTP History and open the filter settings. 
In the settings, we choose “Images” and then click the “Apply ” button. T
his helps us to hide the traffic we don’t need and only show image-related requests. 
These image requests are important for our analysis, so we focus on them.
Next, we logged into the website using the “wiener” user account. 
After logging in, we saw that there was an option to upload a profile picture, also called an avatar. 
This feature allows users to add a personal image to their account.
On your system, create a file called test.php, containing a script for fetching the contents of Carlos's secret file.

<?php echo file_get_contents('/home/carlos/secret'); ?>

We uploaded the test.php file. After that, we visited the page where the file was located. 
This allowed us to execute the script and view the information it returned.
We returned to the account page by clicking “Back to My Account,” we used Burp Suite to forward the requests. 
After that, we found the correct request in the history. By either checking the response, we were able to view the contents of the /home/carlos/secret file.
Next, we copy the flag and submit it to finish the challenge.
