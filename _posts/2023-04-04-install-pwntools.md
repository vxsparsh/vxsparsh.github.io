---
layout: post
title: "Install Pwntools + Command-Line Tools in Kali Linux"
date: 2023-04-04
categories: pwn
---

Hey everyone, I am writing a blog after a very long time. In this blog i will take you through the installation process of pwntools and its command-line tools in kali linux.




Pwntools is a python ctf library designed for rapid exploit development. It essentially help us write exploits quickly, and has a lot of useful functionality behind it. Also one thing to note, pwntools has Python2 and Python3 versions. (Source: guyinatuxedo.github.io)
<br> <br> <br>





# Installation Process

Copy and Paste the following commands in your terminal one by one.

```
apt-get update
apt-get install python3 python3-pip python3-dev git libssl-dev libffi-dev build-essential
python3 -m pip install --upgrade pip
python3 -m pip install --upgrade pwntools
```
The above commands are taken from the official [https://docs.pwntools.com/en/stable/install.html](pwntools documentation)
Once all these commands are executed, you can verify whether pwntools is correctly installed or not by typing python3 in terminal and then typing:
```
from pwn import *
```
If this command executes without any errors then pwntools is correctly installed.

# Installing Command-Line Tools
To install the pwn command line tools open a new terminal and type 
```nano .zshrc``` 
if you are using zsh. If you are using bash then type
 ```nano .bashrc```

Go to the bottom of the file and type:
```export PATH="/home//kali/.local/bin$PATH"```

and save the file. Open a new terminal and type pwn to verify the command line tools are working.


EOF
