# simple-deploy-kube
Uses Vagrant and Ansible to deploy a single node Kubernetes cluster with StorageOS Installed

# Kubernetes Deployment

This deployment requires `vagrant-hostmanager` plugin:

```bash
$ vagrant plugin install vagrant-hostmanager
```

## Deploy

```bash
$ vagrant up
$ ansible-playbook -i inventory main.yml
```

## Post Deployment

```bash
$ vagrant ssh kube1
$ kubectl get nodes
```
