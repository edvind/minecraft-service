Minecraft service
=================

A Minecraft server init script for debian based distributions that aims to be a simple and robust script with basic functionality of starting, stopping, restarting and checking the status of a server.

This script does not provide fancy features such as backup or ramdisk, there's already a plethora of great scripts that can handle those kind of features. Instead, this script provides a simple base that doesn't require any extra installs and can be used for writing your own customized server environment.

**Tested on**

- Ubuntu 14.04

Features
--------

- Server commands using fifo (eg. `echo "say This is the server admin speaking." > console.input`)
- LSB standards for init scripts, see [Linux Standard Base Core Specification 3.1](http://refspecs.linuxbase.org/LSB_3.1.1/LSB-Core-generic/LSB-Core-generic/iniscrptact.html)

Installation
------------

1. `git clone https://github.com/edvind/minecraft-service.git`
2. `cd minecraft-service`
3. `cp config.default config`
4. `pico config`  (make any changes you need)
5. `chmod +x minecraft`
6. `sudo ln -s /path/to/minecraft-service/minecraft /etc/init.d/minecraft`
7. `sudo ln -s /path/to/minecraft-service/config /etc/default/minecraft`

Start it up
-----------

When configuration is pointed to a Minecraft server directory:

`service minecraft start` (or `/etc/init.d/minecraft start`) starts the server.
