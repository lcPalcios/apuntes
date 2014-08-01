.. _reference-editors-netbeans-lf_windows:

##########
LF Windows
##########

Poner final de linea LF en Netbeans
***********************************

Editar como administrador

.. code-block:: bash

    C:\Program Files\NetBeans 7.3\etc\netbeans.conf

Buscar netbeans_default_options= y añadir

.. code-block:: bash

    -J-Dline.separator=LF -J-Dfile.encoding=UTF-8
