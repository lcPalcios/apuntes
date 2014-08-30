.. _reference-programacion-python-django-estructura_de_proyecto_nuevo:

##############################
Creación de un proyecto Django
##############################

.. note::
    Para esta practica uso Django 1.7rc3 y Python 3.4

La creación de un proyecto en Django te permite generar la estructura de
directorios que mas te guste/interese, etc.

Yo, voy creándome una que para mi gusto esta bien, pero que para nada
significa que este bien o que sea la correcta.

Utilizo Virtualenv/Virtualenvwrapper y tengo creado en env fuera del proyecto.

La instalación de ``Django`` y cualquier otro paquete lo hago con un entorno
virtual de Python.

Dejo aquí como :ref:`reference-linux-python-instalar_python`

Ahora creo un directorio que es donde estará todo lo relacionado
con el proyecto, como docs, cron, requeriments, etc.

.. code-block:: bash

    mkdir proyect_name

Creo varias carpetas, que mas tarde usare.

.. code-block:: bash

    cd proyect_name
    mkdir docs requeriments cron logs bin run

La carpeta de ``cron`` la creo pero no hablare mas de el,
ya que no se cuando me hará falta generar automatizaciones
para el servidor (pensado para producción).

Los documentos (docs), lo genero con Sphinx y en requeriments creo tres archivos,
uno común y otros dos, uno para desarrollo y otro para producción.

Empiezo con requeriments

.. code-block:: bash

    cd requeriments
    touch base.txt production.txt development.txt

    echo '-r base.txt' > production.txt
    echo '-r base.txt' > development.txt

Para un ejemplo simple, ``Django`` estará tanto en producción como en desarrollo,
por lo que se añade a ``base.txt``.

``Sphinx`` y ``django-debug-toolbar`` solo para desarrollo,
``Gunicorn`` solo para producción , así que editamos los tres archivos.

.. note::
    Al no poner versiones, bajara la ultima versión, si se quiere
    especificar la versión poner por ejemplo ``Django==1.6.6``.

    Seria buena idea, al menos después de instalar los paquetes, poner
    las versiones correspondientes.

.. code-block:: bash

    vim base.txt

    # Añadir
    Django
    psycopg2

    vim development.txt

    # Añadir
    Sphinx
    django-debug-toolbar


    vim production.txt

    # Añadir
    gunicorn

Ahora dependiendo de si estamos en el entorno de desarrollo o
el de producción:

.. code-block:: bash

    # Para el entorno de desarrollo.
    pip install -r development.txt

    # Para el entorno de producción.
    pip install -r production.txt

Creacion del proyecto Django
*****************************

El proyecto para la explicación se llamara ``mysite``, así que empezamos con
``django-admin`` en la raíz de ``proyect_name``.

.. code-block:: bash

    django-admin.py startproject mysite

Renombro ``mysite`` a ``src``

.. code-block:: bash

    mv mysite src

Esto genera una pequeña estructura:

.. code-block:: bash

    src
    ├── manage.py
    └── mysite
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py

Entramos a ``src``

.. code-block:: bash

    cd src

La carpeta ``mysite``, la renombro a ``settings``

.. code-block:: bash

    mv mysite settings

Creo que queda mas claro donde están los archivos de configuración.

Ahora, creo dos archivos mas de configuración, uno para desarrollo y otro
para producción, que usara otra base de datos
dentro de la capeta ``settings``.

.. code-block:: bash

    cd settings
    touch settings_prod.py settings_dev.py
    cd ..

El archivo ``settings.py`` lo dejo como base, para las configuraciones que se
comparten en desarrollo y producción.

Edito los archivos recién creados y les añado:

.. code-block:: bash

    echo 'from settings.settings import *' > settings_dev.py
    echo 'from settings.settings import *' > settings_prod.py

De momento, usan las mismas configuraciones, mas tarde las cambiaremos.

Ahora, hay que decirle a ``Django`` que archivos de configuración usar.

