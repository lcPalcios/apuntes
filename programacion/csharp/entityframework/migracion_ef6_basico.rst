.. _reference-programacion-csharp-entityframework-migracion_ef6_basico:

###################
Migraciones con EF6
###################

.. warning::
    Por hacer y mejorar.

.. warning::
    Solo funciona con Sql Server

    Aunque para postgres he leido algo, en alguna parte, lo vi
    algo lioso.

.. note::
    Todos los comandos es en Package Manager Console

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
