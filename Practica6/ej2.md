Capacidad disco = `128 GB = 128 * 2^30 Bytes`
Tamaño del bloque = `8 KB = 8 * 2^10 Bytes`
entrada de la FAT = `24 bytes`

### a

Cantidad de bloques en disco= `128 GB / 8 KB = 128 * 2^30 Bytes / 8 * 2^10 = 16 * 2^20`

Tamaño tabla = `Cantidad de bloques * tamaño entrada = 16 * 2^20 * 24 = 384 * 2^20 = 384 MB`


### b
Voy a suponer que la estructura del file system es la FAT y el espacio de datos.

Tamaño tabla en bloques = `384 * 2^20 / 8 * 2^10 = 48 * 2^10`
Tamaño espacio datos en bloques = `16 * 2^20 - 48 * 2^10 = 16336 * 2^10`
Cantidad de bloques que ocupa archivo de 10 MB = `10 * 2^20 / 8 * 2^10 =  5/4 * 2^10`

Cantidad de archivos de 10MB que entran en el espacio de datos = `16336 * 2^10 / 5/4 * 2^10 = floor(16336 * 4/5) = 13068`

### c

Ocupa 7 bloques. Cada bloque es de 8 KB, por lo que ocupa 56 KB