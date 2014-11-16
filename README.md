Minecraft service
=================

A Minecraft server init script for debian based distributions that aims to be a simple and robust service with basic functionality of starting, stopping, restarting and checking the status of a server.

This script does not provide fancy features such as backup or ramdisk, there's already a plethora of great scripts that can handle those kind of features. Instead, this script provides a simple base that doesn't require any extra installs and can be used for writing your own customized server environment.

**Tested on**

- Ubuntu 14.04

Features
--------

- Server commands using fifo
- LSB standards for init scripts, see [Linux Standard Base Core Specification 3.1](http://refspecs.linuxbase.org/LSB_3.1.1/LSB-Core-generic/LSB-Core-generic/iniscrptact.html)
- Multiple servers

Installation
------------

1. `git clone https://github.com/edvind/minecraft-service.git`
2. `cd minecraft-service`
3. `cp config.default config`
4. `pico config`*
5. `chmod +x minecraft`
6. `sudo ln -s /path/to/minecraft-service/minecraft /etc/init.d/minecraft`
7. `sudo ln -s /path/to/minecraft-service/config /etc/default/minecraft`

(*) Make any changes you need, point `location` to your full server path and make sure `user` can read and write to it.

Start it up
-----------

`service minecraft start` (or `/etc/init.d/minecraft start`) starts the server.

FAQ
---

Q: What if I don't have a server to point the full server path in the config?

A: If you're not feeling awkward by running scripts from the net you could initiate: `bash <(wget -qO- https://gist.githubusercontent.com/edvind/c1e0afbd40006f6183f3/raw/a116876e340f5780b2dfb5a0c3a077b9e3899935/install.sh)` for a guided installation and download of minecraft_server.jar


Q: How do I configure multiple servers?

A: Symlink (or copy) the minecraft script to an init.d script with a different name, eg. `sudo ln -s /path/to/minecraft-service/minecraft /etc/init.d/minecraft-creative` and create another config file and symlink (or copy) it to its corresponding `/etc/default/minecraft-creative`.