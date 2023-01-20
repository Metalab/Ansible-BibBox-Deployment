Look, I'm a readme!


# ATTENTION - SECURITY WARNING!  

This setup is not secure by default and does not implement best practices (!). We ship default credentials with the config files for this Tomcat Setup and the RDP account. The username `metalab` and password `metalab` are hardcoded the config files.  
Also MD5 is used for the secrets in the config!  

**This is bad design and does not follow best practices - DO NOT USE THIS PROJECT IF YOU DON'T KNOW WHAT YOU ARE DOING! - Especially not in production systems of companies!** - **BUT:** In our case the guacamole client is publicy available on-site for all members and users and the credentials are no secrets. See: https://metalab.at/wiki/LibRemote#Usage_Instructions  

# (Implementation)TODOs  
* Implement Wake on LAN (WoL)
* Add the PC to the Shutdown procedure. maybe via SSH and sending the shutdown command?

## Done  
* Add the shutdown command to sudoers file with NOPASSWD option for the metalab user, so triggering shutdown via guacamole does not prompt for a password

## Not feasible  
* Lockscreen Option is deactivated by default: Implement Kill Lockscreen as Guacamole Shell Option; see https://notes.zerodogg.org/GNOME/lock-unlock-cli/  
`dbus-send --session --dest=org.gnome.ScreenSaver --type=method_call --print-reply --reply-timeout=20000 /org/gnome/ScreenSaver org.gnome.ScreenSaver.SetActive boolean:false`

# Project Info  

This Ansible Playbook installs and configures on a fresh Ubuntu 22.04 Installation a webservice to access the Desktop via Webinterface.  

It uses RDP of the Ubuntu built-in Gnome Remote Desktop Feature. Apache Guacamole Server (https://github.com/apache/guacamole-server) proxies the RDP and the Guacamole Client that is locally served via Apache Tomcat provides the Webclient.

It is used in the Metalab for the Streaming and Presentation Setup in the Library. The Project Webpage is available under: https://metalab.at/wiki/LibRemote  

After deployment the guacamole client is available under Port 80.  
So just visit <Hostname/IP> in your web browser and enjoy the remote session.

Used Reference for the installation and configuration:  

* https://idroot.us/install-apache-guacamole-ubuntu-22-04/  
* https://gitlab.gnome.org/-/snippets/1778
* https://ask.fedoraproject.org/t/enable-gnome-screen-sharing-via-commandline/6837/2
* https://ubuntuforums.org/showthread.php?t=2459541

# Prerequisites  

1. Install a fresh Ubuntu 22.04 with auto-login enabled
2. Install the `ssh` Package
3. Create the gnome keychain with an empty password. (You should be prompted with a dialogue after first boot)

# How To Deploy  

Configure the `inventory.ini` accordingly to the (Library) PC IP settings.

Run the Playbook as following:
`ansible-playbook deploy_bibBox.yml -t deploy -kK`

or with more details:  
`ansible-playbook deploy_bibBox.yml -t deploy -kK -vv`

and provide the user password for Ansible.

Roles should be self explanatory according to the code. Check the roles in the corresponding roles folder.  
If you have questions please ask around or use the search engine of your choice!

# Ansible Playbook Guidelines  

All commits should follow the Ansible Best Practices.
This includes checking the code with the `ansible-lint` tool.

**Remember: no dashes ("-") in group names!**

# Useful Links/Resources  

Ansible collections (functions) documentation:  
https://docs.ansible.com/ansible/latest/collections/index.html  

Making a Handler global:  
https://serverfault.com/a/928205  

Inventory File Documentation:  
https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html  

Ansible Inventory File Guide:  
https://www.educba.com/ansible-inventory-file/  