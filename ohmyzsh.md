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

设置终端代理

```
export HOSTIP=$(cat /etc/resolv.conf | grep "nameserver" | cut -f 2 -d " ")
export https_proxy=http://$HOSTIP:7890;export http_proxy=http://$HOSTIP:7890;export all_proxy=socks5://$HOSTIP:7890
```

## zsh安装

`sudo apt-get install zsh`

安装完成后使用`cat /etc/shells`查看系统可以使用的shell

使用`chsh -s /bin/zsh`设置zsh为默认shell

## oh-my-zsh安装

使用wget,为root安装需要使用sudo
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
## 主题修改
```
cd .oh-my-zsh/themes/
vim amuse.zsh-theme
```
修改内容：

```
# vim:ft=zsh ts=2 sw=2 sts=2

# Must use Powerline font, for \uE0A0 to render.
ZSH_THEME_GIT_PROMPT_PREFIX=" on %{$fg[magenta]%}\uE0A0 "
ZSH_THEME_GIT_PROMPT_SUFFIX=" %{$reset_color%}"
ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[red]%}!"
ZSH_THEME_GIT_PROMPT_UNTRACKED="%{$fg[green]%}?"
ZSH_THEME_GIT_PROMPT_CLEAN=""

ZSH_THEME_RUBY_PROMPT_PREFIX="%{$fg_bold[red]%}‹"
ZSH_THEME_RUBY_PROMPT_SUFFIX="›%{$reset_color%}"

PROMPT='%(?:%{$fg_bold[green]%}➜ :%{$fg_bold[red]%}➜ )%{$fg_bold[blue]%}%n%u%{$fg_bold[green]%}[%~]%{$reset_color%}$(git_prompt_info)$(virtualenv_prompt_info)%{$fg_bold[yellow]%} %D{%H:%M}%{$reset_color%} %(?:%{$fg_bold[green]%}➜ :%{$fg_bold[red]%}➜ )'

RPROMPT='$(ruby_prompt_info)'

VIRTUAL_ENV_DISABLE_PROMPT=0
ZSH_THEME_VIRTUAL_ENV_PROMPT_PREFIX=" %{$fg[green]%}🐍"
ZSH_THEME_VIRTUAL_ENV_PROMPT_SUFFIX="%{$reset_color%}"
ZSH_THEME_VIRTUALENV_PREFIX=$ZSH_THEME_VIRTUAL_ENV_PROMPT_PREFIX
ZSH_THEME_VIRTUALENV_SUFFIX=$ZSH_THEME_VIRTUAL_ENV_PROMPT_SUFFIX
```

激活主题vim ~/.zshrc

修改ZSH_THEME="amuse"

## brew安装

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

之后修改.zshrc
```
export BREW_HOME="/home/linuxbrew/.linuxbrew/bin"
export PATH="$PATH:$BREW_HOME"
```


## 插件加载

### 1. 自动提示

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

激活插件`vim ~/.zshrc`
```
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```

### 2. 命令语法校验
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
激活插件`vim ~/.zshrc`


### 3. zsh-completions：额外补全

二选一
```
##下载安装
git clone --depth=1 https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions

##添加目录
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src

##激活
source "$ZSH/oh-my-zsh.sh"

##brew下载安装
brew install zsh-completions
```
使用brew安装后

```
if type brew &>/dev/null; then
  FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

  autoload -Uz compinit
  compinit
fi
```


### thefuck安装

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
```
plugins=(
  git
  zsh-completions
  urltools
  bgnotify
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```
### Incremental completion on zsh:实时补全

```
##创建文件夹
mkdir $ZSH_CUSTOM/plugins/incr

##下载
curl -fsSL https://mimosa-pudica.net/src/incr-0.2.zsh -o $ZSH_CUSTOM/plugins/incr/incr.zsh

##配置
echo 'source $ZSH_CUSTOM/plugins/incr/incr.zsh' >> ~/.zshrc

##激活
source ~/.zshrc
```
