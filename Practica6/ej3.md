Tamaño de bloques = `4 KB`
LBA (logical block addressing, dirección del bloque en disco) = `8 bytes`

Entrada inodos
    - 5 entradas directas
    - 2 indirectas 
    - 1 doble inderecta

### a

El tamaño máximo de archivo, en bloques, corresponde a la cantidad de bloques que puede direccionar un inodo.

Cantidad de bloques direccionables
    - directo = `1`
    - indirecto = `4 KB / 8 = 4096 / 8 = 4 * 2^7 = 512 bloques de disco`
    - indirecto doble = `(4 * 2^7) * (4 * 2^7) = 16 * 2^14 = 262144 bloques de disco` 

Por lo que el tamaño máximo, en bloques, es `5 + 2*512 + 262144 = 263173`. En bytes serían `263173 * 4KB = 1052692 KB ≈ 1 GB `

### b

- 50% del espacio en disco ocupado por archivos de 2KB
- 25% ocupado por archivos de 4KB
- 25% ocupado por archivos de 8KB

Para los archivos de 2KB voy a ocupar solo la primera dirección directa, ya que direccionan a bloques de 4KB. De dicho bloque entonces voy a desperdiciar la mitad del espacio.

Para los archivos de 4KB tambien solo se usa la primer indirección, pero esta vez se ocupa la totalidad del bloque.

Para los archivos de 8KB voy a necesitar 2 direcciones directas, por lo que tampoco se desperdicia, ya que con estas 2 obtengo 8KB en bloque de datos.

Luego solo se desperdicia la mitad del 50% del espacio ocupado por archivos de 2KB. Es decir, el 25% del disco (la parte de datos) es desperdiciada.

### c

Tenemos un archivo de `5MB = 5 * 2^20 bytes = 5120 * 2^10 bytes = 5120 KB`
El tamaño en bloques es entonces de `5120 / 4 = 1280`

Dijimos que tenemos 5 direcciones directas, 2 indirectas (que cada una puede direccionar indirectamente a 512 bloques) y 1 doble indirecta. Sumando las direcciones directas y las indirectas podemos direccionar a 1029 bloques, por lo que no alcanza para guardar el archivo entero y debemos utilizar la doble indirección.

Suponiendo que tengo el inodo ya cargado a memoria, la cantidad de bloques que debo acceder para procesar todo el archivo es:
    - 5 de las direcciones directas
    - 2 de las direcciones indirectas
        - 2 * 512, por cada una cargamos sus 512 bloques 
    - 1 del primer nivel de la indirecciones doble
        - 1 del segundo nivel de la indirección doble. Del primer nivel solo vamos a usar la primer entrada ya que con él obtendremos 512 bloques adicionales. Estos sobran, recordando que teníamos 1029 bloques y faltaban 1280 - 1029 = 251.
        - Las primeras 251 bloques de la segunda indirección

En total accedemos a `5 + 2 + 1024 + 1 + 1 + 251 = 1284` bloques