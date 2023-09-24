#### Default location of ansible
/etc/ansible

#### location of config file in ansible
/etc/ansible/ansible.cfg

#### Values to be modified in ansible.cfg
inventory = /etc/ansible/hosts
sudo_user = root

#### Create a new user ansible for all ansible operations
useradd ansible

#### Create a password for the user ansible & give Training@123 as password
passwd ansible

#### Give root privileges to ansible
visudo
##### Next to root ALL=(ALL)   ALL, add below
ansible    ALL=(ALL:ALL)   NOPASSWD:   ALL
##### Update PasswordAuthentication in SSH as yes
vi /etc/ssh/sshd_config
PasswordAuthentication yes
##### Do the same for other EC2 instances


##### Run below in All Servers:
sudo systemctl restart sshd
sudo systemctl status sshd

##### LOGIN as ansible in all servers by using
su - ansible

##### Generate SSH Keys
ssh-keygen
ssh-copy-id ansible@localhost
ssh ansible@localhost
hostname -i


ssh-copy-id ansible@dev-ip-address
ssh-copy-id ansible@qa-ip-address

