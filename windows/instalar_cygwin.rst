.. _reference--windows-instalar_cygwin:

###############
Instalar Cygwin
###############


Fuentes
*******

* http://www.cygwin.com/

-----------

Descargar el instalador e instalar. La primera vez que lo instalo, lo instalo sin
elegir nada, cuando a acabado la primera instalación, lo vuelvo a ejecutar y
selecciono los paquetes a instalar.


.. code-block:: none

    openssh
    wget
    ca-certificates
    curl
    tree

Añadir al path

.. code-block:: none

    C:\cygwin64\bin;

Modificar C:\cygwin64\home\snicoper\.bashrc

.. code-block:: none

    # Añadir al final
    alias ll="ls -lF"
    alias la="ls -a"
    alias lla="ll -a"
    alias ccat='pygmentize -g'

    RED="\033[0;31m"
    GREEN="\033[0;32m"
    ORANGE="\033[1;31m"
    YELLOW="\033[0;33m"
    MAGENTA="\033[0;35m"
    CYAN="\033[0;36m"
    PURPLE="\033[1;35m"

    DARK="\033[1;32m"
    DEFAULT="\033[1;32m"
    MEDIUM="\033[1;33m"
    LIGHT="\033[1;34m"
    WHITE="\033[1;37m"

    RESET="\033[m"

    function git_info() {
        # check if we're in a git repo
        git rev-parse --is-inside-work-tree &>/dev/null || return

        # quickest check for what branch we're on
        local branch=$(git symbolic-ref -q HEAD | sed -e 's|^refs/heads/||')

        # check if it's dirty (via github.com/sindresorhus/pure)
        local dirty=$(git diff --quiet --ignore-submodules HEAD &>/dev/null; [ $? -eq 1 ] && echo -e "*")

        echo -e "${RESET}on ${GREEN}$branch ${RED}$dirty"
    }

    # window title
    PS1='\[\033]0;\W\007\]'

    # prompt title
    PS1="$PS1\n${ORANGE}\u@\h ${RESET}in ${YELLOW}\w \$(git_info) ${RESET}"

    # testing colors
    # PS1="$PS1\n\[\033[0;30m\]0;30m  \[\033[0;31m\]0;31m  \[\033[0;32m\]0;32m  \[\033[0;33m\]0;33m  \[\033[0;34m\]0;34m  \[\033[0;35m\]0;35m  \[\033[0;36m\]0;36m  \[\033[0;37m\]0;37m  \n\[\033[1;30m\]1;30m  \[\033[1;31m\]1;31m  \[\033[1;32m\]1;32m  \[\033[1;33m\]1;33m  \[\033[1;34m\]1;34m  \[\033[1;35m\]1;35m  \[\033[1;36m\]1;36m  \[\033[1;37m\]1;37m  \[$RESET\]default"

    # default interaction prompt
    PS1="$PS1\n\[$LIGHT\]\$ \[$RESET\]"

    # continuation interactive prompt
    PS2="${WHITE}→ ${RESET}"
