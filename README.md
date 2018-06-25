# I2P

Ansible role to provision a linux system with I2P ([geti2p.net](https://get2ip.net) - Invisible Internet Project)

Requirements
------------

 - java - in order to run I2P
 - pip - for installing pexpect, which is used for the interactive I2P installer

Role Variables
--------------

 - i2p\_version - version of I2P to download and install **(default 0.9.34)**
 - i2p\_sha256sum - checksum to verify installer **(default 61a255911dbe6a3196ddae9c445ffa543c321320f98f48dc880d6f0e0cc0a259)**
 - i2p\_user - user for I2P installation and runtime. By default the .i2p config directory will also be created inside this users home directory. You will need to create this user beforehand in a pre\_tasks section, or reuse one (other than root) already available on your server **(default i2p)**
 - i2p\_install\_path - installation location for I2P, should be i2p\_user writable **(default /home/{{ i2p\_user }}/i2p)**

Example Playbook
----------------

    - hosts: i2p.nodes
      pre_tasks:
        - user: name=i2p createhome=yes state=present
      roles:
        - geerlingguy.java 
        - geerlingguy.pip

        - role: grooveadelic.i2p
          i2p_install_path: /home/i2p/router/

License
-------

GPLv3

## Contribute

Bug reports, flag/toggle proposals, patches and donations[1] welcome.

[1] litecoin - ltc1qudlkn0kmca4xhypz4wmkxhtzmwgm80sl93larn
