# Sela-Week7-Ansible
## Ansible guide lines
### Installation
1. Install ansible on each of the ansible machines (2 different submets with no connectioin between them):
    - sudo apt update
    - sudo apt install ansible
    - sudo apt-get install unzip
1. Create sshkey for ansible and copy to all web servers, or ansible will not be able to connect to them
  - ssh-keygen -t ed25519 -C "ansible"
  - Save it as /home/azureuser/.ssh/ansible in your .ssh directory 
  - Do not enter passphrase (or you will be asked to do it everytime ansible connects)
1. Copy the ssh key to all web servers
  - ssh-copy-id -i /home/azureuser/.ssh/ansible.pub x.x.x.x
### Configuration
1. Create your working dir (for example Sela-Week6-Ansible) and change dir to that
1. Set the ansible config gile to set your inventory hosts file and ssh key you just created
    - Edit ansible.cfg
	- [defaults]
        - inventory = inventory
        - private_key_file = ~/.ssh/{your ssh private key file}
1. Set your inventory file with the IP address of the VMs of the relevant envirnment
```
    [webservers]
    x.x.x.x
    x.x.x.x
    x.x.x.x
    x.x.x.x
```

1. Check connection to the servers with ping: ansible webservers -m ping. Then check all is ok with all servers
1. Copy run_node and staging.env / production.env to the ansible files directory
1. Run ansible-playbook install_site.yml 

