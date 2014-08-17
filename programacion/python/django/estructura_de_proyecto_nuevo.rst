.. _reference-programacion-python-django-estructura_de_proyecto_nuevo:

###############################
Estructura de un proyecto nuevo
###############################

Crear el proyecto
*****************

.. code-block:: bash

    django-admin.py startproject nombre_proyecto
    cd nombre_proyecto

freeze

.. code-block:: bash

    mkdir requeriments
    pip freeze > requeriments/requeriments.txt

nombre_proyecto es la raiz del proyecto

.. code-block:: bash

    cd nombre_proyecto

    # Crear la estuctura del sitio
    mkdir apps templates static media

Donde

+ apps -> Aplicaciones
+ templates -> Archivos .html compartidos
+ static -> archivos .css .js, etc, fonts, img
+ media -> archivos subidos por los usuarios, e.j. imagenes

Crear las carpetas de js, css, etc dentro de static

.. code-block:: bash

    cd static
    mkdir js css img fonts
    touch css/main.css
    cd ..

La aplicacion para el index del sitio ``/``, se llama home y crear el archivo
``base.html`` dentro de ``~/templates``. Cada app tendra un directorio en
``templates/nombre_app`` dentro de ``~/nombre_app``

.. code-block:: bash

    cd apps
    django-admin.py startapp home
    mkdir -p home/templates/home
    touch home/templates/home/index.html
    touch home/urls.py
    cd ..
    touch templates/base.html
    touch templates/404.html
    touch templates/500.html

.. note::
    **Copiado y pegado del** `tutorial django <https://docs.djangoproject.com/en/1.6/intro/tutorial03/>`_

    Podríamos tener todas nuestras plantillas juntas, en un solo directorio de
    plantillas grandes, y que funcionaría perfectamente bien. Sin embargo, esta
    plantilla pertenece a la aplicación polls, por lo que a diferencia de la
    plantilla de administración que hemos creado en el tutorial anterior, vamos
    a poner esto en el directorio de la plantilla de la aplicación (``polls/templates``)
    y no del proyecto (``templates``).

    Ahora podríamos ser capaces de salirse con poner nuestras plantillas
    directamente en ``polls/templates`` (en lugar de crear otro subdirectorio
    polls), pero en realidad sería una mala idea.
    Django elegirá la primera plantilla que encuentra cuyo nombre coincide,
    y si has tenido una plantilla con el mismo nombre en una aplicación diferente,
    Django sería incapaz de distinguir entre ellos.
    Tenemos que ser capaces de señalar Django la correcta, y la mejor manera
    de asegurar esto es por el namespacing.
    Es decir, al poner las plantillas dentro de otro directorio llamado
    así por la propia aplicación.

Añadir al pythonpath el directorio ``apps``, en el inicio de ``setting.py``

.. code-block:: python

    # Build paths inside the project like this: os.path.join(BASE_DIR, ...)
    import os
    import sys
    BASE_DIR = os.path.dirname(os.path.dirname(__file__))
    sys.path.insert(0, BASE_DIR + '/nombre_proyecto/apps/')

Añadir la nueva ``app`` en ``INSTALLED_APPS``

``setting.py``

.. code-block:: python

    INSTALLED_APPS = (
        [...]
        'home',
    )

Añadir TEMPLATE_DIRS y STATICFILES_DIRS al final de ``setting.py``

.. code-block:: python

    TEMPLATE_DIRS = (
        os.path.join(BASE_DIR, 'nombre_proyecto/templates'),
    )

    STATICFILES_DIRS = (
        os.path.join(BASE_DIR, 'nombre_proyecto/static'),
    )

Editar el timezone y language en ``setting.py``
buscar y remplazar

.. code-block:: python

    LANGUAGE_CODE = 'en-us'

    TIME_ZONE = 'Europe/Madrid'

Esqueleto de base.html y main.css
*********************************

Plantilla base, usa bootstrap y jquery, comprobar las versiones si corresponden

``templates/base.html``

.. code-block:: html

    {% load staticfiles %}
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>{% block title %}{% endblock title %}</title>
        <link href="{% static "css/bootstrap.min.css" %}" rel="stylesheet">
        <link href="{% static "css/bootstrap-theme.min.css" %}" rel="stylesheet">
        <link href="{% static "css/main.css" %}" rel="stylesheet">
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
                    <a class = "navbar-brand" href="{% url 'books.index' %}">Application name</a>
                </div>
                <div class="navbar-collapse collapse">
                    <ul class="nav navbar-nav">
                        <li>Link 1</li>
                    </ul>
                </div>
            </div>
        </nav>

        <div class="container body-content">
            {% block content %}{% endblock content %}
            <hr />
            {% block footer %}
                <footer>
                    <p>&copy; Footer de la pagina</p>
                </footer>
            {% endblock footer %}
        </div>

        <script src="{% static "js/jquery-2.1.1.min.js" %}"></script>
        <script src="{% static "js/bootstrap.min.js" %}"></script>
        {% block scripts %}{% endblock scripts %}
    </body>
    </html>


``static/css/main.css``

.. code-block:: css

    body {
        padding-top: 70px;
        padding-bottom: 20px;
    }

``home/templates/home/index.html``

.. code-block:: css

    {% extends "base.html" %}

    {% block body %}
        <h1>Pagina inicio</h1>
    {% endblock body %}

Git
********************

.. code-block:: bash

    cd ..
    git init .
    vim .gitignore

Añadir a .gitignore

.. code-block:: bash

    # File types #
    ##############
    *.pyc
    *.swo
    *.swp
    *.swn

    # Directories #
    ###############
    logs/
    __pycache__/
    .idea/

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

.. code-block:: bash

    git add --all
    git commit -m "Initial commit, added gitignore, requeriments.txt and structure"

Estructura
**********

.. code-block:: bash

    .
    ├── manage.py
    ├── nombre_proyecto
    │   ├── apps
    │   │   └── home
    │   │       ├── admin.py
    │   │       ├── __init__.py
    │   │       ├── migrations
    │   │       │   └── __init__.py
    │   │       ├── models.py
    │   │       ├── templates
    │   │       │   └── home
    │   │       │       └── index.html
    │   │       ├── tests.py
    │   │       ├── urls.py
    │   │       └── views.py
    │   ├── __init__.py
    │   ├── media
    │   ├── settings.py
    │   ├── static
    │   │   ├── css
    │   │   │   └── main.css
    │   │   ├── fonts
    │   │   ├── img
    │   │   └── js
    │   ├── templates
    │   │   └── base.html
    │   ├── urls.py
    │   └── wsgi.py
    └── requeriments
        └── requeriments.txt

    14 directories, 16 files
