.. _reference-git-gitconfig_linux:

###################
Git Config Linux
###################

Configuracion con Kdiff3
************************

.. code-block:: bash

    [user]
        name = Salvador Nicolas
        email = snicoper@gmail.com
    [color]
        ui = true
    [core]
        editor = vim
        excludesfile = /home/snicoper/.gitignore_global
    [alias]
        lg = log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr %an)%Creset' --abbrev-commit --date=relative
        co = checkout
        cm = commit
        st = status
        br = branch
    [merge]
        tool = kdiff3
    [diff]
        tool = kdiff3
    [mergetool]
        keepBackup = false
        trustExitCode = false

Configuración con Meld
**********************

.. code-block:: bash

    [user]
        name = Salvador Nicolas
        email = snicoper@gmail.com
    [color]
        ui = true
    [core]
        editor = vim
        excludesfile = /home/snicoper/.gitignore_global
    [alias]
        lg = log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr %an)%Creset' --abbrev-commit --date=relative
        co = checkout
        cm = commit
        st = status
        br = branch
    [merge]
        tool = meld
    [diff]
        tool = meld
    [mergetool]
        keepBackup = false
        trustExitCode = false

Arhora hay que crear el archivo

.. code-block:: bash

    touch ~/.gitignore_global

Ver :ref:`reference-git-gitignore_global`
