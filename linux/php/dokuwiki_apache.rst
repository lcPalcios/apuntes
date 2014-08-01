.. _reference-linux-php-dokuwiki_apache:

###############
DokuWiki Apache
###############

Fedora
******

Copiar el contenido por ejemplo en ~/public_html/wiki, despues
dar permisos.

.. code-block:: bash

    cd ~/public_html/wiki
    find ./wiki -type d -exec chmod 755 {} \;
    find ./wiki -type f -exec chmod 644 {} \;

    sudo setfacl -R -m u:snicoper:rwx -m u:apache:rwx wiki/conf/ wiki/data/
    sudo setfacl -dR -m u:snicoper:rwx -m u:apache:rwx wiki/conf/ wiki/data/

.. code-block:: bash

Esto no es necesario si esta en ~/public_html/*

.. code-block:: bash

    # chcon -R -t httpd_sys_rw_content_t wiki/data
    # chcon -R -t httpd_sys_rw_content_t wiki/conf

Crear el host virtual

.. code-block:: bash

    sudo vim /etc/httpd/conf.d/wiki.workspace.local.conf

.. code-block:: bash

    <VirtualHost *:80>
        DocumentRoot /home/snicoper/public_html/wiki
        ServerName cvowiki.workspace.local
        ServerAlias cvowiki.workspace.local
        DirectoryIndex index.php
        ServerAdmin snicoper@gmail.com
        ErrorLog logs/cvo.workspace.local-error_log
        CustomLog logs/cvo.workspace.local-access_log combined
        <Directory /home/snicoper/Projects/cvo/wiki>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
            Require all granted
        </Directory>
    </VirtualHost>

Reiniciar apache
.. code-block:: bash

    systemctl restart httpd.service

Ubuntu
******

.. warning::
    Por hacer
