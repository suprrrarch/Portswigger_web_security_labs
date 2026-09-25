## 📤 File-Upload vulnerability lab-05

Web shell upload via obfuscated file extension

## 🎯 Objective
To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the 
file /home/carlos/secret. Submit this secret using the button provided in the lab banner.


## 🔍 Vulnerability
This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this 
defense can be bypassed using a classic obfuscation technique.

## 📝 Methodology
You can log in to your own account using the following credentials: wiener:peter
When we tried to upload the shell.php file, the server returned an error message: “Sorry, only JPG and PNG 
files are allowed.” This shows that the server only accepts image files in those specific formats.
Press enter or click to view image in full size

Next, we modified the filename to shell.php%00.png, applying a null byte bypass 
technique. This allowed us to trick the server into accepting the file as a PNG image
Press enter or click to view image in full size

And if we send the request as it is, we get a 404 not found, this is 
because our application is unable to read the null byte in the URL
Because the null byte lets us ignore everything after it in the URL, we were able to restructure 
the URL to bypass the file type restriction.After that, we removed the %00.png part from the filename and sent the request once more.
Press enter or click to view image in full size


