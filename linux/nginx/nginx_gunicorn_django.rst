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
    SOCKFILE=/home/snicoper/projects/python/proyect_name/run/gunicorn.sock # we will communicte using this unix socket
    LOGFILE=/home/snicoper/projects/python/proyect_name/logs/gunicorn.log
    LOGDIR=$(dirname $LOGFILE)
    USER=snicoper # the user to run as
    GROUP=snicoper # the group to run as
    NUM_WORKERS=3 # how many worker processes should Gunicorn spawn
    DJANGO_SETTINGS_MODULE=settings.settings_prod # which settings file should Django use
    DJANGO_WSGI_MODULE=settings.wsgi # WSGI module name

    echo "Starting $NAME as `whoami`"

    # Activate the virtual environment
    source /home/snicoper/.virtualenvs/default/bin/activate
    export DJANGO_SETTINGS_MODULE=$DJANGO_SETTINGS_MODULE
    export PYTHONPATH=$DJANGODIR:$PYTHONPATH

    # Create the run directory if it doesn't exist
    RUNDIR=$(dirname $SOCKFILE)
    test -d $RUNDIR || mkdir -p $RUNDIR

    # Start your Django Unicorn
    # Programs meant to be run under supervisor should not daemonize themselves (do not use --daemon)
    exec gunicorn ${DJANGO_WSGI_MODULE}:application \
    --name $NAME \
    --workers $NUM_WORKERS \
    --user=$USER --group=$GROUP \
    --bind=unix:$SOCKFILE \
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

.. code-block:: bash

    sudo vim /etc/nginx/sites-avalaible/proyect_name

Añadimos

.. code-block:: bash

    upstream proyect_name_server {
        # fail_timeout=0 means we always retry an upstream even if it failed
        # to return a good HTTP response (in case the Unicorn master nukes a
        # single worker for timing out).

        server unix:/home/snicoper/projects/python/proyect_name/run/gunicorn.sock fail_timeout=0;
    }

    server {
        listen   80;
        server_name lxmaq1.workspace.local;

        access_log /home/snicoper/projects/python/proyect_name/logs/nginx-access.log;
        error_log /home/snicoper/projects/python/proyect_name/logs/nginx-error.log;

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
            root /home/snicoper/.virtualenvs/default/lib/python3.4/site-packages/django/contrib/admin/;
        }

         location / {
            # an HTTP header important enough to have its own Wikipedia entry:
            # http://en.wikipedia.org/wiki/X-Forwarded-For
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

            # enable this if and only if you use HTTPS, this helps Rack
            # set the proper protocol for doing redirects:
            # proxy_set_header X-Forwarded-Proto https;

            # pass the Host: header from the client right along so redirects
            # can be set properly within the Rack application
            proxy_set_header Host $http_host;

            # we don't want nginx trying to do something clever with
            # redirects, we set the Host: header above already.
            proxy_redirect off;

            # set "proxy_buffering off" *only* for Rainbows! when doing
            # Comet/long-poll stuff. It's also safe to set if you're
            # using only serving fast clients with Unicorn + nginx.
            # Otherwise you _want_ nginx to buffer responses to slow
            # clients, really.
            # proxy_buffering off;

            # Try to serve static files from nginx, no point in making an
            # *application* server like Unicorn/Rainbows! serve static files.
            if (!-f $request_filename) {
            proxy_pass http://proyect_name_server;
                break;
            }
        }

        # what to serve if upstream is not available or crashes
        error_page 500 502 503 504 /media/50x.html;
    }

.. code-block:: bash

    sudo ln -s /etc/nginx/sites-avalaible/proyect_name /etc/nginx/sites-enabled/proyect_name

Reiniciar nginx

.. code-block:: bash

    sudo service nginx restart

Supervisor
**********

.. code-block:: bash

    sudo apt-get install supervisor
    sudo vim /etc/supervisor/conf.d/proyect_name.conf

Añadir

.. code-block:: bash

    [program:proyect_name]
    command = /home/snicoper/projects/python/proyect_name/bin/gunicorn_start.sh ; Command to start app
    user = snicoper ; User to run as
    stdout_logfile = /home/snicoper/projects/python/proyect_name/logs/gunicorn_supervisor.log ; Where to write log messages
    redirect_stderr = true ; Save stderr in the same log
    environment=LANG=en_US.UTF-8,LC_ALL=en_US.UTF-8 ; Set UTF-8 as default encoding

Crear archivo de log

.. code-block:: bash

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

