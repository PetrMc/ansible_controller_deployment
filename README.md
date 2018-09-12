# ansible_controller_deployment
Basic controller rollout on CentOS with Ansible playbook

IP Addresses are defined on every host at /etc/sysconfig/network-scripts/ifcfg-ens160:

BOOTPROTO=static
IPADDR=192.168.38.XXX
NETMASK=255.255.255.0
GATEWAY=192.168.38.1
ONBOOT=yes

Optionally adjust hostname:
/etc/hosts adding "192.168.38.XXX hostname" line

'service network restart' command to get ip address reset to the new settings

Controllers:
IP Addresses - 192.168.38.221/2/3
SEs 
IP Addresses - 192.168.38.225/6
WebServers - 192.168.38.228/9

the docker_install.tar.gz install file should be placed at 192.168.38.228 (after wget is installed  yum install wget) - location of  /var/www/html/

ansible server 192.168.38.239
yum install git, ansible
git init
git pull https://github.com/PetrMc/ansible_controller_deployment.git
git list
ssh-keygen
ssh-copy-id root@192.168.38.221
ssh-copy-id root@192.168.38.222
ssh-copy-id root@192.168.38.223
ssh-copy-id root@192.168.38.224
ssh-copy-id root@192.168.38.225
ssh-copy-id root@192.168.38.226
ssh-copy-id root@192.168.38.228
ssh-copy-id root@192.168.38.229
ansible-playbook -i hosts centos-basic.yaml
ansible-playbook -i hosts controllers_install.yaml

git config --global user.email "petr.mcallister@gmail.com"
git config --global user.name "PetrMc"
git add .
git commit
git push https://github.com/PetrMc/ansible_controller_deployment.git
