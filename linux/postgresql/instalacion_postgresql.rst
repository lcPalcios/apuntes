.. _reference-linux-postgresql-instalacion_postgresql:

#########################
Instalación de PostgreSQL
#########################

Fuentes
*******

* https://help.ubuntu.com/community/PostgreSQL

Ubuntu
******

Instalación

.. code-block:: bash

    sudo apt-get install -y postgresql postgresql-client postgresql-contrib

    # Opcional
    sudo apt-get install -y pgAdmin3

Si se quiere instalar psycopg2 con Python pip

.. code-block:: bash

    sudo apt-get -y install libpq-dev

Establecer contraseña del usuario postgres

.. code-block:: bash

    sudo -u postgres psql postgres
    \password postgres

Crear usuario snicoper y database practicas

.. code-block:: sql

    CREATE user snicoper WITH PASSWORD '123456' NOCREATEDB NOCREATEUSER;
    CREATE DATABASE practicas WITH OWNER snicoper;
    \q

Configuración PostgreSQL

.. code-block:: bash

    sudo vim /etc/postgresql/9.3/main/postgresql.conf

.. code-block:: bash

    # Descomentar, linea 59
    listen_addresses = 'localhost'

    # Descomentar, linea 89
    password_encryption = on

.. code-block:: bash

    sudo service postgresql restart

Fedora y Centos
***************

.. warning::
    En Centos 7 no lo he probado, pero debe ser la misma que en Fedora 19, 20

Instalación

.. code-block:: bash

    yum install -y postgresql postgresql-server

    # Opcional
    yum install -y pgadmin3

Si se quiere instalar psycopg2 con python pip

.. code-block:: bash

    yum install -y postgresql-devel

.. code-block:: bash

    postgresql-setup initdb
    systemctl enable postgresql.service
    systemctl start postgresql.service

Establecer contraseña de postgres

.. code-block:: bash

    su postgres
    psql

    CREATE USER snicoper WITH PASSWORD '123456' NOCREATEDB NOCREATEUSER;
    CREATE DATABASE practicas WITH OWNER snicoper;
    \q
    exit

Configuración

.. code-block:: bash

    vim /var/lib/pgsql/data/postgresql.conf

.. code-block:: bash

    # linea 59
    listen_addresses = 'localhost'

    # linea 63 descomentar
    port = 5432

.. code-block:: bash

    vim  /var/lib/pgsql/data/pg_hba.conf

Remplazar toda la parte siguiente al final del archivo

.. code-block:: bash

    # TYPE  DATABASE        USER            ADDRESS                 METHOD

    # "local" is for Unix domain socket connections only
    local   all         all                               md5
    # IPv4 local connections:
    host    all         all         127.0.0.1/32          md5
    # IPv6 local connections:
    host    all         all         ::1/128               md5

.. code-block:: bash

    systemctl restart postgresql.service

Ver :ref:`reference-linux-fedora-centos-reglas_selinux`

