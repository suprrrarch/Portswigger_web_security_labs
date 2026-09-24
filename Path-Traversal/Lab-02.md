# 📂 Path Traversal - Lab 02
File Path traversal sequences blocked with absolute path bypass.

## 🎯 Objective
To solve the lab, retrieve the contents of the /etc/passwd file.


## 🔍 Vulnerability
The application blocks traversal sequences but treats the supplied filename as being relative to a default working directory.

## 📝 Methodology
The image catalog showcases a collection of products. Each product is displayed with an image, title, price, star rating, and a “View details” button. The application loads product images using the filename query /images?filename=1.jpg.

In the requester tab of Burp Suite, replace the image name 1.jpg with the absolute path of the passwd file /etc/passwd.

