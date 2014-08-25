.. _reference-git-configurarion_desde_shell:

###############################################
Configruacion de Git desde la linea de comandos
###############################################

.. note::
    Usar mejor Configuración :ref:`reference-git-gitconfig_linux`, tiene configuraciones que
    aquí no tengo puestas.


Configuración basica
====================

.. code-block:: bash

    git config --global user.name "Salvador Nicolas"
    git config --global user.email "snicoper@gmail.com"
    git config --global color.ui true
    git config --global core.editor vim

Mis Alias
=========

.. code-block:: bash

    git config --global alias.lg "log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr %an)%Creset' --abbrev-commit --date=relative"
    git config --global alias.co "checkout"
    git config --global alias.cm "commit"
    git config --global alias.st status
    git config --global alias.br branch

Global gitignore
================

Con este archivo, todos los repos ignoraran los patrones de este archivo.

.. code-block:: bash

    git config --global core.excludesfile ~/.gitignore_global

Ahora hay que crear el archivo.

.. code-block:: bash

    touch ~/.gitignore_global

Ver :ref:`reference-git-gitignore_global`
