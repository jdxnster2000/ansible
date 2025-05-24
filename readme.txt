production                # inventory file for production servers
staging                   # inventory file for staging environment

group_vars/
   group1.yml             # here we assign variables to particular groups
   group2.yml
host_vars/
   hostname1.yml          # here we assign variables to particular systems
   hostname2.yml

library/                  # if any custom modules, put them here (optional)
module_utils/             # if any custom module_utils to support modules, put them here (optional)
filter_plugins/           # if any custom filter plugins, put them here (optional)

site.yml                  # master playbook
webservers.yml            # playbook for webserver tier
dbservers.yml             # playbook for dbserver tier

roles/
    common/               # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies
        library/          # roles can also include custom modules
        module_utils/     # roles can also include custom module_utils
        lookup_plugins/   # or other types of plugins, like lookup in this case

    webtier/              # same kind of structure as "common" was above, done for the webtier role
    monitoring/           # ""
    fooapp/               # ""



Notes: 

Install Ansible

sudo apt-get install ansible

Install git client

sudo apt-get install git

Install sshpass
sudo apt-get isntall sshpass

Install pip
sudo apt-get install pip

Clone ansible repo with localhost and semaphore UI playbook

Clone ansible repo 2 with windows playbooks
Clone ansible repo 3 with linux playbooks

https://docs.ansible.com/ansible/latest/os_guide/windows_winrm.html#windows-winrm

Setup for psrp access

pip3 install "pypsrp<=1.0.0"  # for psrp

Enable winrm


inventory
[all:vars]


[linuxserver]
192.168.1.106

[linuxserver:vars]
ansible_connection=ssh
ansible_user=jd
ansible_ssh_pass=Trustme2!

[winserver]
192.168.1.107

[winserver:vars]
ansible_user=Administrator
ansible_password=Trustme2!

# psrp
ansible_connection=psrp
ansible_psrp_auth=basic

# winrm
ansible_connection=winrm
ansible_winrm_transport=basic

# disable certificate validation
ansible_psrp_cert_validation=ignore
ansible_winrm_server_cert_validation=ignore

Install chocolatey - reboot if chocolatey not installed at first attempt

---
- name: install edge
  hosts: winserver

  tasks:
  - name: install edge
    win_chocolatey:
       name: microsoft-edge
       state: latest
       ignore_checksums: yes

