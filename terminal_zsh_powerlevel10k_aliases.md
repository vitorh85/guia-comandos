# Instalacao do shell ZSH, do Oh-my-zsh! e do Powerlevel10k

## Pre-requsisitos
```sh
sudo apt update -y && sudo apt upgrade -y
sudo apt install build-essential git curl -y
```

## Instalacao do ZSH
```sh
sudo apt install zsh -y
chsh -s /bin/zsh
zsh
```

## Instalacao do Oh-my-zsh!

Fonte: https://ohmyz.sh/
```sh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Instalacao do Powerlevel10k

Fonte: https://github.com/romkatv/powerlevel10k

1. Clone the repository:
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
``` 
2. Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`. 
3. Start a new terminal session and configure the layout:
```
Options:
2 1 4  2 1 1  5 2 2  1 2 2 y 1
``` 

## Instalar Zsh Autosuggestions

Fonte: https://github.com/zsh-users/zsh-autosuggestions

1. Clone this repository into `$ZSH_CUSTOM/plugins` (by default `~/.oh-my-zsh/custom/plugins`)
```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
2. Add the plugin to the list of plugins for Oh My Zsh to load (inside `~/.zshrc`):
```sh
vim ~/.zshrc
# Adiciona configuracao dos plugins
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
3. Start a new terminal session.

## Terminal Aliases

* Adicionar no `~/.bashrc` ou `~/.zshrc`
```sh
alias myip="curl http://ipecho.net/plain"
alias pingg="ping -c 100 -i 0,2 8.8.8.8"
alias dud="du -h --max-depth=1 ."
alias dufolders="du -hd 0 ./* | sort -hr"
alias ll="exa -l --icons -a --group-directories-first"
```

## Setup history between sessions

* Adicionar no `~/.zshrc`
```sh
bindkey  "^[[H"   beginning-of-line
bindkey  "^[[F"   end-of-line
bindkey  "^[[3~"  delete-char

HISTSIZE=100000
HISTFILESIZE=200000
SAVEHIST=100000
HISTFILE=~/.zsh_history
setopt INC_APPEND_HISTORY_TIME
```
