.. _reference-linux-nginx-nginx_gunicorn_django:

####################################
Instalacion Nginx, Gunicorn y Django
####################################

**Fuentes**

* http://goodcode.io/blog/django-nginx-gunicorn/
* http://michal.karzynski.pl/blog/2013/06/09/django-nginx-gunicorn-virtualenv-supervisor/
* https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-django-with-postgres-nginx-and-gunicorn

----------

Ejemplo muy simple para usar django con nginx

.. code-block:: bash

    mkdir myproject
    cd myproject
    virtualenv venv --no-site-packages
    source venv/bin/activate
    (myproject)$ pip install django gunicorn
    (myproject)$ django-admin.py startproject myproject
    (myproject)$ cd myproject

Ubuntu
******

Una vez se esta en el entorno virtual de python, instalar django y gunicorn

Se crea una dicrectorio para el proyecto, dentro estara virtualenv y el proyecto django.

Dentro de la raiz del proyecto django, dende esta ``manage.py``, usamos el comando

.. code-block:: bash

    gunicorn -w 3 myproject.wsgi:application

Ahora hay que crear un virtualhost para nginx

.. code-block:: bash

    sudo vim /etc/nginx/sites-avalaible/lxmaq1

Dentro ponemos lo siguiente (cambiando rutas y server_name)

.. code-block:: bash

    server {
        listen   80;
        server_name lxmaq1.workspace.local;

        # no security problem here, since / is alway passed to upstream
        root /home/snicoper/projects/python/practicas/practicas;

        # Django media
        location /media/  {
            alias /home/snicoper/projects/python/practicas/media/;  # your Django project's media files - amend as required
        }

        # Django static
        location /static/ {
            alias /home/snicoper/projects/python/practicas/static/; # your Django project's static files - amend as required
        }

        # Django static admin
        location /static/admin/ {
            # this changes depending on your python version
            root /home/snicoper/projects/python/venvdefault/lib/python3.4/site-packages/django/contrib/admin/;
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

.. code-block:: bash

    sudo ln -s /etc/nginx/sites-avalaible/lxmaq1 /etc/nginx/sites-enabled/lxmaq1

Reiniciar nginx

.. code-block:: bash

    sudo service nginx restart

Para la practica, puse en ``/etc/hosts``

.. code-block:: bash

    127.0.0.1       lxma1.workspace.local   lxmaq1

Listo, en el navegador entrar a lxma1.workspace.local
