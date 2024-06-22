El siguiente protocolo puede ser iniciado desde cualquier nodo que requiera seleccionar un nuevo lider en una red con topología anillo

- El nodo inicial le manda su ID al proximo nodo en el anillo
- Cuando un nodo recibe un ID, lo compara con el suyo y reenvia el menor de los dos
- El proceso sigue hasta que un nodo recibe su propio ID. Dicho nodo es el que menor ID tiene y se proclama lider
- Por ultimo lo notifica mandando un mensaje por el anillo.
- Cuando le llega la notificación al lider, recorrió todo el anillo y damos por terminado el protocolo

Cantidad de mensajes:
    - Para elegir el lider, en el peor caso el nodo con mínimo ID es el nodo antecesor al que inició el protocolo, por lo que se necesitan 2 vueltas por el anillo. Uno para obtener el minimo ID y otro para que llegue nuevamente al nodo con mínimo ID
    - Para la notificación de lider solo se necesita una vuelta
    - En total son 3n mensajes $O(n)$