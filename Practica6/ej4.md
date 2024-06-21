Suponiendo que el sistema de archivos tiene inodos con el mismo formato que ext2 entonces tenemos 12 direcciones directas, 1 indirección simple, 1 indirección doble y 1 indirección triple. Y las direcciones de los bloques de disco (LBA) son de 4 bytes 

Tenemos bloques de `4KB`

### a

Tenemos un archivo de `40KB`. Con 10 direcciones simples direccionamos 10 bloques de 4KB, que en total da 40KB.

Luego si suponemos que tenemos el inodo correspondiente cargado en memoria, solo debemos cargar los 10 primeros bloques de la dirección directa.

### b

Ahora si el archivo es de `80KB`, con los primeros 12 direcciones directas solo nos alcanza para 48KB de datos. Necesitamos entonces la primera indirección. Esta puede direccionar a 4KB / 4 = 1024 bloques. Usamos las primeras 8 para los 32KB de datos restantes.

Leimos entonces 12 + 1 + 8 = 21 bloques