.. _reference-linux-mi_bashrc:

#########
Mi bashrc
#########

Usuario
*******

.. code-block:: bash

    vim ~/.bashrc

.. code-block:: bash

    alias ll="ls -lF"
    alias la="ls -a"
    alias lla="ll -a"
    alias ccat='pygmentize -g' # Requiere python-pygments

    # Git
    function git_branch {
        git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1) /'
    }

    PS1='\[\e[0;32m\]\u@\[\e[m\]\[\e[0;32m\]\h\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\n\[\033[0;32m\]$(git_branch)\[\033[00m\]\$ '

root
****

.. code-block:: bash

    sudo vim /root/.bashrc

.. code-block:: bash

    alias ll="ls -lF"
    alias la="ls -a"
    alias lla="ll -a"
    # alias ccat='pygmentize -g' # Requiere pygmentize

    # Git
    function git_branch {
        git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1) /'
    }

    PS1='\[\e[0;31m\]\u@\[\e[m\]\[\e[0;31m\]\h\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\n\[\033[0;32m\]$(git_branch)\[\033[00m\]\$ '
