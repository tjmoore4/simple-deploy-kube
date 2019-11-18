# simple-deploy-kube
Uses Vagrant and Ansible to deploy a single node Kubernetes cluster with StorageOS Installed

# Local Testing Environment for Development

Utilizing Vagrant and ansible provided here are instructions for a simple local testing enviroment to get up and running quickly for development of crunncy containers and or the crunchy postgres operator.

## Automated Kubernetes VM Deployment

The goal of the steps below is to have a basic virtual environment from which the Crunchy Containers and the Crunchy Postgres Operator can be utilized with a minimum of hands on configuration. At the end of this guide, you should have a functional VM test environment.

### Host Resource Installation

#### Git

First, Install git if not already installed.

```
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

```

#### VirtualBox

For the virtual machine itself, download and install VirtualBox

```
 virtualbox.org
```

#### Vagrant

Next, you will need to install Vagrant on your host operatoring system.

```
 https://www.vagrantup.com/intro/getting-started/install.html
```


{{% notice warning %}}vagrant 2.2.6 will error on MAC catalina when trying to install.  A work around can be found here:
```
https://github.com/hashicorp/vagrant/issues/11127
```
{{% /notice %}}

Once Installed, you will also neeed the Vagrant Host Manager, which is installed with the following command

```
vagrant plugin install vagrant-hostmanager
```

Finally you will need to clone the vagrant project reposity to you local system.

```
git clone https://github.com/tjmoore4/simple-deploy-kube.git

```

### Vagrant Project Deployment

Now that you environment is ready, cd to the newly created simple-deploy-kube folder and run

```
vagrant up
```

Once completed, run the command below to log into the new vm and view the availbe nodes

```
vagrant ssh kube1
kubectl get nodes
```

### Intallting the Crunchy Postgres Operator

After logging in, you can simply clone the Crunchy Postgres Operator project with

```
git clone https://github.com/CrunchyData/postgres-operator.git
```

And follow the installation guide provided

https://access.crunchydata.com/documentation/postgres-operator/4.1.0/


{{% notice tip %}}Please keep in mind that this VM is only configured to use StorageOS storage! If you’d like to use other storage options, those will need to be installed manually.
{{% /notice %}}
