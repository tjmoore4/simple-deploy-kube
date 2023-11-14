# Install instructions

This simplified implementation of 'simply deploy kube' assumes the VM/server/etc you wish
to install Kubernetes and the Rancher hostpath provisioner is already configured and ready to go.

Just install Git:
```
sudo dnf install -y git
```
and install Ansible:
```
sudo dnf install -y python3
pip3 install ansible --user
```

if this results in an error, run
```
pip3 install -U pip --user
```
as well.

update the inventory file (proper IPs, hostname, kube version, etc)
```
vi inventory
```

update the kube version
in
`roles/kube-base/files/kubernetes.repo`
and/or the version numbers in
`roles/calico/tasks/main.yml`
if needed.
TODO: add necessary values to inventory file

[NOTE: see below for kube 1.21 or below]
then run the ansible playbook:
```
ansible-playbook -i inventory --ask-become main.yml
```
and you're good to go!

## cgroupfs to systemd change

\*When running kube 1.21 or below:

Per https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/configure-cgroup-driver/#configuring-the-kubelet-cgroup-driver
starting in kube 1.22, the default cgroup driver is `systemd` instead of `cgroupfs`. If installing on an earlier version
https://github.com/tjmoore4/simple-deploy-kube/blob/onlyAnsibleCentos8Crio/roles/kube-base/files/02-cgroup-manager.conf
will need to be updated accordingly.

## master to control-plane change

For Kubernetes versions below 1.24, step 

```
- name: Taint Master Node
  shell: kubectl taint nodes --all node-role.kubernetes.io/control-plane-
```

in roles/kube-master/tasks/main.yml needs to be updated to

```
- name: Taint Master Node
  shell: kubectl taint nodes --all node-role.kubernetes.io/master-
```

