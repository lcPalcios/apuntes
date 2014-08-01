.. _reference-linux-php-instalacion_php:

###############
Instalacion PHP
###############

Ubuntu
******

Apache y Nginx
==============

.. code-block:: bash

    sudo apt-get install -y php5 php5-cli php5-gd php5-xsl php5-json php5-mcrypt

.. note::
    Si se instala Nginx, desactivar uno de los dos, ver carpeta de
    ubuntu para desactivar servicios.

.. important::
    Crear enlace cuando este creado el archivo de ubuntu para desactivar
    servicios.

Apache
======

.. code-block:: bash

    sudo apt-get install libapache2-mod-php5


Nginx
=====

.. code-block:: bash

    sudo apt-get install php5-fpm
    sudo php5enmod mcrypt

PHP.ini
=======

Apache
^^^^^^

.. code-block:: bash

    sudo cp /usr/share/php5/php.ini-development /etc/php5/apache2/php.ini
    sudo vim /etc/php5/apache2/php.ini

Nginx
^^^^^

.. code-block:: bash

    sudo cp /usr/share/php5/php.ini-development /etc/php5/fpm/php.ini
    sudo vim /etc/php5/fpm/php.ini

Nginx y Apache
^^^^^^^^^^^^^^

.. note::
    Se puede omitir, es el cli

.. code-block:: bash

    sudo cp /usr/share/php5/php.ini-production.cli /etc/php5/cli/php.ini
    sudo vim /etc/php5/cli/php.ini

Modificar php.ini y cli/php.ini

* expose_php = Off
* short_open_tag Off
* timezone Europe/Madrid

Configuracion php-opcache
=========================

En la linea 1877 mas o menos:

.. code-block:: bash

    opcache.enable=1
    opcache.enable_cli=1
    opcache.memory_consumption=128
    opcache.interned_strings_buffer=8
    opcache.max_accelerated_files=4000
    opcache.revalidate_freq=60
    opcache.fast_shutdown=1

Apache
======

.. code-block:: bash

    sudo service apache2 restart

Nginx
=====

.. code-block:: bash

    sudo service nginx restart
    sudo service php5-fpm restart

Fedora Centos
*************

.. note::
    Para php 5.5 en centos usar: yum --enablerepo=remi,remi-php55, yo
    lo omito por que todo lo demas es igual en fedora que en centos.

.. code-block:: bash

    yum install -y php php-gd php-pdo php-xml php-mcrypt php-cli php-soap php-opcache

Para ver lista de paquetes php-*

.. code-block:: bash

    yum search php-

Fedora
======

.. code-block:: bash

    cp /usr/share/doc/php-common/php.ini-development /etc/php.ini

Centos
======

.. code-block:: bash

    cp /usr/share/doc/php-common-5.5.14/php.ini-development /etc/php.ini

Fedora y Centos
===============

.. code-block:: bash

    yum install php-fpm -y

    systemctl start php-fpm.service
    systemctl enable php-fpm.service

PHP.ini
=======

.. code-block:: bash

    vim /etc/php.ini

Buscar y editar

* timezone Europe/Madrid
* php_expose = off
* short_open_tags = off

Configuracion de php-opcache
============================

En la linea 1872 (fedora) 1836 (centos), debajo de [opcache], añadir

.. code-block:: bash

    opcache.enable=1
    opcache.enable_cli=1
    opcache.memory_consumption=128
    opcache.interned_strings_buffer=8
    opcache.max_accelerated_files=4000
    opcache.revalidate_freq=60
    opcache.fast_shutdown=1