Para el caso de desarrollo, cuando se usa ``./manage.py``, hay que editar ese mismo
archivo. ``manage.py``

.. code-block:: bash

    # cambiar
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "mysite.settings")

    # por
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "settings.settings_dev")

Cambiar dentro de ``settings/settings.py`` algunas configuraciones.

.. code-block:: bash

    # Linea 51, cambiar
    ROOT_URLCONF = 'settings.urls'

    # Linea 53, cambiar
    WSGI_APPLICATION = 'settings.wsgi.application'

Estados de ``DEBUG`` y ``Database``

Editar en ``settings/settings.py``, y aliminar lo siguiente:

.. code-block:: python

    # Eliminar
    # SECURITY WARNING: don't run with debug turned on in production!
    DEBUG = True

    TEMPLATE_DEBUG = True

    ALLOWED_HOSTS = []

    # Eliminar
    # Database
    # https://docs.djangoproject.com/en/dev/ref/settings/#databases

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        }
    }

Editar en ``settings/settings_prod.py``

.. code-block:: python

    # Añadir
    # SECURITY WARNING: don't run with debug turned on in production!
    DEBUG = False

    TEMPLATE_DEBUG = False

    ALLOWED_HOSTS = ['ip(s) y/o dominio(s), aquí']

    # Añadir la base de datos de produccion
    # Database
    # https://docs.djangoproject.com/en/dev/ref/settings/#databases

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        }
    }

En ``ALLOWED_HOSTS = []`` Añadir un string con el dominio o ip.

Editar en ``settings/settings_dev.py``

.. code-block:: python

    # SECURITY WARNING: don't run with debug turned on in production!
    DEBUG = True

    TEMPLATE_DEBUG = True

    # Añadir la base de datos de desarrollo
    # Database
    # https://docs.djangoproject.com/en/dev/ref/settings/#databases

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        }
    }

.. note::
    Configurar las bases de datos.

Modificar ``settings/wsgi.py`` para decirle cual es el archivo de configuración
de producción.

.. code-block:: bash

    # Linea 11, cambiar
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "settings.settings_prod")

Lo básico ya esta creado y configurado, ahora los directorios.

Crear directorios para templates, media, etc., Nos situamos en ``src``
y creamos algunas carpetas.

.. code-block:: bash

    mkdir templates media static
    cd ..

* **static** - Archivos de imágenes del sitio, css, jss y fonts para Bootstrap
* **media** - Archivos por el servidos, por usuarios o administración.
* **templates** - Archivos .html

Dentro de ``static`` creamos cuatro carpetas, ``img, js, fonts, css``

.. code-block:: bash

    cd static
    mkdir img js fonts css

Ahora descargamos `Bootstrap <http://getbootstrap.com/>`_ y copiamos los archivos
dentro de cada carpeta en ``static``.

Hacemos los mismo con `JQuery <http://jquery.com/>`_

Dentro de templates, creamos algunos archivos ``.html``

.. code-block:: bash

    cd templates
    touch base.html 404.html 500.html _messages.html

Editar ``base.html`` y añadir

.. code-block:: html

    {% load staticfiles %}
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="utf-8">
        <!--[if IE]>
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <![endif]-->
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>{% block title %}{% endblock title %}</title>
        <!-- Bootstrap -->
        <link href="{% static "css/bootstrap.min.css" %}" rel="stylesheet">
        <link href="{% static "css/bootstrap-theme.min.css" %}" rel="stylesheet">
        <link href="{% static "css/main.min.css" %}" rel="stylesheet">
        {% block styles %}{% endblock styles %}
    </head>
    <body>
        <nav class="navbar navbar-default navbar-fixed-top" role="navigation">
            <div class="container">
                <div class="navbar-header">
                    <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                    </button>
                    <a class="navbar-brand" href="{% url 'home.index' %}">Application name</a>
                </div>
                <div class="navbar-collapse collapse">
                    <ul class="nav navbar-nav">
                        <li><a href="#">Home</a></li>
                    </ul>
                </div>
            </div>
        </nav>

        <div class="container body-content">
            {% include "_messages.html" %}

            {% block content %}{% endblock content %}

            <hr/>
            {% block footer %}
                <footer>
                    <div>
                        &copy; Footer de la pagina
                    </div>
                </footer>
            {% endblock footer %}
        </div>

        <diV class="go-top">
            <span class="glyphicon glyphicon glyphicon-chevron-up"></span>
        </diV>

        <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
        <script src="{% static "js/jquery-2.1.1.min.js" %}"></script>
        <!-- Include all compiled plugins (below), or include individual files as needed -->
        <script src="{% static "js/bootstrap.min.js" %}"></script>
        <script src="{% static "js/common.min.js" %}"></script>
        {% block scripts %}{% endblock scripts %}
    </body>
    </html>

