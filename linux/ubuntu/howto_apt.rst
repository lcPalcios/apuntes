.. _reference-linux-ubuntu-howto_apt:

##########
How To Apt
##########

Instalar un paquete

.. code-block:: bash

    apt-get install <paquete>

Desinstalar un paquete

.. code-block:: bash

    apt-get remove <paquete>

Eliminar un paquete incluidos sus ficheros de configuración

.. code-block:: bash

    apt-get purge <paquete>

Eliminar de forma automática aquellos paquetes que no se estén utilizando

.. code-block:: bash

    apt-get autoremove

Actualizar un paquete a la última versión disponible en el repositorio

.. code-block:: bash

    apt-get update <paquete>

Actualizar el sistema. Actualizará todos los paquetes que dispongan de una
versión superior dentro de la rama instalada de la distribución

.. code-block:: bash

    apt-get upgrade

Actualizar la distribución completa. Actualizará nuestro sistema a la siguiente
versión disponible de la distribución

.. code-block:: bash

    apt-get dist-upgrade

Descargar únicamente las fuentes de un paquete para manipularlas de forma manual

.. code-block:: bash

    apt-get source <paquete>

Limpiar cachés, paquetes descargados, etc

.. code-block:: bash

    apt-get clean
    apt-get autoclean

Verificar que no tenemos ninguna dependencia incumplida

.. code-block:: bash

    apt-get check

Buscar un paquete en los repositorios, se puede especificar un patrón, expresión
regular, el nombre exacto del paquete, etc

.. code-block:: bash

    apt-cache search <paquete>

Mostrar información sobre un paquete específico (nombre del paquete, versión, dependencias…)

.. code-block:: bash

    apt-cache showpkg <paquete>

Mostrar información del paquete incluyendo la descripción, información del paquete
como su sitio web, página de bugs…

.. code-block:: bash

    apt-cache show <paquete>

Mostrar dependencias de un paquete

.. code-block:: bash

    apt-cache depends <paquete>

Mostrar los nombres de todos los paquetes instalados en el sistema

.. code-block:: bash

    apt-cache pkgnames
