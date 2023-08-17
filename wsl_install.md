## 安装wsl

使用`wsl --list --online`来查看能安装哪些发行版

如果出现`无法解析服务器的名称或地址`，需要在控制面版-网络和internet-更改连接网络属性中的（TCP/IPv4）

使用下面的DNS地址服务器

首选DNS服务器`114.114.114.114`
备用DNS服务器`8.8.8.8`

使用`wsl --install -d Ubuntu-22.04`安装Ubuntu

设置root用户密码

`sudo passwd root`

定期更新和升级apt-get

```
sudo apt update && sudo apt upgrade
```

brew安装

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

之后修改.zshrc
```
export BREW_HOME="/home/linuxbrew/.linuxbrew/bin"
export PATH="$PATH:$BREW_HOME"
```




thefuck安装

```
sudo apt update
sudo apt install python3-dev python3-pip python3-setuptools
pip3 install thefuck --user
```
需要将python加入PATH，修改.zshrc
```
export PATH="$PATH:/usr/bin/python3"

export PATH="$PATH:~/.local/bin/"
eval $(thefuck --alias fuck)
```

