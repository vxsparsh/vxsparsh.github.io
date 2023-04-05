---
layout: post
title: "How to install Pwn Tools + Command-Line Tools in Kali Linux"
date: 2023-04-05
categories: reverse-engineering pwn python
---

Hey everyone, its been a while since I have posted a blog. In this post i will guide you through the installation process of Pwntools and its command line tools.
pwntools is a CTF framework and exploit development library. Written in Python, it is designed for rapid prototyping and development, and intended to make exploit writing as simple as possible.

The whole installation guide is available on [https://docs.pwntools.com/en/stable/install.html](https://docs.pwntools.com/en/stable/install.html)

# Installing Pwntools

Just copy and paste the following commands one by one in your terminal.

```
sudo apt-get update
sudo apt-get install python3 python3-pip python3-dev git libssl-dev libffi-dev build-essential
sudo python3 -m pip install --upgrade pip
sudo python3 -m pip install --upgrade pwntools
```

And verify by running `from pwn import *` in python3 shell

# Installing Command-Line TOols

To be able to use pwn command-line tools you need to add the .local/bin folder in your home directory to path. You can do so by putting the following line in your bashrc or zshrc file.

`export PATH="home/kali/.local/bin$PATH"`

assuming your current username is kali, if not change `kali to your username` in the above command. Save the file and open a new terminal and type pwn to check if the command line tools are working.



EOF