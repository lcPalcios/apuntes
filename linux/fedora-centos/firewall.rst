.. _reference-linux-fedora-centos-firewall:

###############
Firewall Basico
###############

Referencias
***********

* https://fedoraproject.org/wiki/FirewallD#Using_firewall-cmd
* http://ktaraghi.blogspot.com.es/2013/10/what-is-firewalld-and-how-it-works.html
* http://liquidat.wordpress.com/2013/04/09/howto-firewalld-basics/

-------------

* drop (Inmutable):
    Los paquetes de red entrantes se cae, no hay respuesta. Sólo las conexiones de
    red salientes son posibles.

* block:
    Las conexiones de red entrantes se rechazarán con un mensaje icmp-host-prohibited
    para IPv4 e icmp6-adm-prohibido para IPv6. Sólo las conexiones de red iniciadas
    dentro de este sistema son posibles.

* external:
    Para su uso en redes externas con enmascaramiento habilitado especialmente para
    los routers. Usted no confía en los otros equipos de redes para no dañar su equipo.
    Sólo seleccionados conexiones entrantes son aceptadas.

* dmz:
    Para los equipos de la zona de distensión que son de acceso público con acceso
    limitado a la red interna. Sólo seleccionados conexiones entrantes son aceptadas.

* work:
    Para el uso en las áreas de trabajo. Que en su mayoría confían en los otros
    equipos de redes para no dañar su equipo. Sólo seleccionados conexiones entrantes
    son aceptadas.

* home:
    Para su uso en zonas de origen. Que en su mayoría confían en los otros equipos de
    redes para no dañar su equipo. Sólo seleccionados conexiones entrantes son aceptadas.

* internal:
    Para su uso en redes internas. Que en su mayoría confían en los otros equipos de
    la red para no dañar su equipo. Sólo seleccionados conexiones entrantes son
    aceptadas.

* trusted:
    Todas las conexiones de red son aceptadas.

-------------

Añadir un puerto de manera persistente

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-port=80/tcp

Añadir un servicio de manera persistente

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-service=http

Para eliminar cabiar --add-x por --remove-x
