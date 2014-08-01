.. _reference-linux-fedora-centos-reglas_selinux:

##############
Reglas SELinux
##############

Virt-Manager y Boxes (Cajas)
****************************

.. code-block:: bash

    setsebool -P virt_use_fusefs 1
    setsebool -P virt_use_rawip 1

Postfix
*******
Para permitir a Apache poder enviar correo electrónico desde alguna aplicación

.. code-block:: bash

    setsebool -P httpd_can_sendmail on

Postgresql
**********

.. code-block:: bash

    setsebool -P allow_user_postgresql_connect on

Memcached
*********

.. code-block:: bash

    setsebool -P httpd_can_network_memcache 1

Apache2.4 y Nginx
*****************

Para permitir que Apache pueda leer contenidos localizados en los directorios
de inicio de los usuarios locales

.. code-block:: bash

    setsebool -P httpd_enable_homedirs 1
    setsebool -P httpd_read_user_content 1

Enable File Control Contexts (No me hizo falta)

.. code-block:: bash

    setsebool -P httpd_unified 1

Para definir que un directorio fuera de ``/var/www``, como por ejemplo
``/sitios/dominio.tld/html``, pueda ser utilizado por Apache, se le debe asignar el
contexto httpd_sys_content_t. Éste puede asignarse a través del mandato chcon,
como se muestra en el siguiente ejemplo

.. code-block:: bash

    chcon -t httpd_sys_content_t /sitios/dominio.tld/htm

    # ls -Z para saber el contexto
