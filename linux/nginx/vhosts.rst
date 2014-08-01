.. _reference-linux-nginx-vhosts:

.. |br| raw:: html

    <br />

###############
Vhosts en Nginx
###############

Ubuntu
******

Como usuario

.. code-block:: bash

    mkdir ~/public_html

    sudo vim /etc/nginx/sites-available/workspace.local

.. code-block:: bash

    server {
        listen 80;
        server_name lxmaq2.workspace.local;
        access_log /var/log/nginx/workspace-access.log;
        error_log /var/log/nginx/workspace-error.log;
        root /home/snicoper/public_html;

        location / {
            index index.html index.htm index.php;
        }

        location ~* \.(jpg|jpeg|gif|png|css|js|ico|xml)$ {
            access_log        off;
            log_not_found     off;
            expires           360d;
        }

        # Si quiero que se vean los archivos y directorios cambiar a on
        autoindex on;

        location ~ .php$ {
            try_files $uri =404;
            fastcgi_pass unix:/var/run/php5-fpm.sock;
            fastcgi_index index.php;
            include /etc/nginx/fastcgi_params;
        }
    }

Copiar el sitio creado a sites-enabled

.. code-block:: bash

    sudo ln -s /etc/nginx/sites-available/workspace.local /etc/nginx/sites-enabled/workspace.local

**Si instalo phpmyadmin**

En ubuntu ademas, hago un enlace simbolico de phpmyadmin en la carpeta home,
para acceder luego a phpmyadmin http://www.workspace.local/phpmyadmin y me ahorro
tener que crear un nuevo vhost para phpmyadmin.

.. code-block:: bash

    sudo ln -s ln -s /usr/share/phpmyadmin/ public_html/

Reiniciar los servicios.

.. code-block:: bash

    sudo service nginx restart
    sudo service php5-fpm restart

Fedora
******

Todo como root

.. code-block:: bash

    mkdir /home/snicoper/public_html
    chmod 711 /home/snicoper
    chmod 755 /home/snicoper/public_html
    chown snicoper:snicoper /home/snicoper/public_html

    vim /etc/nginx/conf.d/workspace.local.conf

.. code-block:: bash

    server {
        listen 80;
        server_name www.workspace.local;
        access_log /var/log/nginx/workspace-access.log;
        error_log /var/log/nginx/workspace-error.log;
        root /home/snicoper/public_html;

        location / {
            index index.html index.htm index.php;
        }

        location ~* \.(jpg|jpeg|gif|png|css|js|ico|xml)$ {
            access_log        off;
            log_not_found     off;
            expires           360d;
        }

        # Si quiero que se vean los archivos y directorios cambiar a on
        autoindex on;

        location ~ \.php$ {
            include /etc/nginx/fastcgi_params;
            fastcgi_pass  127.0.0.1:9000;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME /home/snicoper/public_html$fastcgi_script_name;
        }
    }

.. code-block:: bash

    systemctl restart nginx.service
    systemctl restart php-fpm.service

.. danger::
    If you get 403 forbidden error, then you probably have problem with SELinux,
    then run simply following command:

    Ver :ref:`reference-linux-fedora-centos-reglas_selinux`

.. warning::
    PRO PROVAR |br|
    Creo que me deberia dar error SELinux...

.. code-block:: bash

    chcon -R -t httpd_sys_content_t /home/snicoper/public_html

    ## Or some apps might need httpd_sys_rw_content_t ##
    chcon -R -t httpd_sys_rw_content_t /home/snicoper/public_html
