# 📂 Path Traversal - Lab 05
File path traversal, validation of start of path

## 🎯 Objective
To solve the lab, retrieve the contents of the /etc/passwd file.

## 🔍 Vulnerability
The application transmits the full file path via a request parameter and validates that the supplied path starts with the expected folder.

## 📝 Methodology
The application blocks both absolute and relative paths for accessing files outside of the intended directory. We can bypass this by adding dot-dot-slash (../) sequences after the intended path, which in this case is /var/www/images. This will navigate up the directory structure to access restricted files by attempting to traverse out of the web application’s root directory and access the system files.

/image?filename=/var/www/images/../../../etc/passwd
