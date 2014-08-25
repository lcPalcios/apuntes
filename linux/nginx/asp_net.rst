.. _reference-linux-nginx-asp_net:

#################
ASP .NET en Nginx
#################

.. note::
    No esta del todo completada y solo esta de momento, para Ubuntu.

Ubuntu
******

Crear el sitio donde se alojaran los archivos.

.. code-block:: bash

    mkdir ~/public_html/asp

Configurar un entorno virtual para Nginx

.. code-block:: bash

    sudo vim /etc/nginx/sites-available/asp.workspace.local


Añadir

.. code-block:: bash

    server {
        listen   80;
        server_name  asp.workspace.local;
        access_log   /var/log/nginx/asp.workspace.local.access.log;

        location / {
            root /home/snicoper/public_html/asp/;
            index index.html index.htm default.aspx Default.aspx;
            fastcgi_index Default.aspx;
            fastcgi_pass 127.0.0.1:9090;
            include /etc/nginx/fastcgi_params;
        }
    }

Poner en sites-enabled

.. code-block:: bash

    sudo ln -s /etc/nginx/sites-available/asp.workspace.local /etc/nginx/sites-enabled/asp.workspace.local

Añadir en /etc/nginx/fastcgi_params

.. code-block:: bash

    sudo vim /etc/nginx/fastcgi_params

.. code-block:: bash

    fastcgi_param  PATH_INFO          "";
    fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;

    fastcgi-mono-server4 /applications=asp.workspace.local:/:/home/snicoper/public_html/asp/ /socket=tcp:127.0.0.1:9090 &


Mirar el PID y para cerrar kill (PID)
Para saber el PID

.. code-block:: bash

    pidof mono
    sudo service nginx restart

Una pagina de prueba
********************

.. code-block:: bash

    vim /home/snicoper/public_html/asp/Default.aspx

.. code-block:: html

    <%@ Page language="C#" %>
    <html>
        <head>
            <title>Hello C#</title>
        </head>
        <body>
            <p><% Response.Write("Hello World");%></p>
        </body>
    </html>

.. note::
    Falta por hacer auto inicio de XPS4
