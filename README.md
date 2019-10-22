# simple-deploy-kube
Uses Vagrant and Ansible to deploy a single node Kubernetes cluster with StorageOS Installed

# Kubernetes Deployment

The host environment needs to have the following software installed:

- Git
- VirtualBox
- Vagrant

This deployment also requires `vagrant-hostmanager` plugin:

```bash
$ vagrant plugin install vagrant-hostmanager
```

## Deploy

```bash
$ vagrant up
```

## Post Deployment

```bash
$ vagrant ssh kube1
$ kubectl get nodes
```
