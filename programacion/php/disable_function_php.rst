.. _reference-programacion-php-disable_function_php:

################
Disable function
################

En ``php.ini`` una directiva es ``disable_function =``

pasando en un string y separados por comas, es posible desactivar funciones
como eval u otras potencialmente peligrosas para el proyecto.

Esto solo funciona en ``php.ini``, no con ``php_value`` (apache) o ``ini_set()``
