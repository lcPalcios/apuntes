.. _reference-programacion-csharp-entityframework-migracion_ef6_basico:

###################
Migraciones con EF6
###################

.. warning::
    Requiere Npgsql 2.2+ para Npgsql

-------------

Inicializar migraciones
***********************

.. code-block:: none

    enable-migrations

.. note::
    Esta parte debo de aprender mas.

Eso crea un archivo ~/Migrations/Configuration.cs donde
podemos poblar datos (Seed)

Crear el primer archivo de migracion
************************************

.. code-block:: none

    add-migration InitialCreate


Update database
***************

.. code-block:: none

    update-database
