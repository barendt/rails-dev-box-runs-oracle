# A Virtual Machine for Ruby on Rails Core Development with Oracle database

## Introduction

This project supports to provide a Oracle database support on top of rails-dev-box. 

## Requirements

* [VirtualBox](https://www.virtualbox.org)

* [Vagrant 1.1+](http://vagrantup.com)

* VirtualBox needs support 64-bit guest OS

## How To Build The Virtual Machine

Building the virtual machine is this easy:

* Download [Oracle Database 11g Express Edition](http://www.oracle.com/technetwork/products/express-edition/overview/index.html) for Linux x64. The file name is `oracle-xe-11.2.0-1.0.x86_64.rpm.zip`.

```sh
    host $ git clone https://github.com/yahonda/rails-dev-box-runs-oracle.git
    host $ cp oracle-xe-11.2.0-1.0.x86_64.rpm.zip rails-dev-box-runs-oracle/puppet/modules/oracle/files/.
    host $ cd rails-dev-box-runs-oracle
    host $ git checkout delayed_provisioning
    host $ vagrant up
    host $ vagrant ssh
    vagrant@rails-dev-box:~$ sudo puppet apply /vagrant/puppet/manifests/default.pp --modulepath=/vagrant/puppet/modules/

```

That's it.

After the installation has finished, you can access the virtual machine with

```sh
    host $ vagrant ssh
    Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)
    ...
    vagrant@rails-dev-box:~$ sqlplus system/manager@//localhost:1521/XE
```

Port 3000 in the host computer is forwarded to port 3000 in the virtual machine. Thus, applications running in the virtual machine can be accessed via localhost:3000 in the host computer. 

## What's In The Box

* Everthing in [rails-dev-box](https://github.com/rails/rails-dev-box)

* Oracle 11g XE

## Acknowledgements

This project is based on [rails-dev-box](https://github.com/rails/rails-dev-box) 
and [vagrant-ubuntu-oracle-xe](https://github.com/hilverd/vagrant-ubuntu-oracle-xe).

Thanks to everyone who contributes these projects.

## Questions

Please email me yasuo.honda@gmail.com

