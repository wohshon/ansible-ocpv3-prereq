# Pre-req for OCP installation

This script runs the 'Host preparation' steps required for the pre-requisites for OCP installation (v 3.3)

It covers all the steps from RHN registration till public key distribution from master node to all other nodes

Installation will be done separately, it will be integrated to this playbook at a later date  
(Installation playbook will be run from the master node)

Installation of standalone registry will be done separately

## Environment

 - The hosts file points to 4 VM instances (1 master, 2 nodes, 1 standalone registry).
 - This setup looks for a vault file under vars/secrets.yml (not in this repo for obvious reasons). The values required  (RHN ID and password) are outlined in the comments in vars/vars.yml
 - The password for the vault is maintained in another file which you have to provide
 - To run the playbook

	ansible-playbook -i hosts-prereq site.yml --skip-tags "unsub" --vault-password-file ~/osev3/pw.txt

 - To retry the playbook, need to unregister the system first or you can skip the registration task

 	ansible-playbook -i hosts-prereq site.yml --tags "unsub" --vault-password-file ~/osev3/pw.txt

 	ansible-playbook -i hosts-prereq site.yml --skip-tags "rhn-sub" --vault-password-file ~/osev3/pw.txt
