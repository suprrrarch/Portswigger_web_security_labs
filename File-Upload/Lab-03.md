
## 📤 File-Upload vulnerability lab-03
Web shell upload via path traversal

## 🎯 Objective
To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file /home/carlos/secret. 
Submit this secret using the button provided in the lab banner.

## 🔍 Vulnerability
This lab contains a vulnerable image upload function. The server is configured to prevent execution of 
user-supplied files, but this restriction can be bypassed by exploiting a secondary vulnerability.


## 📝 Methodology
You can log in to your own account using the following credentials: wiener:peter
We uploaded the shell.php file and captured the request. Upon reviewing the request, we saw 
that the filename was set as test.php. In the response, we received a message saying, “The file avatars/test.php has been uploaded.”
We opened the image in a new tab and captured its network request. In the response, instead of running 
our shell file, we only saw its plain text code. This tells us that the /files/avatars directory does not allow shell scripts to execute — it only displays the file content as raw text.
We changed the filename to %2e%2e%2fshell.php. The string %2e%2e%2f is the URL-encoded form of “../”. 
This means that we tried to upload our file to the /files/ directory instead of the avatars folder.
After reopening the image in a new tab, we managed to retrieve the content of /home/carlos/secret. 
This success allowed us to complete the lab.
