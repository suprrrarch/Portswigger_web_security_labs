# 📂 Path Traversal - Lab 06
File path traversal, validation of file extension with null byte bypass


## 🎯 Objective
To solve the lab, retrieve the contents of the /etc/passwd file.

## 🔍 Vulnerability
The application validates that the supplied filename ends with the expected file extension.

## 📝 Methodology
What is Null Byte?

The null character (also null terminator) is a control character with the value zero. It is a special character used to indicate the end of a string in languages like C and C++. It helps define string boundaries in memory but can also appear in binary data, file formats, and network protocols. In security, null byte injection was a common exploit where attackers inserted %00 to manipulate file handling or bypass validation in poorly coded applications.

Solution:

The application validates that the supplied filename ends with the expected file extension, meaning it will only return a response if the filename ends with a valid image extension, likely .jpg or .png. However, we know that the /etc/passwd file is a plain text file. Thus, we can use Null Byte to truncate the file path by prematurely ending the string and bypassing security filters or file extension checks.

Payload:
/image?filename=../../../etc/passwd%00.jpg
