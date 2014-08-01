.. _reference-git-gitignore_global:

################
Gitignore Global
################

Configuracion que voy poniendo aqui, es general para todos los casos mas comunes.

Crear archivo .gitignore_global

.. code-block:: bash

    vim ~/.gitignore_global

.. code-block:: bash

    # Python
    .idea/
    __pycache__/
    *.pyc

    # Global
    *log*
    .directory
