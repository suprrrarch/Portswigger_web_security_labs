## 📤 File-Upload vulnerability lab-07
Web shell upload via race condition


## 🎯 Objective
To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of 
the file /home/carlos/secret. Submit this secret using the button provided in the lab banner. 

## 🔍 Vulnerability

This lab contains a vulnerable image upload function. Although it performs robust validation on any files that 
are uploaded, it is possible to bypass this validation entirely by exploiting a race condition in the way it processes them. 

## 📝 Methodology
<?php echo file_get_contents(‘/home/carlos/secret’); ?>

in a text doc and save it as abc.php intercept the request send it to intruder and 
also the get request to intruder start both the get and post requests with null payload and look for 200 code
