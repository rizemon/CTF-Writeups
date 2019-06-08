# Fish

Written by: Tux

I got a weird image from some fish. What is this?

File: fish.jpg

## Solution

![](./fish.jpg)

Hm... That's a lot of white. However, running ```stegsolve``` did not return any results. Lets ```strings``` it.

![](./1.png)

We see a string ```bobross63```. Maybe this is some form of password? Lets use ```steghide``` along with the password.

![](./2.png)

It worked! Lets check ```flag.txt```

![](./3.png)

Flag: ```hsctf{fishy_fishy_fishy_fishy_fishy_fishy_fishy123123123123}```
