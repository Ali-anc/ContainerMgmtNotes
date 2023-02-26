## The following isntalltion of packages were done on Ubuntu 20.04. However the same can be applied on RHEL like linux distributions via dnf/yum Package Manager, and their respective repo's.


> ### As usual, before installing a package we will make sure that our server is updated

```
apt-get update
apt-get upgrade
```

> ### We install the necessary packages to be able to install Docker:

```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common gnupg-agent
```
> ### Run the commands below to download and install Docker’s official GPG key. The key is used to validate packages installed from Docker’s repository making sure they’re trusted.
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo apt-key fingerprint 0EBFCD88
```
### The response would be like this:
> ### Response:
> ### pub   rsa4096 2017-02-22 [SCEA]
> ###      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
> ### uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
> ### sub   rsa4096 2017-02-22 [S]


### Now that the official GPG key is installed, run the commands below to add its stable repository to Ubuntu. To add the nightly or test repository, add the word nightly or test (or both) after the word stable in the commands below.

```
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

> ### The command below will always install the highest possible version:
 ``` 
 sudo apt-get install docker-ce docker-ce-cli containerd.io
``` 


> ### Create the volume that Portainer Server will use

``` 
docker volume create portainer_data
```

### https://docs.portainer.io/start/install-ce/server/docker/linux

> ### Portainer installation . --privileged  flag is used if you have SELinux enabled.
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --privileged  --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

> ### Add the following ports in Firewalld:

```
firewall-cmd --zone public --add-port={8000/tcp,9443/tcp} --permanent

firewall-cmd --reload
```

> ### Few Useful Commands 

```
list voulmes
docker volume ls
check volume config
docker volume inspect portainer_data
```

> ### SSL Cert
### https://docs.portainer.io/admin/settings#ssl-certificate


> ### Offical docs - Install Portainer with Docker on Linux
### https://docs.portainer.io/start/install/server/docker/linux
