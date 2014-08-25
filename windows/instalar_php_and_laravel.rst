.. _reference--windows-instalar_php_and_laravel:

######################
Instalar PHP y Laravel
######################

Instalación de PHP y Laravel, para una instalación mas completa, apache o nginx
instalar `xampp <https://www.apachefriends.org/es/index.html>`_ o
`wpn-xm <http://wpn-xm.org/>`_

Descargar la version `VC11 x86 Non Thread Safe <http://windows.php.net/download/>`_

Crear una carpeta en ``C:\php`` y descomprimir dentro los archivos del ``.zip`` siendo
esta la raiz de todos los archivos.

Añadir al path
**************

Ir a propiedades de ``Mi Pc > Advanced system settings > Environment Variables...``
En el cuadro de abajo, ``System variables``, buscar el Path y añadir al final

.. code-block:: bash

    ;C:\php;

Editar php.ini
**************

Entrar en ``C:\php``, Ctrl+C, Ctrl+V en ``php.ini-development`` y renombrar a ``php.ini``

Abrirlo y editar

.. code-block:: bash

    # Linea 721
    extension_dir = "C:/php/ext"

    # A partir de la linea 863 mas o menos, descomentar
    extension=php_bz2.dll
    extension=php_curl.dll
    extension=php_fileinfo.dll
    extension=php_gd2.dll
    extension=php_gettext.dll
    extension=php_mbstring.dll
    extension=php_openssl.dll
    extension=php_pdo_pgsql.dll
    extension=php_pdo_sqlite.dll
    extension=php_pgsql.dll
    extension=php_soap.dll
    extension=php_sockets.dll
    extension=php_sqlite3.dll
    extension=php_xsl.dll

    #Linea 913
    date.timezone = Europe/Madrid

.. note::
    Por ejemplo ``php_pgsql.dll`` hay que tener instalado
    :ref:`reference--windows-instalacion_postgresql_win`

    Para ``date.timezone`` ver
    `Listado de zonas horarias soportadas <http://php.net/manual/es/timezones.php>`_

XDebug
******

Abrir CMD y escribir

.. code-block:: bash

    php -i > phpini.txt

Abrir el ``phpini.txt`` copiar todo el texto y pegarlo en
http://xdebug.org/wizard.php

Descargar y renombrar a ``php_xdebug.dll`` en ``C:\php\ext``

Añadir al final del ``php.ini``

.. code-block:: bash

    zend_extension = C:\php\ext\php_xdebug.dll

Composer
********

Abrir CMD

.. code-block:: bash

    cd C:\php
    php -r "readfile('https://getcomposer.org/installer');" | php
    echo @php "%~dp0composer.phar" %*>composer.bat
    composer -V
