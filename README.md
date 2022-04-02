# Sela-Week6-Ansible
## General

1. Create the Terraform infrastructure, one for each environemt
    - terraform select production; terraform apply
    - terraform select staging; terraform apply
1. Check for the outputs: 
    - Connection string to the database 
    - Load balancer IP address
    - User names and passwords for the VMs
1. Set in your Okta account, in the right application settings with the new LB IP. Note you need to have **2 applications**, one for each envirnment (and each one has a different IP for its own load balancer and of course a different key and secret for the .env file)

## Ansible guide lines

### Installation
1. Install ansible on each of the ansible machines (2 different submets with no connectioin between them):
    - sudo apt update
    - sudo apt install ansible
1. Create sshkey for ansible and copy to all web servers, or ansible will not be able to connect to them
1. Copy the ssh key to all web servers
### Configuration
1. Set the ansible config gile to set your inventory hosts file and ssh key you just created
    - Edit ansible.cfg
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
1. Run ansible-playbook install_site.yml --ask-become-pass

