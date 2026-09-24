# 📂 Path Traversal - Lab 01
File Path Traversal, Simple case 

## 🎯 Objective

To solve the lab, retrieve the contents of the /etc/passwd file.

## 🔍 Vulnerability

This lab contains a path traversal vulnerability in the display of product images.

# Solution:

Access lab ----->   open image in new tab ------------> capture request in burp -------->

The application loads product images as filenames, such as /image?filename=1.jpg.
Remove the image name 1.jpg and replace it with a relative path traversal technique ../../../etc/passwd to retrieve the contents of the /etc/passwd file.

