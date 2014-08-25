.. _reference-programacion-csharp-aspnet-mvc-definicion_modelo:

#################
Definición modelo
#################

Fuentes
*******

* Beginning ASP.NET MVC 4 Pagina 69

-----------------

El término modelo se refiere a un conjunto de objetos que implementa una pieza de funcionalidad.
Un modelo en el patrón MVC pueden ser clasificados ya sea como un modelo de datos, un modelo de
negocio, o un modelo de vista. Cada uno de los diferentes tipos de modelo tiene un propósito
específico, tal como se describe en la Tabla 6-1. En su conjunto, los modelos de datos y de
negocios que se conoce como el modelo de dominio. Modelo de vista no son parte del modelo de dominio,
ya que su propósito es sólo para pasar los datos desde el controlador a las vistas y viceversa.

[Modelo de dominio]

+ Data model (Modelo de datos)

    Los objetos en el modelo de datos representan clases que interactúan con una base de datos.
    Normalmente, se puede pensar en el modelo de datos como el conjunto de las clases creadas por
    herramientas como Entity Framework (EF). Estas clases pueden comenzar ya sea en forma de tablas
    existentes en la base de datos que hay que leer para generar clases (enfoque database-first) o
    empezar como clases que se utilizarán para generar tablas de la base de datos
    (enfoque code-first). Además, puede crear manualmente estas clases utilizando ADO.NET para
    implementar la base de datos de interacción particular que necesita su aplicación.

[Modelo de dominio]

+ Business Model (Modelo de negocio)

    Las clases en el modelo de negocio normalmente implementa la funcionalidad que representa las
    reglas de negocio o de procesamiento (por ejemplo, el cálculo de un coste de envío particular
    para un elemento carrito de compras basado en el peso del artículo que se compra). Como parte
    de la transformación, las clases del modelo de negocio pueden interactuar con las clases del
    modelo de datos para leer o guardar datos en la base de datos.

+ View model (Modelo de vista)

    Las clases del modelo de vista proporcionan información transmitida desde los controladores a
    las vistas, por lo que las vistas saben qué hacer en el navegador del usuario.
    Por ejemplo, una clase de modelo de vista puede contener información sobre el producto que es
    utilizado por el fin de mostrar el nombre del producto, el precio, y las imágenes.
    La función de una clase de modelo de vista no es procesar cualquier cosa, más bien, su única
    función es la de contener los datos y metadatos opcional para el fin de rendir adecuadamente.
    Un modelo de vista también se utiliza cuando un usuario realiza una solicitud desde una vista
    previamente prestados (por ejemplo, cuando se envía un formulario de contacto).
