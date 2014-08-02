.. _reference-programacion-csharp-metodos_extension_csharp:

#######################
Metodos de Extension C#
#######################

Fuentes
*******

* http://msdn.microsoft.com/es-es/library/bb383977.aspx

---------

Cita de MSDN

.. raw:: html

    <cite>
        Los métodos de extensión permiten "agregar" métodos a los tipos existentes
        sin crear un nuevo tipo derivado, recompilar o modificar de otra manera el
        tipo original. Los métodos de extensión son una clase especial de método
        estático, pero se les llama como si fueran métodos de instancia en el tipo
        extendido. En el caso del código de cliente escrito en C# y Visual Basic,
        no existe ninguna diferencia aparente entre llamar a un método de extensión
        y llamar a los métodos realmente definidos en un tipo.
    </cite>

Ejemplo simple
**************

Los metodos de extension deven estar en una clase ``static`` y el metodo tambien
ha de ser ``static``.

.. code-block:: c#

    public static clss StringExtension
    {
        public static string UcFirst(this string str)
        {
            if (str.Length == 0)
            {
                return string.Empty;
            }

            return string.Format("{0}{1}",
                str[0].ToUpper(), str.SubString(1));
        }
    }

El primer parametro ``UcFirst(this string str)`` con ``this`` le decimos
a que hace referencia, en este caso es un tipo ``string``, pero podria
ser cualquier tipo.

Despues del pirmer parametro, se pueden poner tantos como se quiera,
lo que al llamar al metodo, el "primer" argumento se omite.

.. code-block:: c#

    string nombre = "salvador";

    Console.WriteLine(nombre.UcFirst()); // Salvador

Al ser una extension de ``string`` al ``nombre.MyExtension()`` es como si
el metodo fuera parte del string.
