.. _reference-programacion-python-django-estructura_de_proyecto_nuevo:

###############################
Estructura de un proyecto nuevo
###############################

Crear el proyecto
*****************

.. code-block:: bash

    django-admin.py startproject nombre_proyecto

freeze
******

.. code-block:: bash

    mkdir requeriments
    pip freeze > reqrequeriments/reqrequeriments.txt

Inicializar Git
********************

.. code-block:: bash

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

    # Specific files #
    ##################

    # OS generated files #
    ######################
    .DS_Store?
    ehthumbs.db
    Icon?
    Thumbs.db
    *~

Primer commit
=============

.. code-block:: bash

    git add --all
    git commit -m "Initial commit, added gitignore and requeriments.txt"

nombre_proyecto es la raiz del proyecto

.. code-block:: bash

    cd nombre_proyecto

    # Crear la estuctura del sitio
    mkdir templates static media

Donde

+ templates -> Archivos .html compartidos
+ static -> archivos .css .js, etc, fonts, img
+ media -> archivos subidos por los usuarios, e.j. imagenes

Crear las carpetas de js, css, etc dentro de static

.. code-block:: bash

    cd static
    mkdir js css img fonts

    cd ..

La aplicacion para el index del sitio ``/``, se llama main y crear el archivo
``base.html`` dentro de ``~/templates``. Cada app tendra un directorio en
``templates/nombre_app`` dentro de ``~/nombre_app``

.. code-block:: bash

    django-admin.py startapp main
    mkdir -p main/templates/main
    touch main/templates/main/index.html
    touch main/urls.py

    touch templates/base.html

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

Añadir TEMPLATE_DIRS y STATICFILES_DIRS en setting.py

.. code-block:: python

    TEMPLATE_DIRS = (
        os.path.join(BASE_DIR, 'nombre_proyecto/templates'),
    )

    STATICFILES_DIRS = (
        os.path.join(BASE_DIR, 'nombre_proyecto/static'),
    )

Editar el timezone y language en setting.py
buscar y remplazar

.. code-block:: python

    LANGUAGE_CODE = 'en-us'

    TIME_ZONE = 'Europe/Madrid'

Para que pueda leer los ``static``  del ``admin``, añadir en ``urls.py`` principal

.. code-block:: python

    url(r'^static/(?P<path>.*)$', 'serve'),


Esqueleto de base.html
**********************

Plantilla base, usa bootstrap y jquery, comprobar las versiones si corresponden

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
    </head>
    <body>

    <div class="navbar navbar-inverse navbar-fixed-top">
            <div class="container">
                <div class="navbar-header">
                    <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                    </button>
                    Application name
                </div>
                <div class="navbar-collapse collapse">
                    <ul class="nav navbar-nav">
                    </ul>
                </div>
            </div>
        </div>

        <div class="container body-content">
            {% block body %}{% endblock body %}
            <hr />
            <footer>
                <p>&copy; Footer de la pagina</p>
            </footer>
        </div>

        <script src="{% static "js/jquery-2.1.1.min.js" %}"></script>
        <script src="{% static "js/bootstrap.min.js" %}"></script>
        {% block scripts %}{% endblock scripts %}
    </body>
    </html>


Estructura
**********

.. code-block:: bash

    (venv)snicoper@lxmaq1 ~/projects/python/nombre_proyecto
    (master) $ pwd
    /home/snicoper/projects/python/nombre_proyecto
    (venv)snicoper@lxmaq1 ~/projects/python/nombre_proyecto
    (master) $ tree
    .
    ├── manage.py
    ├── nombre_proyecto
    │   ├── __init__.py
    │   ├── main
    │   │   ├── admin.py
    │   │   ├── __init__.py
    │   │   ├── migrations
    │   │   │   └── __init__.py
    │   │   ├── models.py
    │   │   ├── templates
    │   │   │   └── main
    │   │   │       └── index.html
    │   │   ├── tests.py
    │   │   ├── urls.py
    │   │   └── views.py
    │   ├── media
    │   ├── settings.py
    │   ├── static
    │   │   ├── css
    │   │   ├── fonts
    │   │   ├── img
    │   │   └── js
    │   ├── templates
    │   │   └── base.html
    │   ├── urls.py
    │   └── wsgi.py
    └── requeriments
        └── requeriments.txt

    13 directories, 15 files
