.. _reference-mono-monodevelop-mono_monodevelop_repos:

###########################
Repos de Mono y Monodevelop
###########################

.. note::
    Para Ubuntu, si se quiere tener los ultmos mono y monodevelop,
    ver los PPAs

Fuentes
*******

* http://software.opensuse.org/download/package?project=home:tpokorra:mono&package=mono-opt
* https://launchpad.net/~ermshiperete/+archive/ubuntu/monodevelop

----------------------


Instalar Mono Monodevelop y XSP desde los repos de OpenSUSE
***********************************************************

Ubuntu
======

.. code-block:: bash

    wget http://download.opensuse.org/repositories/home:tpokorra:mono/xUbuntu_14.04/Release.key
    sudo apt-key add - < Release.key
    rm -f  Release.key
    sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/tpokorra:/mono/xUbuntu_14.04/ /' >> /etc/apt/sources.list.d/monodevelop-opt.list"

    sudo apt-get update
    sudo apt-get install mono-opt monodevelop-opt mono-xsp-opt -y

Fedora
======

.. code-block:: bash

    cd /etc/yum.repos.d/
    wget http://download.opensuse.org/repositories/home:tpokorra:mono/Fedora_20/home:tpokorra:mono.repo
    yum install mono-opt monodevelop-opt mono-xsp-opt

Fedora Ubuntu
=============

Editar ~/.bashrc

.. code-block:: bash

    PATH="$PATH:/opt/mono/bin"
    export PATH

.. code-block:: bash

    sudo mkdir /opt/mono/etc/mono/registry
    sudo mkdir /opt/mono/etc/mono/registry/LocalMachine
    sudo chmod g+rwx /opt/mono/etc/mono/registry
    sudo chmod g+rwx /opt/mono/etc/mono/registry/LocalMachine

Ubuntu ultimo Mono and MonoDevelop PPA
**************************************

.. code-block:: bash

    sudo apt-add-repository ppa:ermshiperete/monodevelop
    sudo apt-get install monodevelop mono-xsp4

    sudo mkdir -p /etc/mono/registry/LocalMachine
    sudo chmod g+rwx /etc/mono/registry
    sudo chmod g+rwx /etc/mono/registry/LocalMachine