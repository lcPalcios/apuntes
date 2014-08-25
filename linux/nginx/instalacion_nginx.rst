.. _reference-linux-nginx-instalacion_nginx:

#################
Instalacion Nginx
#################

Ubuntu
******

Instalacion

.. code-block:: bash

    sudo apt install nginx
    sudo service nginx start

Si se quiere permitir que puedan verse las paginas desde fuera del localhost
añadir regla en ufw

.. code-block:: bash

    sudo ufw allow 80


Fedora
******

Instalacion

.. code-block:: bash

    yum install nginx

Centos
******

    En la wiki dice lo siguiente:

.. code-block:: bash

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=0
    enabled=1

Pero a mi no me funciono por el $releasever, en cambio, poniendo "7", en ves de $releasever
me funciono sin problemas.

.. code-block:: bash

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/7/$basearch/
    gpgcheck=0
    enabled=1

.. warning::
    Probar la próxima vez como dice el Wiki, cuando lo probé
    Centos acababa de salir.

Fedora y Centos
===============

.. code-block:: bash

    systemctl start nginx.service
    systemctl enable nginx.service

Firewall

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-service=http
    firewall-cmd --permanent --zone=public --add-service=https
    systemctl restart firewalld.service
