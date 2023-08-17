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



