.. _reference-linux-php-memcached:

#########
Memcached
#########

Fedora
******

.. code-block:: bash

    yum -y install memcached php-pecl-memcached

    systemctl enable memcached.service
    systemctl start memcached.service

Para editar la configuracion

.. code-block:: bash

    vim /etc/sysconfig/memcached

Ubuntu
******

.. code-block:: bash

    sudo apt-get install memcached php5-memcached

Para editar la configuracion

.. code-block:: bash

    sudo vim /etc/memcached.conf
