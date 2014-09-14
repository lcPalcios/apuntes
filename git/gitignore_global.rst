.. _reference-git-gitignore_global:

################
Gitignore Global
################

Configuración que voy poniendo aquí, es general para todos los casos mas comunes.

Crear archivo .gitignore_global

.. code-block:: bash

    vim ~/.gitignore_global

.. code-block:: bash

    # File types #
    ##############
    *.pyc
    *.swo
    *.swp
    *.swn

    # Directories #
    ###############
    __pycache__/
    .idea/
    build/
    logs/

    # Specific files #
    ##################

    # OS generated files #
    ######################
    .directory
    .DS_Store?
    ehthumbs.db
    Icon?
    Thumbs.db
    *~
