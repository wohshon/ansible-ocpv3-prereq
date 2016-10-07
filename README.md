# Pre-req for OCP installation

	ansible-playbook -i hosts-prereq site.yml --skip-tags "unsub" --vault-password-file ~/osev3/pw.txt
