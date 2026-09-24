# 💉 OS-Command-Injection - Lab 02
Blind OS Command injection with time delays

## 🎯 Objective
To solve the lab, exploit the blind OS command injection vulnerability to cause a 10 second delay

## 🔍 Vulnerability
This lab contains a blind OS command injection vulnerability in the feedback function.


## 📝 Methodology
>Click on Submit Feedback
>Enter random data and intercept the request using burpsuit.
>select /feedback/submit request and send it to repeater.
>When we send this request we get response in 439mills
>Then change the value of email parameter to & ping -c 10 127.0.0.1 &
>this will send 10 ICMP echo request packets to the loopback address 127.0.0.1.
>Then select this payload and Ctrl + U to url encode and send the request.
>Now we get response in 9640 millis
