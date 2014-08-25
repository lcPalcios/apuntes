.. _reference-programacion-csharp-aspnet-mvc-redireccionar_dentro_de_un_controlador:

######################################
Redireccionar dentro de un controlador
######################################

Hay dos maneras para hacerlo, las dos el metodo debe devolver un ``RedirectToRouteResult``,
y dentro del método debe usar ``RedirectToRoute`` o ``RedirectToAction``.

Ambos tienen el mismo efecto y coinciden en sus argumentos.

Ejemplo básico de RedirectToRoute

.. code-block:: c#

    public RedirectToRouteResult Accion()
    {
        return RedirectToRoute(
            new { controller = "Customer", action = "ChangePassword",
                user = "snicoper", password = "123456" });
    }

Ejemplo básico de ``RedirectToAction``, ``user`` y ``password`` son
parámetros para la acción.

.. code-block:: c#

    public RedirectToRouteResult Accion()
    {
        return RedirectToAction(
            "ChangePassword", "Customer",
            new { user = "snicoper", password = "123456" });
    }

Varian un poco en como pasar los argumentos, pero tienen exactamente el mismo efecto.

Otra manera es con una propiedad de la clase base ``Controller``,
la propiedad es ``Response``

.. code-block:: c#

    public void ProduceRedirect()
    {
        Response.Redirect("/Url/Aqui"):
    }

O tambien devolviendo un ``RedirectResult``

.. code-block:: c#

    public RedirectResult ProduceRedirect()
    {
        return Redirect("/Url/Aqui"):

        // Cambio permanente
        return RedirectPermanent("/Url/Aqui");
    }

.. note::
    Es mejor los dos primeros enfoques, ver Pro ASP.NET MVC 5 pagina 443.

    El problema con el uso de direcciones URL literales para la redirección es
    que cualquier cambio en el esquema de enrutamiento significa que hay que
    ir a través del código y actualizar las direcciones URL.

    En cambio con ``Redirect``, si el router cambia, se tendrá que
    buscar/modificar las rutas.

