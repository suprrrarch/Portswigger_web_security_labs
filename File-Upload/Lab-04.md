
## 📤 File-Upload vulnerability lab-04
Web shell upload via extension blacklist bypass

## 🎯 Objective
To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the 
file /home/carlos/secret. Submit this secret using the button provided in the lab banner.

## 🔍 Vulnerability
This lab contains a vulnerable image upload function. Certain file extensions are blacklisted,
but this defense can be bypassed due to a fundamental flaw in the configuration of this blacklist.

## 📝 Methodology
You can log in to your own account using the following credentials: wiener:peter
I attempted to upload our test.php file, but instead of success, we received an 
error message saying, “Sorry, PHP files are not allowed.”
In Burp Repeater, open the tab for the POST /my-account/avatar request. Look for the part of the request body that includes your PHP file. Then, do the following changes:

    Change the value of the filename parameter to .htaccess.
    Change the value of the Content-Type header to text/plain.
    Replace the file’s content with the Apache directive:
    AddType application/x-httpd-php .shell

In Burp Repeater, click the back arrow to go back to the original request for uploading your PHP exploit. 
Next, change the filename parameter from test.php to test.shell. Then, send the request again and notice that the file was uploaded successfully.
After we uploaded our test.shell file, we refreshed the page and saw the flag
