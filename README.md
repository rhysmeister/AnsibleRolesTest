# AnsibleRolesTest

A Vagrant project to tests a few roles on my github


Creates the following virtual machines

mariadb1
mariadb2
nginx1
nginx2

and uses the following roles from githib

https://github.com/rhysmeister/common.git
https://github.com/rhysmeister/nginx.git
https://github.com/rhysmeister/mariadb10.3.git

# Installing Roles

ansible-galaxy install git+https://github.com/rhysmeister/common.git -p roles
ansible-galaxy install git+https://github.com/rhysmeister/nginx.git -p roles
ansible-galaxy install git+https://github.com/rhysmeister/mariadb10.3.git -p roles
