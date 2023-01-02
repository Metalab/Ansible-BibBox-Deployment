Look, I'm a readme!


# ATTENTION - SECURITY WARNING!  

This setup is not secure by default and does not implement best practices (!). We ship default credentials with the config files for this Tomcat Setup and the RDP account. The username `metalab` and password `metalab` are hardcoded the config files.  
Also MD5 is used for the secrets in the config!  

**This is bad design and does not follow best practices - DO NOT USE THIS PROJECT IF YOU DON'T KNOW WHAT YOU ARE DOING! - Especially not in production systems of companies!** - **BUT:** In our case the guacamole client is publicy available on-site for all members and users and the credentials are no secrets. See: https://metalab.at/wiki/Libremote#Usage_Instructions  

# Implementation TODOs

Fix Audio via Ansible; see https://ubuntuforums.org/showthread.php?t=2459541  
Kill Lockscreen via systemd-timer; see https://notes.zerodogg.org/GNOME/lock-unlock-cli/  
`dbus-send --session --dest=org.gnome.ScreenSaver --type=method_call --print-reply --reply-timeout=20000 /org/gnome/ScreenSaver org.gnome.ScreenSaver.SetActive boolean:false`
# Project Info  

This Ansible Playbook installs and configures on a fresh Ubuntu 22.04 Installation a webservice to access the Desktop via Webinterface.  

It uses RDP of the Ubuntu built-in Gnome Resktop Desktop Feature. Apache Guacamole Server (https://github.com/apache/guacamole-server) proxies the RDP and the Guacamole Client that is locally served via Apache Tomcat provides the Webclient.

It is used in the Metalab for the Streaming and Presentation Setup in the Library. The Project Webpage is available under: https://metalab.at/wiki/Libremote  

Used Reference for the installation and configuration:  

* https://idroot.us/install-apache-guacamole-ubuntu-22-04/  
* https://gitlab.gnome.org/-/snippets/1778
* https://ask.fedoraproject.org/t/enable-gnome-screen-sharing-via-commandline/6837/2
* https://ubuntuforums.org/showthread.php?t=2459541

# Prerequisites  

1. Install a fresh Ubuntu 22.04 with auto login enabled
2. Install and enable SSH Server

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
