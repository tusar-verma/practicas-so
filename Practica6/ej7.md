### 1

FAT no soporta enlaces simbólicos, ext2 sí.

### 2

Para FAT podemos tener una tabla de tamaño acotada jugando con el tamaño del bloque. A cambio, tenemos mayor fragmentación intera si los archivos son de tamaño chico en comparación al tamaño del bloque

Para ext2 la cantidad de disco que hay que usar para estructura del file system es fija por cada block group y no se puede modificar mucho. Es decir es proporcional al tamaño del disco.

Podemos elegir entonces FAT, ya que uno puede mantener chico el tamaño de la estructura a cambio de bloques más grandes.

### 3

Para FAT uno podría tener el archivo del tamaño que quiciera, ya que los bloques se relacionan como una lista enlazada que puede crecer hasta el tamaño del disco.

En cambio para ext2 depende de la configuración que se emplee para los inodos y los bloques.

### 4

Para esta característica, ext2 es mejor. Carga en memoria las estructuras correspondientes a los bloques de los archivos que necesita. En cambio FAT tenemos que cargar toda la tabla en memoria, que corresponde a todos los archivos guardados en el disco.