Editar ``_messages.html`` y añadir:

.. code-block:: html

    {% if messages %}
        <div class="row">
            <div class="col-md-6 col-md-offset-3">
                {% for message in messages %}
                    {% if message.tags == 'error' %}
                        <div class="alert alert-danger">{{ message }}</div>
                    {% else %}
                        <div class="alert alert-{{ message.tags }}">{{ message }}</div>
                    {% endif %}
                {% endfor %}
            </div>
        </div>
    {% endif %}

Con esto saldrá un mensaje de ``django.contrib.messages`` un mensaje en al cabecera
de la pagina.

Editar ``404.html`` y añadir

.. code-block:: bash

    {% extends 'base.html' %}
    {% block title %}Pagina no encontrada{% endblock title %}

    {% block content %}
        <div class="row">
            <div class="col-md-4 col-md-offset-4 col-sm-6 col-sm-offset-3 col-xs-12">
                <h3>Pagina no encontrada</h3>
            </div>
        </div>
    {% endblock content %}

Ir a ``src/templates/js``, crear un archivo ``common.js`` y añadir

.. code-block:: javascript

    // Show or hide the sticky footer button
    $(window).scroll(function() {
        if ($(this).scrollTop() > 200) {
            $('.go-top').fadeIn(200);
        } else {
            $('.go-top').fadeOut(200);
        }
    });

    // Animate the scroll to top
    $('.go-top').click(function(event) {
        event.preventDefault();
        $('html, body').animate({scrollTop: 0}, 300);
    })

Creara un pequeño scroll en la parte inferior derecha de la pagina
para subir a la cabecera.

Ir a ``src/templates/css``, crear un archivo ``main.css`` y añadir

.. code-block:: css

    body {
        padding-top: 70px;
        padding-bottom: 20px;
    }

Editar ``src/settings/settings.py`` y añadir al final

.. code-block:: python

    STATICFILES_DIRS = (
        os.path.join(BASE_DIR, 'static'),
    )

    TEMPLATE_DIRS = (
        os.path.join(BASE_DIR, 'templates'),
    )

APPs
****

Las ``apps`` se puede poner en ``src/`` o crear un directorio ``src/apps``, si se ponen en
``src/``, no hacer nada, si se crea ``src/apps`` modificar ``src/settings/settings.py``.

.. code-block:: python

    # Solo si se van a crear las apps en ~/src/apps/

    # Debajo de:
    import os

    # Insertar:
    import sys

    # Debajo de:
    BASE_DIR = os.path.dirname(os.path.dirname(__file__))

    Insertar:
    sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))

    # Quedando asi:
    import os
    import sys

    BASE_DIR = os.path.dirname(os.path.dirname(__file__))
    sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))

Crear app home
**************

Si se ha creado el directorio ``src/apps`` navegar hasta ``src/apps``,
de lo contrario navegar hasta ``src/``

.. code-block:: bash

    # En src/
    ./manage.py startapp home
    mkdir -p home/templates/home
    touch home/templates/home/index.html
    touch home/urls.py

    # Si es en src/apps, desde src/apps
    django-admin.py startapp home
    mkdir -p apps/home/templates/home
    touch apps/home/templates/home/index.html
    touch apps/home/urls.py

