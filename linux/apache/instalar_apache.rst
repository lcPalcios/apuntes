.. _reference-linux-apache-instalar_apache:

#####################
Instalacion de Apache
#####################

Fedora
******

.. code-block:: bash

    yum -y install httpd

Remove test page

.. code-block:: bash

    rm -f /etc/httpd/conf.d/welcome.conf

.. code-block:: bash

    vim /etc/httpd/conf/httpd.conf

**Opcional**

.. code-block:: bash

    # line 86: Admin's address
    ServerAdmin snicoper@gmail.com

    # line 95: change to your server's name
    ServerName www.workspace.local:80

    # Añadir en la ultima linea
    # server's header
    ServerTokens Prod

    # ServerSignature
    ServerSignature Off

SELinux
=======

Ver :ref:`reference-linux-fedora-centos-reglas_selinux`

.. code-block:: bash

    systemctl start httpd.service
    systemctl enable httpd.service

Firewall
========

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-service=http
    firewall-cmd --permanent --zone=public --add-service=https
    systemctl restart firewalld.service

Ubuntu
******

.. code-block:: bash

    sudo apt-get -y install apache2
