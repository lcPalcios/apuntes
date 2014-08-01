.. _reference-programacion-apuntes_sin_clasificar-calcular_porcentaje:

###################
Calcular porcentaje
###################

Incrementar un %
****************

Incrementar un % a una cantidad.

+ Cantidad initial -> 200
+ % a incrementar -> 1.10

.. code-block:: bash

    200 * 1.10 = 220

Por el ejemplo, si el porcentaje que se quiere averiguar es 8%, 8 es un integer
y para poderlo pasar a %, se deve hacer la conversion.

Obtener que % se ha aplicado a una cantidad.
********************************************

Para averiguarlo, debemos saber 2 datos:

+ Cantidad total -> 160
+ Cantidad incrementada del % -> 30

.. code-block:: bash

    100 * (cantidad_porcentaje / total)
    100 * (30 / 160) = 18,75 %
