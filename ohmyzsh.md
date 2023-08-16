## zsh安装

`sudo apt-get install zsh`

安装完成后使用`cat /etc/shells`查看系统可以使用的shell

使用`chsh -s /bin/zsh`设置zsh为默认shell

## oh-my-zsh安装

使用wget
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
主题修改
```
cd .oh-my-zsh/themes/
vim amuse.zsh-theme
```
修改内容：
```
PROMPT='%(?:%{$fg_bold[green]%}➜ :%{$fg_bold[red]%}➜ )%{$fg_bold[blue]%}%n%u%{$fg_bold[green]%}[%~]%{$reset_color%}$(git_prompt_info)$(virtualenv_prompt_info) %{$fg_bold[yellow]%}%D{%H:%M}%{$reset_color%}$ '
```

激活主题vim ~/.zshrc

修改ZSH_THEME="amuse"



插件加载

1. 自动提示

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

2. 命令语法校验
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
激活插件`vim ~/.zshrc`

```
plugins=( [plugins...] zsh-syntax-highlighting)

```


```
plugins=(
  git
  autojump
  urltools
  bgnotify
  zsh-autosuggestions
  zsh-syntax-highlighting
  zsh-history-enquirer
)
```

要在root用户使用需要在root用户下安装oh-my-zsh在重复上述步骤


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