Añadir al index recién creado

.. code-block:: html

    {% extends "base.html" %}

    {% block title %}Home{% endblock title %}

    {% block content %}
        <h2>Home page</h2>
    {% endblock content %}

Editar ``settings/urls.py``

.. code-block:: python

    from django.conf.urls import patterns, include, url
    from django.contrib import admin

    urlpatterns = patterns(
        '',
        url(r'^admin/', include(admin.site.urls)),
        url(r'^$', include('home.urls')),
    )

Editar ``home/urls.py``

.. code-block:: python

    from django.conf.urls import patterns, url

    urlpatterns = patterns(
        'home.views',
        url(r'^$', 'index', name='home.index'),
    )

Editar ``home/views.py``

.. code-block:: python

    from django.shortcuts import render


    def index(request):
        return render(request, 'home/index.html')

Ahora ya solo quedar añadir la ``app`` en ``settings/settings.py``

.. code-block:: python

    # Application definition

    INSTALLED_APPS = (
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    )

    # Local APPS
    INSTALLED_APPS += (
        'home',
    )

GIT
***

Nos situamos en ``src`` e inicializamos git

.. code-block:: bash

    git init .
    git add --all
    git commit -m 'Initial commmit'

Crear .gitignore

.. code-block:: bash

    # File types #
    ##############
    *.pyc
    *.swo
    *.swp
    *.swn

    # Directories #
    ###############
    __pycache__/
    logs/
    .idea/
    build/

    # Specific files #
    ##################

    # OS generated files #
    ######################
    .directory
    .DS_Store?
    ehthumbs.db
    Icon?
    Thumbs.db
    *~

Resultado final de la estructura:

.. code-block:: bash

    .
    |-- .git
    |-- .gitignore
    |-- bin
    |   `-- gunicorn_start.sh
    |-- cron
    |-- docs
    |-- logs
    |-- requeriments
    |   |-- base.txt
    |   |-- development.txt
    |   `-- production.txt
    |-- run
    `-- src
        |-- apps
        |   `-- home
        |       |-- __init__.py
        |       |-- admin.py
        |       |-- migrations
        |       |   `-- __init__.py
        |       |-- models.py
        |       |-- templates
        |       |   `-- home
        |       |       `-- index.html
        |       |-- tests.py
        |       |-- urls.py
        |       `-- views.py
        |-- manage.py
        |-- media
        |-- settings
        |   |-- __init__.py
        |   |-- settings.py
        |   |-- settings_dev.py
        |   |-- settings_prod.py
        |   |-- urls.py
        |   `-- wsgi.py
        |-- static
        |   |-- css
        |   |   |-- bootstrap-theme.css
        |   |   |-- bootstrap-theme.css.map
        |   |   |-- bootstrap-theme.min.css
        |   |   |-- bootstrap.css
        |   |   |-- bootstrap.css.map
        |   |   |-- bootstrap.min.css
        |   |   |-- main.css
        |   |   `-- main.min.css
        |   |-- fonts
        |   |   |-- glyphicons-halflings-regular.eot
        |   |   |-- glyphicons-halflings-regular.svg
        |   |   |-- glyphicons-halflings-regular.ttf
        |   |   `-- glyphicons-halflings-regular.woff
        |   |-- img
        |   `-- js
        |       |-- bootstrap.js
        |       |-- bootstrap.min.js
        |       |-- common.js
        |       |-- common.min.js
        |       `-- jquery-2.1.1.min.js
        `-- templates
            |-- 404.html
            |-- 500.html
            |-- _messages.html
            `-- base.html

Si todo ha salido bien

.. code-block:: bash

    ./manage.py runserver

Me dejo en github una plantilla creada

`GitHub <https://github.com/snicoper/structura-dj>`_

Quizas te pueda interesar: :ref:`reference-linux-nginx-nginx_gunicorn_django`
