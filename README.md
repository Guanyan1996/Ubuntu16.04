# Ubuntu16.04 的环境搭建

## 通过root账号，添加新的用户

- useradd –d /usr/name -m name

- passwd name

- sudo usermod -s /bin/bash name 新增客户解决shell问题

- vim /etc/sudoers 调整权限

- sudo userdel -r name 删除客户

## 安装htop

- sudo apt-get update

- sudo apt install htop

## [安装docker-ce(docker-io为老版本）](https://docs.docker.com/v17.09/engine/installation/linux/docker-ce/ubuntu/#upgrade-docker-after-using-the-convenience-script)

> sudo apt-get remove docker docker-engine docker.io

> sudo apt-get update

```bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```
    
> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

> sudo apt-key fingerprint 0EBFCD88

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

> sudo apt-get update

> sudo apt-get install docker-ce

