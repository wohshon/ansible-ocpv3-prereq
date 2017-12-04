# Pre-req for OCP installation on AWS


This script runs the following steps required for the pre-requisites for OCP installation

- create instances (master and nodes, currently 1 master 2 nodes)

- install prerequisites (based on 3.7)

 This setup looks for a vault file under vars/secrets.yml (not in this repo for obvious reasons). The values required  (RHN ID and password) are outlined in the comments in vars/vars.yml
 - The password for the vault is maintained in another file which you have to provide
 - To run the playbook

	```
	ansible-playbook -i hosts site.yml -e "jump_server_ip=54.255.191.5"  --vault-password-file ./pw.txt -v 

	```

Need to provide public ip for jump host if it is dynamic

 - To retry the playbook, need to unregister the system first or you can skip the registration task

 	```
	ansible-playbook -i hosts site.yml --tags "unsub" -e "jump_server_ip=54.255.191.5"  --vault-password-file ./pw.txt -v 

	ansible-playbook -i hosts site.yml --skip-tags "rhn-sub" -e "jump_server_ip=54.255.191.5"  --vault-password-file ./pw.txt -v 

 	```
