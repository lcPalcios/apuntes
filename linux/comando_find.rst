.. _reference-linux-comando_find:

############
Comando find
############

.. code-block:: bash

    find ./ -name '*.php' -type f -exec chmod 777 {} \;

Con esto busca en el arbol ./ los archivos que contienen .php tipo file y
ejecuta chmod 777 a todos los archivos, omitir -name '\*.php' para que sean todos
los archivos

Eliminar recursivamente carpetas con X nombre

.. code-block:: bash

    rm -rf `find ./ -type d -name .svn`
