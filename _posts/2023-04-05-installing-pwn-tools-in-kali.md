---
layout: post
title: "How to install Pwn Tools in Kali Linux"
date: 2023-04-05
categories: reverse-engineering gdb
---

Hey guys, how are you all doing. In this post i will guide you through the installation process of gef. Gef is an extension for GDB (Gnu Debugger), gef enhances
the existing features of gdb to help with reverse engineering and rapid exploitation of linux binaries. So lets get started with the installation.

The whole installation guide is available on [hugsy.github.io/gef/](https://hugsy.github.io/gef/)

# Install GDB & Other Dependencies

Now first of all make sure gdb and python3 is installed and working:

`sudo apt-get install gdb python3 python3-pip`

And verify by running gdb, python3 and pip3 (or pip)

# Installing GEF

Now according to the official documentation you only have to run one command and it will install everything.

`bash -c "$(curl -fsSL https://gef.blah.cat/sh)"`

Wait till the installation is done and run gdb to check if gef is working properly.


EOF