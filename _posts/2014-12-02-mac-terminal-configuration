---
layout: post
title: Minimal terminal configuration for Mac
---
Here is my terminal configuration file `.bash_profile`


    #git auto completions
    if [ -f ~/.git-completion.bash ]; then
      . ~/.git-completion.bash
    fi
    
    #look and feel
    export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
    export CLICOLOR=1
    export LSCOLORS=ExFxBxDxCxegedabagacad
    alias ls='ls -GFh'
    
    #terminal window's title
    PROMPT_COMMAND='echo -ne "\033]0;${PWD/#$HOME/~}"; echo -ne "\007"'

  

References:

1. [http://osxdaily.com/2013/02/05/improve-terminal-appearance-mac-os-x/](http://osxdaily.com/2013/02/05/improve-terminal-appearance-mac-os-x/)
2. [http://blog.friedland.id.au/2010/03/automatically-update-terminal-window.html](http://blog.friedland.id.au/2010/03/automatically-update-terminal-window.html)


