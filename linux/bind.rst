.. _reference-linux-bind:

####
Bind
####

Fuentes
*******

* http://blog.ca.edu.ni/cleal/2012/11/28/servidor-dns-en-ubuntu-12-04/
* http://www.belinuxmyfriend.com/2007/07/ip-estatica-en-ubuntu-manualmente.html
* http://www.server-world.info/en/note?os=Ubuntu_13.04&p=dns&f=1
* http://lani78.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/
* http://docs.fedoraproject.org/en-US/Fedora/20/html/Networking_Guide/index.html

Instalacion
***********

Ubuntu
======

.. code-block:: bash

    sudo apt-get install bind9 bind9utils

Fedora
======

.. code-block:: bash

    yum install bind bind-utils bind-chroot
    systemctl enable named-chroot
    systemctl start named-chroot

Configuración Red
*****************

Ubuntu
======

.. code-block:: bash

    sudo vim /etc/network/interfaces

.. code-block:: bash

    auto eth0
    iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1
        network 192.168.1.0
        broadcast 192.168.1.255
        dns-nameservers 127.0.0.1 8.8.4.4 8.8.8.8
        dns-search ns1.workspace.local
        dns-domain workspace.local


Fedora
======

:ref:`reference-linux-fedora-centos-configurar_red`

Configuracion Bind
******************

Ubuntu
======

.. code-block:: bash

    sudo vim /etc/bind/named.conf.local

.. code-block:: bash

    zone "workspace.local" IN {
        type master;
        file "/etc/bind/db.workspace";
    };

    zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "/etc/bind/db.1.168.192";
    };

Fedora
======

.. code-block:: bash

    vim /etc/named.conf

Cambiar al principio:

.. code-block:: bash

    options {
            listen-on port 53 { 127.0.0.1; 192.168.1.100; };
            listen-on-v6 port 53 { ::1; };
            directory       "/var/named";
            dump-file       "/var/named/data/cache_dump.db";
            statistics-file "/var/named/data/named_stats.txt";
            memstatistics-file "/var/named/data/named_mem_stats.txt";
            allow-query     { localhost; any; };

Insertar entre ``logging {...`` y ``zone "." IN {...``

.. code-block:: bash

    zone "workspace.local" IN {
        type master;
        file "/var/named/db.workspace";
    };

    zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "/var/named/db.1.168.192";
    };

Ubuntu y Fedora
***************

.. code-block:: bash

    # Ubuntu
    sudo vim /etc/bind/db.workspace

    # Fedora
    vim /var/named/db.workspace

.. code-block:: bash

    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     workspace.local. root.workspace.local. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
            IN      NS      ns1.workspace.local.
            IN      A       192.168.1.100

            IN      MX 10   mail.workspace.local.

    ns1     IN      A       192.168.1.100
    mail    IN      A       192.168.1.100
    www     IN      A       192.168.1.100

    ; Otras maquinas
    wsmaq1  IN      A       192.168.1.3

.. code-block:: bash

    # Ubuntu
    sudo vim /etc/bind/db.1.168.192

    # Fedora
    vim /var/named/db.1.168.192

.. code-block:: bash

    ;
    ; BIND reverse data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     workspace.local. root.workspace.local. (
                                  1         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;

            IN      NS      ns1.workspace.local.

            IN      PTR     workspace.local.

    100     IN      PTR     ns1.workspace.local.
    3       IN      PTR     wsmaq1.workspace.local.


Ubuntu
******

.. code-block:: bash

    chmod -R 755 /etc/bind
    chown -R bind:bind /etc/bind
    service bind9 restart

Fedora
******

Firewall

.. code-block:: bash

    systemctl restart named-chroot.service
    systemctl enable named-chroot.service

    firewall-cmd --permanent --add-service=dns
    firewall-cmd --reload
