## FAT

Tenemos cargado en memoria la tabla y basta con recorrerla para obtener las direcciones de los bloques que se quiere leer. Por lo tanto, por cada bloque en la secuencia se hace una lectura en disco.  

- I: 9
- II: 7
- III: 3
- IV: 37

## EXT2
Para este sistema asumo que los bloques son de 4KB y el tamaño de direcciones de bloques de disco es de 4 bytes

Tenemos carga en memoria el inodo 

- I:
    - Con las direcciones directas tenemos los bloques 1, 2, 3, 5, 7, 11. Necesitamos hacer `6` accesos a disco para estos bloques.
    - Para los bloques 13, 17, 23 basta con la indirección simple, ya que puede direccionar 1024 bloques. Cargamos la tabla de indirección simple y los 4 bloques de datos. Tenemos `4` accesos a disco
    - En total tenemos 10 accesos a disco

- II:
    - Para los bloques 1, 2, 3, 4, 5, 6 usamos la direcciones directas. `6` accesos.
    - La indirección simple puede direccionar 1024 bloques. Entonces direccionará a los bloques 12 a 1035
    - La indirección doble direcciona a una tabla de indirección simple, cada una puede direccionar 1024 bloques. Por lo que en total la tabla de indirección doble puede direccionar 1024 * 1024 bloques = 1048576 bloques. Del bloque 1036 al 1049599. Luego el bloque 10001 entra en este rango.
    - Calculamos en que entrada de la tabla de indirección doble está el bloque a cargar. `1` acceso a disco para cargar la indirección doble: 
        - bloque relativo a la indirección doble: 10001 - 1035 = 8966
        - entrada de la indirección doble que tiene dicho bloque: 8966 \ 1024 = 8. Cargamos esta tabla de direcciones simples. `1` acceso a disco
        - dirección del bloque dentro de la tabla de direcciones simples: 8966 % 1024 = 774. Cargamos este bloque, que es el dato que queríamos. `1` acceso a disco
    - En total hicimos 9 accesos a disco

- III:
    - Para el bloque 13 cargamos la indirección simple y el bloque 13. `2` accesos.
    - Para el 10000 hacemos el mismo proceso que para el 10001 en II, dando `3` accesos a disco
    - Para el 1000000, el bloque sigue entrando en el rango de indirección doble, pero no necesitamos volver a cargar la indirección doble, si la segunda tabla y el bloque en sí. `2` acceos a disco
    - En total 7 accesos a disco

- IV
    - Todos los bloques caen en la indirección simple. Cargamos el bloque de la indirección, `1` acceso, y los `37` bloques de datos. En total 38 accesos a disco