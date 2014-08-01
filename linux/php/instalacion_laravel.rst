.. _reference-linux-php-instalacion_laravel:

###################
Instalacion Laravel
###################

Fuentes
*******

* http://laravel.com/docs/quick#installation

Archivo Phar
************

Fedora
======

.. code-block:: bash

    yum install -y php-curl

Centos, si se ha instalado php 5.5
==================================

.. code-block:: bash

    yum install --enablerepo=remi,remi-php55 php-curl

Ubuntu
======

.. code-block:: bash

    apt-get install php5-curl

Todos
=====

Como root

.. code-block:: bash

    wget http://laravel.com/laravel.phar
    chmod +x laravel.phar
    mv laravel.phar /usr/local/bin/laravel
    laravel --version

Con Composer
************

:ref:`reference-linux-php-composer`

.. code-block:: bash

    composer create-project laravel/laravel your-project-name --prefer-dist
