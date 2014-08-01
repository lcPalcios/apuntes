.. _reference-programacion-csharp-ref_and_out:

###########
ref and out
###########

sirven para usar variables como referencias en los metodos.

Tanto ref, como out, no se pueden usar en parametros opcionales.

Reglas de ref
*************

* El pasametro pasado al metodo, ha de estar declarado e inicializado
* El metodo se le ha de añadir 'ref' (ref int i)
* Al llamar el metodo, en el parametro se ha de volver a usar 'ref' LlamarMethod(ref i)

Reglas de out
*************

* El argumento dentro del metodo (referencia a), se le ha de dar un valor antes de que termine el metodo.
* Tanto el parametro como el argumento, es necerario indicarlo con 'out tipo nombre'
