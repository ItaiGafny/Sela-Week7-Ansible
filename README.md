# Sela-Week7-Ansible
## Ansible guide lines
### Installation
1. Install ansible on each of the ansible machines (2 different submets with no connectioin between them):
    - sudo apt update
    - sudo apt install ansible
    - sudo apt-get install unzip
    - sudo apt-get install zip
1. Create sshkey for ansible and copy to all web servers, or ansible will not be able to connect to them
  - ssh-keygen -t ed25519 -C "ansible"
  - Save it as /home/azureuser/.ssh/ansible in your .ssh directory 
  - Do not enter passphrase (or you will be asked to do it everytime ansible connects)
1. Copy the ssh key to all web servers
  - ssh-copy-id -i /home/azureuser/.ssh/ansible.pub x.x.x.x
### Configuration
The Ansible configuration (hosts file, inventory, etc.) is done using the pipeline.
