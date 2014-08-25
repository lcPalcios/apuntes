.. _reference-git-git_windows:

##############
Git en Windows
##############

Instalar `Git <http://git-scm.com>`_ y `Tortoise git <http://code.google.com/p/tortoisegit/>`_

Añadir al path

.. code-block:: bash

    C:\Program Files (x86)\Git\bin;C:\Program Files (x86)\Git\cmd;


.. note::
    Las configuración con Cygwin y kdiff3 no me han funcionado, usar
    el instalador de Windows.

Gitconfig con kdiff3
====================

.. code-block:: bash

    [user]
        name = Salvador Nicolas
        email = snicoper@gmail.com
    [color]
        ui = true
    [core]
        editor = 'C:/Program Files/Sublime Text 3/sublime_text.exe' -w
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
    [mergetool "kdiff3"]
        path = C:/Program Files/KDiff3/kdiff3.exe
        keepBackup = false
        trustExitCode = false
