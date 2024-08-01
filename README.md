Ansible Basics

Files
-----
1. /etc/ansible/ansible.cfg
2. /etc/sudoers.d/ansible
3. /var/log/apt/history.log
4. /var/log/apt/apt/term.log

Environment Prep Commands
-------------------------
1. sudo useradd -d /home/ansible -m ansible -s /bin/bash
   sudo passwd ansible
2. su - ansible
   mkdir $HOME/.ssh
   ssh-keygen
   git config --global user.email "<email_addr>"
   git config --global user.name "Tim Stilwell"
3. scp $HOME/.ssh/id_ed25519* ansible@<remote_host>:/home/ansible/.ssh

Packages Commands
-----------------
1. sudo apt update
2. sudo apt dist-upgrade
3. sudo apt list --upgradable
4. sudo apt search <package>
5. sudo apt upgrade=dist

Ansible Commands
----------------
1. ansible all --list-hosts
2. ansible all -m ping
3. ansible all -m gather_facts 
4. ansible all -m apt -a update_cache=true --become --ask-become-pass
4. ansible all -m apt -a name=vim-nox --become --ask-become-pass
5. ansible all -m apt -a "name=snapd state=latest" --become --ask-become-pass
6. ansible all -m apt "upgrade=dist" --become --ask-become-pass
7. ansible-playbook --ask-become-pass <playbook>.yml

Playbook Hints
--------------
1. playbook states: 
   i. ok=             total tasks executed from playbook
   ii. changed=       total tasks where update occurred
   iii. unreachable=  total tasks unaccomplished at time of playbook execution
   iv. failed=        total tasks where update failed
   v. skipped=        total tasks skipped because conditions not met
   vi. rescued=       task executed only because previous task failed
2. install package uses
   ansible.builtint.apt:
     update_cache: yes
     name: <package=version>
     state: latest
3. remove package uses
   ansible.builtint.apt:
     update_cache: yes
     name: <package=version>
     state: absent

Recommended Documentation
-------------------------
1. https://docs.ansible.com/ansible/latest/modules/apt_module.html
2. https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_error_handling.html

Recommended Videos
------------------
1. Getting Started with Ansible
   https://youtu.be/3RiVKs8GHYQ?si=l8EYwvLIKbwJo_dk
2. SSH Overview & Setup
   https://youtu.be/-Q4T9wLsvOQ?si=agLjlWcnLTdXdDTI
3. Git Repository
   https://youtu.be/FFaMqxpphjo?si=d7dRquLYrLMNsBzx
4. Ansible ad-hoc commands
   https://youtu.be/4REljLsOnXk?si=mTwLfT8AzD0AX5dP
5. Ansible elevated ad-hoc commands 
   https://youtu.be/FPU9_KDTa8A?si=Ij5jTBH5DjG2dga3
6. Ansible Playbook
   https://youtu.be/VANub3AhZpI?si=7TyYG6-a1NQUyeIh
