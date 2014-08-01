.. _reference-programacion-postgresql-comandos_consola_psql:

#########################
Comandos consola Postgres
#########################

.. note::
    Cuando usa ``$``, significa que esta en el shell, cuando no tiene nada
    es que esta en psql

Login usuario postgres

.. code-block:: bash

    $ sudo su - postgres

Creacion de un usuario

.. code-block:: bash

    create user nombre_usuario with password '123456'

Eliminar usuario

.. code-block:: bash

    drop user nombre_usuario


Crear base de datos

.. code-block:: bash

    create database nombre_db with owner nombre_usuario;

Eliminar base de datos

.. code-block:: bash

    drop database nombre_db

Acceder database con usuario x

.. code-block:: bash

    psql -U nombre_usuario nombre_db

Obtener ayuda

.. code-block:: bash

    \h

Quit

.. code-block:: bash

    \q

Leer comandos desde un archivo

.. code-block:: bash

    \i input.sql

Dump db a un archivo

.. code-block:: bash

    $ pg_dump -U nombre_usuario nombre_db > db.out

Dump todas las bases de datos

.. code-block:: bash

    $ sudo su - postgres
    $ pg_dumpall > /var/lib/pgsql/backups/dumpall.sql

Restaurar db

.. code-block:: bash

    $ sudo su - postgres
    $ psql -f /var/lib/pgsql/backups/dumpall.sql mydb

SHOW DATABASES

.. code-block:: bash

    \l

SHOW TABLES

.. code-block:: bash

    \d

SHOW COLUMNS

.. code-block:: bash

    \d table_name

DESCRIBE TABLE

.. code-block:: bash

    \d+ table_name

USE DATABASE_NAME

.. code-block:: bash

    \c nombre_db

Show users

.. code-block:: bash

    select * from "pg_user";
