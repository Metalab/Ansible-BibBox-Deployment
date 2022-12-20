Look, I'm a readme!

# Ansible Playbook Guidelines

All commits should follow the Ansible Best Practices.
This includes checking the code with the `ansible-lint` tool.

# How To Deploy

Configure the `inventory.ini` accordingly to the Library PC IP settings.

Run the Playbook as following:
`ansible-playbook deploy_bibBox.yml -t deploy -kK`

or with more details:  
`ansible-playbook deploy_bibBox.yml -t deploy -kK -vv`


Roles should be self explanatory according to the code. Check the roles in the corresponding roles folder.  
If you have questions please ask arround or use the search engine of your choice!
 
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
