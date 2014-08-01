.. _reference-linux-generar_clave_para_ssh:

######################
Generar clave para SSH
######################

.. code-block:: bash

    ssh-keygen -t rsa

La carpeta ~/.ssh deve tener permisos 700 y los archivos de dentro de ~/.ssh han de ser de 600

.. code-block:: bash

    chmod 700 ~/.ssh
    chmod 600 ~/*
