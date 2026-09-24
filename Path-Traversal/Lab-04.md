# 📂 Path Traversal - Lab 04
File path traversal, traversal sequences stripped with superfluous URL-decode.

## 🎯 Objective
To solve the lab, retrieve the contents of the /etc/passwd file.

## 🔍 Vulnerability
The application blocks input containing path traversal sequences. It then performs a URL-decode of the input before using it.


## 📝 Methodology

Solutions from previous labs won’t work here because, as stated in the lab description, the application first strips path traversal sequences and then decodes the input. Simply URL encoding the payload is also ineffective, as one level of URL decoding is usually done by the server upon receiving the request. Therefore, encoding ../ as %2e%2e%2f is insufficient. The server decodes the URL and passes ../ to the application, which filters it out.

To bypass this, we can URL-encode the encoded string again.
../ --> ..%2F --> ..%252F
After double encoding the payload /image?filename=../../../etc/passwd, the final result is the following.

/image?filename=%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66etc/passwd

