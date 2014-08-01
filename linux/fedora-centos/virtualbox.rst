.. _reference-linux-fedora-centos-virtualbox:

##########
Virtualbox
##########

Fuentes
*******

* http://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/

---------------

.. code-block:: bash

    # The Oracle public key
    wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | rpm --import -

    # Repo
    cd /etc/yum.repos.d/
    wget http://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo

    # Actualizar
    yum update

    # Instalar
    yum install dkms VirtualBox-4.3

    # Inicializar
    /etc/init.d/vboxdrv setup

    # Dar permisos a usuario
    usermod -a -G vboxusers snicoper
