## 📤 File-Upload vulnerability lab-02
Web Shell upload via content-type restriction bypass


## 🎯 Objective
To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file /home/carlos/secret. 
Submit this secret using the button provided in the lab banner.

## 🔍 Vulnerability
This lab contains a vulnerable image upload function. It attempts to prevent users from uploading unexpected file types, 
but relies on checking user-controllable input to verify this.


## 📝 Methodology
We started by uploading our shell file and capturing the request. Afterward, we sent the request to Repeater. 
In the response, we got an error message that said, “Only image/jpeg and image/png files are allowed.” When we 
checked the request, we saw that the file’s Content-Type was set to application/octet-stream
Next, we changed the Content-Type to image/jpeg and sent the request again. This time, we 
received a 200 OK response, which means the request was successful.

After that, we went to the site, opened the image in a new tab, and were able to successfully see the flag.
