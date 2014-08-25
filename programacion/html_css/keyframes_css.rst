.. _reference-programacion-html_css-keyframes_css:

#############
keyframes css
#############

keyframes es una animación que puede hacerse infinitamente

Lo primo es crear una animación:

.. code-block:: css

    @keyframes nombreKeyFrame {
        0% {
            /* reglas css */
        }
        50% {
            /* reglas css */
        }
        100% {
            /* reglas css */
        }
    }

Para ejecutar el keyframe:

.. code-block:: css

    .mi_regla_css {
        /* Aqui las reglas css */
        animacion: nombreKeyFrame 1.5s infinite ease-in;
    }
