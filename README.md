# Ubuntu16.04 的环境搭建

## 通过root账号，添加新的用户

- useradd –d /usr/name -m name

- passwd name

- sudo usermod -s /bin/bash name 新增客户解决shell问题

- vim /etc/sudoers 调整权限

- sudo userdel -r name 删除客户

## 免密登陆

- ssh-keygen 生成密钥

- ssh-copy-id -i .ssh/id_rsa.pub target_server

## 设置别名

- 在~/.ssh目录下创建并编辑config文件

　　vim config(centos)

　　vim config(ubuntu)

- config文件内容

```

Host   主机名

    HostName   ip地址

    User   用户名

Port   端口号
```


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

## Z Shell

- 安装方法

  ```shell
  # Ubuntu
  sudo apt install zsh
  echo $SHELL
  sudo chsh -s /bin/zsh
  
  if [ "$SHELL" != "/bin/zsh" ]
  then
     export SHELL="/bin/zsh"
     exec /bin/zsh -l    # -l: login shell again
  fi


  # Mac
  brew install zsh
  # https://stackoverflow.com/questions/31034870/making-zsh-default-shell-in-macosx
  # System Preferences -> Users & Groups -> Unlock -> Right click the current user -> Advanced options -> Change the login shell to /bin/zsh
  ```

## Oh-my-zsh

- 安装方法 https://ohmyz.sh/

  ```shell
  sudo sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```

- 在 .zshrc 中添加下面配置

  ```shell
  # prevent ctr-d from exiting the shell
  set -o ignoreeof

  # fzf config
  export FZF_DEFAULT_COMMAND="fd --exclude={.git,.idea,.vscode,.sass-cache,node_modules,build} --type f"
  export FZF_DEFAULT_OPTS="--height 40% --layout=reverse --preview '(highlight -O ansi {} || cat {}) 2> /dev/null | head -500'"
  ```

> raw.githubusercontent.com:443 :connected refused问题解决

```
解决方法
在Wget后面添加"–no-check-certificate"如下所示:
wget --no-check-certificate 你要下载的SSL网址

第二种解决办法就是
安装ca-certificates
apt-get install ca-certificates -y
或者是
apt-get install ssl-cert
```
