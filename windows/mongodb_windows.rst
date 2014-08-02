.. _reference--windows-mongodb_windows:

##################
MongoDB en Windows
##################

Fuentes
*******

* http://www.mongodb.org/

-----------

Descargar el archivo ``.zip`` para x64 bits

Descomprimir en ``C:\`` y renombrar a ``mongodb``

Añadir al Path:

.. code-block:: bash

    C:\mongodb\bin;


Crear:

.. code-block:: bash

    cd C:\mongodb
    mkdir data
    mkdir log
    touch mongod.cfg

Editar ``mongod.cfg``


.. code-block:: bash

    # mongodb.conf

    # Where to store the data.
    dbpath=C:\mongodb\data

    #where to log
    logpath=C:\mongodb\log\mongod.log

    #append log
    logappend=true

Añadir como servicio

.. code-block:: bash

    C:\mongodb\bin\mongod.exe --auth --config C:\mongodb\mongod.cfg --install


Eliminar servicio

.. code-block:: bash

    C:\mongodb\bin\mongod.exe --auth --config C:\mongodb\mongod.cfg --remove


Iniciar/Parar servicio

.. code-block:: bash

    net start MongoDB
    net stop MongoDB
