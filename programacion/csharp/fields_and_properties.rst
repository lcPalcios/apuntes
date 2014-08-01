.. _reference-programacion-csharp-fields_and_properties:

####################
Compos y Propiedades
####################

Un campo es el equivalente de una propiedad en PHP.

.. code-block:: c#

    private string nombre;

Una propiedad es un setters/getter con posible logica sobre un campo.

.. code-block:: c#

    public string Nombre
    {
        set
        {
            if (value.Length < 5)
            {
                // hacer algo
            }
            else
            {
                nombre = value;
            }
        }
        get { return nombre; }
    }

A groso modo, se puede decir que un campo(field) son como las propiedades en PHP
y las propiedades son los metodos accesores en PHP, con un mecanisco que lo hacen
mas simples.
