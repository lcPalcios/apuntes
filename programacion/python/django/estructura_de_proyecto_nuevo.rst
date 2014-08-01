.. _reference-programacion-python-django-estructura_de_proyecto_nuevo:

###############################
Estructura de un proyecto nuevo
###############################

.. warning::
    Reparsarlo

Crear el proyecto

.. code-block:: bash

    django-admin.py startproject nombre_proyecto


Renombrar nombre_proyecto a src

.. code-block:: bash

    mv nombre_proyecto src
    cd src

freeze
******

.. code-block:: bash

    mkdir requeriments
    pip freeze > reqrequeriments/reqrequeriments.txt

Inicializar repo Git
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

nombre_proyecto es la raiz del pryecto

.. code-block:: bash

    cd nombre_proyecto

    # Crear la estuctura del sitio
    mkdir templates apps static media

    # apps como modulo
    touch apps/__init__.py

Donde

+ templates -> Los archivos .html
+ apps -> las aplicaciones
+ static -> archivos .css .js, etc, fonts, img
+ media -> media que suban los usuarios

Crear las carpetas de js, css, etc dentro de static

.. code-block:: bash

    cd static
    mkdir js css img fonts

    cd ..

La aplicacion para el home, se llama main y crear el archivo base.html dentro de templates.
Cada apps/nombre_app tendra un directorio en templates/nombre_app.

.. code-block:: bash

    cd apps

    django-admin.py startapp main
    touch main/urls.py

    cd ..

    mkdir templates/main
    touch templates/main/index.html
    touch templates/base.html

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

Para que pueda los static del admin, añadir en urls.py principal

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
