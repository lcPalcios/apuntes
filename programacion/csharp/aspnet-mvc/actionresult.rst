.. _reference-programacion-csharp-aspnet-mvc-actionresult:

.. |br| raw:: html

    <br />

############
ActionResult
############

======================  ====================================    ============================================
Action Result           Helper Method                           Descripcion
======================  ====================================    ============================================
ViewResult              View                                    Renderiza una Vista como pagina Web.

PartialViewResult       PartialView                             Renderiza una vista parcial, que define |br|
                                                                una sección de una vista que se puede |br|
                                                                representar dentro de otro vista.

RedirectResult          Redirect                                Redirecciona a otro método de acción |br|
                                                                utilizando su URL.

RedirectToRouteResult   RedirectToAction o                      Redirecciona a otro metodo de acción.
                        |br| RedirectToRoute


ContentResult           Content                                 Representa un tipo de contenido definido |br|
                                                                por el usuario que es el resultado de un |br|
                                                                método de acción.

JsonResult              Json                                    Representa una clase que se usa para |br|
                                                                enviar contenido con formato JSON a la |br|
                                                                respuesta.

JavaScriptResult        JavaScript                              Envía el contenido de JavaScript a la |br|
                                                                respuesta

HttpStatusCodeResult    (None)                                  Proporciona un modo para devolver un |br|
                                                                resultado de la acción con un código  |br|
                                                                de estado de respuesta HTTP y una |br|
                                                                descripción específicos.

HttpUnauthorizedResult  (None)                                  Representa el resultado de una solicitud |br|
                                                                HTTP no autorizada.

HttpNotFoundResult      HttpNotFound                            Define un objeto que se usa para indicar |br|
                                                                que no se encontró el recurso solicitado.

FileResult              File                                    Representa una clase base que se usa para |br|
                                                                enviar contenido de archivo binario a la |br|
                                                                respuesta.

FileContentResult       Controller.File(Byte[], String) |br|    Envía el contenido de un archivo binario |br|
                        or Controller.File(Byte[], |br|         a la respuesta.
                        String, String)

FilePathResult          Controller.File(String, String) |br|
                        or Controller.File(String, |br|
                        String, String)                         Envía el contenido de un archivo a la |br|
                                                                respuesta.

FileStreamResult        Controller.File(Stream, String) |br|
                        or Controller.File(Stream, |br|
                        String, String)                         Envía el contenido binario a la |br|
                                                                respuesta mediante una instancia |br|
                                                                de Stream.

EmptyResult             (None)                                  Representa un resultado que no |br|
                                                                hace nada, tal como un método de |br|
                                                                acción de controlador que no devuelve |br|
                                                                nada.
======================  ====================================    ============================================
