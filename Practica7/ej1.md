### a

El nodo A no puede diferenciar entre la caida del nodo B y la caida de la conexión entre el nodo A y B.

Para el caso de que el tiempo de respuesta es 100 veces mayor al normal, depende del timeout que tiene configurado el nodo A. Si el timeout es mayor al tiempo de respuesta de B, entonces puede comunicarse con B.

### b

Al momento de que A recibe un mensaje de D a travez de B no se puede asumir nada sobre el estado de D, ya que pudo haber pasado varios eventos hasta que llegó el mensaje. 

Realmente aunque A y D esten conectados directamente no se puede asumir nada sobre el nodo D, ya que aunque se reciba el mensaje de D, el estado siguiente puede ser diferente.

### c

No se puede deducir el orden de envio a partir del orden de llegada de los mensajes. Estos dependen fuertemente del medio por donde se envian.