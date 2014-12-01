Minecraft service
=================

A Minecraft server init script for debian based distributions that aims to be a simple and robust service with basic functionality of starting, stopping, restarting, updating and checking the status of a vanilla Minecraft server.

This script does not provide fancy features such as compatibility with modified servers or ramdisk, there's already a plethora of great scripts that can handle those kind of features. Instead, this script provides a simple base that doesn't require any extra installs and can be used for writing your own customized server environment.

Latest code can be found in development branch. Please report any bugs that you encounter.

**Tested on**

- Ubuntu 14.04

Features
--------

- Server commands using fifo
- LSB standards for init scripts, see [Linux Standard Base Core Specification 3.1](http://refspecs.linuxbase.org/LSB_3.1.1/LSB-Core-generic/LSB-Core-generic/iniscrptact.html)
- Multiple servers
- Updating

Installation
------------

**Server**

If you already have a server, you can skip to the Script part below. To install a Minecraft server you can run the following command that starts an interactive installation. Create the user (and login as that user) that will run the server prior to issuing the line:

`bash <(wget -qO- https://gist.githubusercontent.com/edvind/c1e0afbd40006f6183f3/raw/0064265e9e9fc1ce5dc1b0ca9c3cdc042a94e589/install.sh)`

To create a user on Debian based systems you can run the command `adduser <username>`. 


**Script**

1. `git clone https://github.com/edvind/minecraft-service.git`
2. `cd minecraft-service`
3. `cp config.default config`
4. `pico config`*
5. `chmod +x minecraft`
6. `sudo ln -s /path/to/minecraft-service/minecraft /etc/init.d/minecraft`
7. `sudo ln -s /path/to/minecraft-service/config /etc/default/minecraft`

(*) Make any changes you need, point `location` to a full server path and make sure `user` can read and write to it.

Start it up
-----------

`service minecraft start` (or `/etc/init.d/minecraft start`) starts the server. If you want the Minecraft server to be automatically started on system boot: `update-rc.d minecraft defaults`

FAQ
---

Q: How do I configure multiple servers?

A: Symlink (or copy) the minecraft script to an init.d script with a different name, eg. `sudo ln -s /path/to/minecraft-service/minecraft /etc/init.d/minecraft-creative` and create another config file and symlink (or copy) it to its corresponding `/etc/default/minecraft-creative`.


Q: How do I send a command to the server?

A: Either use the built-in command using `service minecraft command "server command here"` or echo to specified fifo in config; eg. `echo "your command here" > /path/to/console.input`