This simplified implementation of 'simply deploy kube' assumes the VM/server/etc you wish
to install Kubernetes and StorageOS on is already configured and ready to go.

Just install Git:
```
sudo yum install -y git
```
and install Ansible:
```
sudo yum install -y ansible
```
update the inventory file:
```
vi inventory
```
then run the ansible playbook:
```
ansible-playbook -i inventory --ask-become main.yml
```
and you're good to go!

