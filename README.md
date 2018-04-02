unifi-vm
========

This project will help you deploying UniFi controller in a VirtualBox VM.

[Unifi System Requirements](https://help.ubnt.com/hc/en-us/articles/115009221227-UniFi-Recommended-Minimum-System-Requirements)
## Required
 - VirtualBox 4.3 or greater
 - Vagrant 1.6 or greater
 - Ansible 1.7 or greater

## Instructions

Start and provision the vagrant environment:
```sh
cd unifi-vm
vagrant up
```

Vagrant will create a Debian VM and it will provision it with the last UniFi controller stable version.

## Use

Thanks to Vagrant configurations, **8080** and **8443** ports are forwarded to localhost. You can access to web GUI using the address in **your host machine**:

```
http://localhost:8080
```

if for any reason it is not running you can check the status of the unifi service by running:
```
systemctl status inifi
```
