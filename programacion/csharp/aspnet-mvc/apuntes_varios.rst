.. _reference-programacion-csharp-aspnet-mvc-apuntes_varios:

############################
Apuntes Varios para recordar
############################


* `Html.EditorForModel() <http://msdn.microsoft.com/es-es/library/ff406445%28v=vs.118%29.aspx>`_

    Devuelve un elemento input HTML para cada propiedad del modelo,
    mediante los datos de vista adicionales.

* Problemas Con Globalizacion Idiomas

     Para permitir la validación de jQuery para las configuraciones regionales
     distintos del inglés que utilizan una coma (",") para el punto decimal,
     y los formatos de fecha no non-English, debe incluir globalize.js y su
     archivo específico ``cultures/globalize.cultures.jss``
     (desde `https://github.com/jquery/globalize <https://github.com/jquery/globalize>`_ )
     y el JavaScript para visualizar ``Globalize.parseFloat``.
     Usted puede obtener el jQuery non-English validación de NuGet.
     (No instale Globalize si está utilizando una configuración regional Inglés.)

    `Ver <http://www.asp.net/mvc/tutorials/mvc-5/introduction/examining-the-edit-methods-and-edit-view>`_
