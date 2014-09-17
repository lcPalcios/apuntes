.. _reference-linux-nginx-nginx_gunicorn_django:

####################################
Instalación Nginx, Gunicorn y Django
####################################

**Fuentes**

* http://goodcode.io/blog/django-nginx-gunicorn/
* http://michal.karzynski.pl/blog/2013/06/09/django-nginx-gunicorn-virtualenv-supervisor/
* https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-django-with-postgres-nginx-and-gunicorn

----------

.. note::
    Estas notas estan basadas en la estuctura
    :ref:`reference-programacion-python-django-estructura_de_proyecto_nuevo`

Gunicorn
********

En ``proyect_name/bin``, creamos un archivo ``gunicorn_start.sh``

.. code-block:: bash

    vim bin/gunicorn_start.sh

    # Añadimos

    #!/bin/bash

    NAME="proyect_name" # Name of the application
    DJANGODIR=/home/snicoper/projects/python/proyect_name/src/ # Django project directory
    LOGFILE=/home/snicoper/projects/python/proyect_name/logs/gunicorn.log
    LOGDIR=$(dirname $LOGFILE)
    USER=snicoper # the user to run as
    GROUP=snicoper # the group to run as
    NUM_WORKERS=3 # how many worker processes should Gunicorn spawn
    DJANGO_SETTINGS_MODULE=settings.settings_prod # which settings file should Django use
    DJANGO_WSGI_MODULE=settings.wsgi # WSGI module name

    echo "Starting $NAME as `whoami`"

    # Activate the virtual environment
    cd $DJANGODIR
    source /home/snicoper/.virtualenvs/default/bin/activate
    export DJANGO_SETTINGS_MODULE=$DJANGO_SETTINGS_MODULE
    export PYTHONPATH=$DJANGODIR:$PYTHONPATH

    # Start your Django Unicorn
    # Programs meant to be run under supervisor should not daemonize themselves (do not use --daemon)
    exec gunicorn ${DJANGO_WSGI_MODULE}:application \
        --name $NAME \
        --workers $NUM_WORKERS \
        --user=$USER --group=$GROUP \
        --log-level=debug \
        --log-file=$LOGFILE 2>>$LOGFILE

.. warning::
    Corregir las rutas y usuario!

Permisos de ejecución

.. code-block:: bash

    chmod +x bin/gunicorn_start.sh


Nginx
*****

:ref:`reference-linux-nginx-instalacion_nginx`

.. note::
    En Fedora/Centos si se sirven las paginas en el ``home`` hay que dar pemisos
    al home del usuario ``chmod 711 /home/usuario``

.. code-block:: bash

    sudo vim /etc/nginx/sites-avalaible/proyect_name

Añadimos

.. code-block:: bash

    server {
        listen   80;
        server_name www.workspace.local;

        access_log /var/log/nginx/proyect_name-access.log;
        error_log /var/log/nginx/proyect_name-error.log;

        # Django media
        location /media/  {
            alias /home/snicoper/projects/python/proyect_name/src/media/;  # your Django project's media files - amend as required
        }

        # Django static
        location /static/ {
            alias /home/snicoper/projects/python/proyect_name/src/static/; # your Django project's static files - amend as required
        }

        # Django static admin
        location /static/admin/ {
            # this changes depending on your python version
            alias /home/snicoper/.virtualenvs/default/lib/python3.4/site-packages/django/contrib/admin/static/admin/;
        }

        location / {
            proxy_pass_header Server;
            proxy_set_header Host $http_host;
            proxy_redirect off;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Scheme $scheme;
            proxy_connect_timeout 10;
            proxy_read_timeout 10;
            proxy_pass http://localhost:8000/;
        }

        # what to serve if upstream is not available or crashes
        error_page 500 502 503 504 /media/50x.html;
    }

Si los archivos static no se ven, mirar ``collectstatic`` de django.

.. code-block:: bash

    sudo ln -s /etc/nginx/sites-avalaible/proyect_name /etc/nginx/sites-enabled/proyect_name

Reiniciar nginx

.. code-block:: bash

    sudo service nginx restart

Supervisor
**********

**Ubuntu**

.. code-block:: bash

    sudo apt-get install supervisor
    sudo touch /etc/supervisor/conf.d/proyect_name.conf

**Fedora/Centos**

.. code-block:: bash

    su

    # Requiere repos epel
    yum install supervisor

    # Esto lo tengo que hacer cada vez que reinicio
    supervisord -c /etc/supervisord.conf

    vim /etc/supervisord.conf

    # Cambiar ``*.ini`` por ``*.conf`` al final del archivo.
    [include]
    files = /etc/supervisord.d/*.conf

    touch /etc/supervisord.d/proyect_name.conf

**Ubuntu/Fedora/Centos**

Añadir en ``proyect_name.conf``

.. code-block:: bash

    [program:proyect_name]
    command=/home/snicoper/projects/python/proyect_name/bin/gunicorn_start.sh
    user=snicoper
    stdout_logfile=/home/snicoper/projects/python/proyect_name/logs/gunicorn_supervisor.log
    redirect_stderr=true
    autostart=true
    autorestart=true

Crear archivo de log

.. code-block:: bash

    mkdir /home/snicoper/projects/python/proyect_name/logs
    touch /home/snicoper/projects/python/proyect_name/logs/gunicorn_supervisor.log

.. code-block:: bash

    sudo supervisorctl reread
    sudo supervisorctl update

**Comandos supervisor**

.. code-block:: bash

    sudo supervisorctl status proyect_name
    sudo supervisorctl stop proyect_name
    sudo supervisorctl start proyect_name
    sudo supervisorctl restart proyect_name

