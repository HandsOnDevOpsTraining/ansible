ansible --version 		- To find the version of the Ansible running in Linux
apt-cache policy ansible	- It is used to display detailed information about a package's installation candidate and its associated repositories.

### Configuration
vi /etc/ansible/ansible.cfg
Add entries of the servers like below
	[webservers]
	hostname.com

### Adhoc commands
#### ansible list hosts
ansible dev --list-hosts
ansible dev[0] --list-hosts
ansible qa[0] --list-hosts

####
ansible dev -a "ls"
ansible dev[0] -a "touch file1"
#### -a stands for module arguments
ansible dev -a "sudo apt install maven -y"
#### -b stands for become as sudo
ansible dev -ba "sudo apt install maven -y"

### Modules
ansible -m ping <inventory-group>	 - command is used to test the connectivity and reachability of  the hosts within a specified Ansible inventory group using the `ping module’
vi /etc/ansible/ansible.cfg
host_key_checking = False
ansible -m ping aws-servers -i ansible_hosts
-i ansible_hosts: Specifies the inventory file to use, in this case, ansible_hosts. The inventory file contains a list of hosts and groups that Ansible uses to determine the target hosts for execution.
vi /opt/ansible/ansible_hosts
[aws-servers]
52.15.182.125 ansible_ssh_user=ubuntu ansible_ssh_private_key_file=/opt/ansible/ansible.pem
Setting variables
vi /opt/ansible/ansible_hosts
[aws-servers:vars]
ansible_ssh_user=ubuntu
ansible_ssh_private_key_file=/opt/ansible/ansible.pem
