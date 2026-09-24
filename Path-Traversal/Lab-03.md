# 📂 Path Traversal - Lab 03
File path traversal, traversal sequences stripped non-recursively.

## 🎯 Objective
To solve the lab, retrieve the contents of the /etc/passwd file.

## 🔍 Vulnerability
Using a simple path traversal sequence, such as ../etc/passwd or an absolute path, such as /etc/passwd, will not return the file’s content. This is because the application performs some validation. Stripping path traversal sequences as mentioned in the lab description. Thus, the user-supplied value ../etc/passwd becomes etc/passwd.

## 📝 Methodology
To solve this lab, we have to meticulously craft a payload that bypasses this validation. We know that the application strips ../. Therefore, we can provide a payload that represents a path traversal string after removing the initial payload.

Payload:/image?filename=....//....//....//etc/passwd
