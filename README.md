# gtm_playbook
The enclosed playbooks are meant to run against F5 BIG-IP GTM/DNS infrastructure.  For more information about F5, go to f5.com or contact your local partner or F5 sales engineer.
The aim is to provide sample playbooks that will create and delete objects in the BIG-IP devices.  The attached playbooks were run agains BIG-IP version 12.1.2 HF2 Virtual Edition. 

The playbooks will work with Ansible 2.5. Requirements:
-Python 2.7.10 or later
-bigsuds (pip install bigsuds)
-f5-sdk (pip install f5-sdk)

The files include 2 playbooks:
-playbook.yaml: creates a datacenter, server, virtual-server, pool and wideip
-undo-playbook.yaml: deletes the datacenter, server, virtual-server, pool and wideip

The target hosts are defined in the ./inventory/hosts file
The username, password are stored in the host_vars/[hostname] directory - current values are default BIG-IP username and passwords
To run the playbooks from the shell, from the directory where the playbook files are located:

[playbook-directory]\# ansible-playbook -i inventory/hosts playbook.yaml -vvv

or to delete the create objects:

[playbook-directory]\# ansible-playbook -i inventory/hosts undo-playbook.yaml -vvv

The playbooks leverage the REST and SOAP API's on the target BIG-IP.

The following resources provide documentation on the different modules used for this playbooks and some of the components that were needed to make this work:

https://docs.ansible.com/ansible/2.4/bigip_gtm_pool_module.html
http://clouddocs.f5.com/products/orchestration/ansible/devel/usage/installing-modules.html
https://github.com/F5Networks/f5-ansible
https://docs.ansible.com/ansible/2.4/bigip_gtm_virtual_server_module.html
http://clouddocs.f5.com/products/orchestration/ansible/devel/modules/bigip_gtm_datacenter_module.html
Fix pip after update: https://stackoverflow.com/questions/28210269/importerror-cannot-import-name-main-when-running-pip-version-command-in-windo
https://docs.ansible.com/ansible/2.4/bigip_gtm_pool_module.html
https://docs.ansible.com/ansible/2.4/bigip_gtm_wide_ip_module.html

The playbooks are provided as-is with no implied support.  Use at your own risk -
