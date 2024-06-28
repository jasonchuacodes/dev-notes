#### Installation guide
Read more [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)

#### Custom zshrc

This is to customize the terminal to have color themes, directory info, branch info, node version, and terminal aliases/shortcuts.
```
# Colors
autoload -Uz colors
colors
export TERM="xterm-256color"

autoload -Uz vcs_info
precmd() { vcs_info }


# History 
HISTFILE=~/.zsh_history
HISTSIZE=10000
SAVEHIST=10000
setopt INC_APPEND_HISTORY_TIME

# Alias
alias ..="cd .."
alias ...="cd ../.."
alias ls="ls --color=auto"
alias l="ls -lah --color=auto"
alias pip=pip3
alias python=python3

# Git alias
alias gst="git status"
alias ga="git add"
alias gl="git pull"
alias gp="git push"
alias gcam="git commit -am"
alias gcmsg="git commit -m"
alias gco="git checkout"
alias ggpush="git push"
alias gaa="git add ."
alias gsta="git stash"
alias cc="clear"

# Prompt
autoload -Uz promptinit
promptinit

# Format the vcs_info_msg_0_ variable for git branch
autoload -Uz vcs_info
precmd() { vcs_info }
zstyle ':vcs_info:git:*' formats '%b'

# Custom Prompt
setopt prompt_subst
PROMPT_CHAR=$'\n%(!.#.$) '
CWD=$'%F{cyan}%(4~|%1~|%~)%f'

# PS1='$CWD %F{red}${vcs_info_msg_0_}%f $(aws_profile)$PROMPT_CHAR'
PS1='$CWD %F{red}${vcs_info_msg_0_}%f $(aws_profile)$(node_version)$PROMPT_CHAR'

# Date date and time Format
RPROMPT='[ %B%F{cyan}%D{%I:%M:%S %p}%b%f ]'

# AWS Profile Prompt
function aws_profile {
  if [[ $AWS_PROFILE ]]; then
    echo "%F{yellow}AWS: $AWS_PROFILE%f "
  fi
}

# Node version
function node_version {
  PACKAGE_JSON=./package.json
  if [[ -f "$PACKAGE_JSON" ]]; then
	NODE=$(which node)
	NODE_VER=$($NODE --version)
	echo "%F{green}NODEJS: ${NODE_VER}%f "
  fi
}

# Node Version Manager
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# load nvmrc
autoload -U add-zsh-hook
load-nvmrc() {
  local node_version="$(nvm version)"
  local nvmrc_path="$(nvm_find_nvmrc)"

  if [ -n "$nvmrc_path" ]; then
    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")

    if [ "$nvmrc_node_version" = "N/A" ]; then
      nvm install
    elif [ "$nvmrc_node_version" != "$node_version" ]; then
      nvm use
    fi
  elif [ "$node_version" != "$(nvm version default)" ]; then
    echo "Reverting to nvm default version"
    nvm use default
  fi
}
add-zsh-hook chpwd load-nvmrc
load-nvmrc

export PATH=$HOME/.local/bin:$PATH

# Zsh Auto Suggestions
. ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh

```