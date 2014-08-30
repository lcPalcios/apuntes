.. _reference-linux-ubuntu-crear_certificado_ssl:

#####################
Crear certificado SSL
#####################

Pongo el nombre de lxmaq1 para el servidor principal, cambiar si es otro servidor

.. code-block:: bash

    sudo -s

    cd /etc/ssl/private

.. code-block:: bash

    openssl genrsa -des3 -out lxmaq1.key 2048

.. code-block:: bash

    openssl req -new -days 3650 -key lxmaq1.key -out lxmaq1.csr

.. code-block:: bash

    Country Name (2 letter code) [XX]:es
    State or Province Name (full name) []:Spain
    Locality Name (eg, city) [Default City]:Barcelona
    Organization Name (eg, company) [Default Company Ltd]:snicoper
    Organizational Unit Name (eg, section) []:nombre_org
    Common Name (eg, your name or your server's hostname) []:lxmaq1.workspace.local
    Email Address []:snicoper@gmail.com

    A challenge password []: (Intro)
    An optional company name []: (Intro)

.. code-block:: bash

    openssl x509 -in lxmaq1.csr -out lxmaq1.crt -req -signkey lxmaq1.key -days 3650

.. code-block:: bash

    chmod 400 lxmaq1.*
