.. _reference-linux-fedora-centos-crear_ssl:

#########
Crear SSL
#########

.. note::
    | Probado para postfix, httpd usa otro.
    | Mirar de configurar para que use el mismo, si es posible.

.. code-block:: bash

    cd /etc/pki/tls/certs
    make workspace.key

Introducir passphrase

.. code-block:: bash

    umask 77 ; \
    /usr/bin/openssl genrsa -aes128 2048 > workspace.key

    openssl rsa -in workspace.key -out workspace.key
    make workspace.csr

Los datos que le pongo (Son para servidor de pruebas!)

.. code-block:: bash

    Country Name (2 letter code) [XX]:es
    State or Province Name (full name) []:Spain
    Locality Name (eg, city) [Default City]:Barcelona
    Organization Name (eg, company) [Default Company Ltd]:snicoper
    Organizational Unit Name (eg, section) []:Web service
    Common Name (eg, your name or your server's hostname) []:ns1
    Email Address []:snicoper@gmail.com

    Please enter the following 'extra' attributes
    to be sent with your certificate request
    A challenge password []:(vacio)
    An optional company name []: (vacio)

.. code-block:: bash

    openssl x509 -in workspace.csr -out workspace.crt -req -signkey workspace.key -days 3650
    chmod 400 workspace.*
