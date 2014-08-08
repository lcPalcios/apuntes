.. _reference-programacion-python-django-migraciones_django:

##########################
Migraciones en Django 1.7+
##########################

Crear migraciones
*****************

.. code-block:: bash

    python manage.py makemigrations polls

Mediante la ejecución de makemigrations, le estás diciendo a Django que
has hecho algunos cambios a sus modelos y que desea que los cambios se
almacenarán como la migración.

Las migraciones son cómo almacena Django cambios a sus modelos (y por tanto
el esquema de base de datos) - son simplemente los archivos en el disco.
Puedes leer la migración para su nuevo modelo si se quiere; que es el
archivo polls/migrations/0001_initial.py . No te preocupes, no se espera para
leerlos cada vez que Django hace uno, sino que están diseñados para ser
humano editable en caso de que quiera ajustar manualmente cómo Django cambia
las cosas.

Ver SQL que generara
********************

Para ver el SQL que generara cuando cree la db, usar sqlmigrate.

Por ejemplo para ver ``0001_initial.py 0002_auto_20140808_1242.py``, solo poner
el premer numero ``0001`` o ``0002``

.. note::
    Esto no genera la base de datos, solo muestra el ``SQL`` que generara cuando
    se haga ``migrate``

.. code-block:: bash

    python manage.py sqlmigrate polls 0001

Comprobar el modelo
*******************

Esto solo comprueba si hay algun error en el modelo, pero no ejecuta nada.

.. code-block:: bash

    python manage.py check


Migrar las base de datos
************************

.. code-block:: bash

    python manage.py migrate

El comando migrate toma todas las migraciones que no han sido aplicadas
(pistas de Django cuáles se aplican mediante una tabla especial en su base
de datos llamada django_migrations ) y les va en contra de su base de
datos - en esencia, la sincronización de los cambios realizados en sus
modelos con el esquema en la base de datos.

Las migraciones son muy potentes y permiten cambiar tus modelos con el
tiempo, a medida que desarrolle su proyecto, sin la necesidad de eliminar
la base de datos o las tablas y hacer otros nuevos - que se especializa
en la actualización de su base de datos en vivo, sin perder datos.
Recordamos la guía de tres pasos para hacer cambios en el modelo:

* Cambiar los modelos (en models.py ).
* Ejecutar python manage.py makemigrations para crear migraciones de esos cambios
* Ejecutar python manage.py migrate para aplicar esos cambios a la base de datos.
