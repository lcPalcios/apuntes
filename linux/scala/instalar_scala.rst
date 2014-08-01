.. _reference-linux-scala-instalar_scala:

##############
Instalar Scala
##############

Fuentes:
********

* http://www.scala-lang.org/

-------------------

.. warning::
    Sustituir 2.11.1 por la version descargada

Descomprimir y mover a opt

.. code-block:: bash

    sudo mv scala-2.11.1 /opt/scala-2.11.1

Añadir al path

.. code-block:: bash

    vim ~/.bashrc

.. code-block:: bash

    PATH="$PATH:/opt/scala-2.11.1/bin"
