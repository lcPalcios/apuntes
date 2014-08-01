.. _reference-linux-python-pip_upgrade_all_packages:

####################################
Actualizar todos los paquetes de Pip
####################################

.. code-block:: bash

    pip freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs pip install -U
