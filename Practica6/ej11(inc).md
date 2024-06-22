```c
struct Ext2FSDirEntry {
    unsigned int inode ;
    unsigned short record_length;
    unsigned char name_length;
    unsigned char file_type ;
    char name[ ] ;
};
struct Ext2FSInode {
    unsigned short mode; // info sobre el tipo de archivo y los permisos
    unsigned short uid ; // id de usuario
    unsigned int size ; // en bytes
    unsigned int atime;
    unsigned int ctime;
    unsigned int mtime; // fecha ultima modificacion
    unsigned int dtime;
    unsigned short gid ; // id de grupo
    unsigned short links_count; // cantidad de enlaces al archivo
    unsigned int blocks ;
    unsigned int flags ;
    unsigned int os_dependant_1;
    unsigned int block [ 1 5];
    unsigned int generation ;
    unsigned int file_acl ;
    unsigned int directory_acl ;
    unsigned int faddr ;
    unsigned int os_dependant_2[ 3];
};

// dado el id de un usuario , devuelve el nombre del usuario .
char ∗ nombre_propietario(unsigned short id_usuario)

// dado un path , devuelve su inodo
struct Ext2FSInode ∗ Ext2FS::inode_for_path(const char ∗ path)

// dada una direccion de bloque y un buffer , carga el bloque indicado en el buffer
void Ext2FS::read_block(unsigned int block_address , unsigned char ∗ buffer )

// dados un inodo y un numero de bloque , recorre el inodo buscando la direccion del bloque de datos indicado
unsigned int Ext2FS::get_block_address(struct Ext2FSInode ∗ inode , unsigned int block_number)

// dado un numero de inodo , busca el inodo en el grupo y lo devuelve
struct Ext2FSInode ∗ Ext2FS::load_inode(unsigned int inode_number)
```

```c
// ejercicio b
struct archivo {
    char *type;    
    char *propietario;
    unsigned int size; // en bytes
    unsigned int mtime; // fecha ultima modificacion
};

// ejercicio a

// toma path de un directorio, una cantidad de bytes, un nombre
// devuelva una lista con todos los archivos que tengan un tamaño menor a min_bytes, 
// cuyo nombre sea arch_nombre, a partir de dir (inclusive). La búsqueda deberá también considerar
// los subdirectorios del directorio dado (excepto ’.’ y ’..’).

// asumo que el path empieza en root
vector<archivo> find_file_less_size(char * dir, int min_bytes, char *arch_nombre) {

    queue<*Ext2FSInode> q;
    // cargo el inodo del directorio pasado por path y lo agrego a una cola
    q.push(Ext2FS::inode_for_path(dir))

    // desencolo un directorio mientras haya elementos en la cola 
    while (!q.empty()) {
        // recorro todas sus dentries
        Ext2FSInode inodo = q.pop();

        // uso la información del tamaño del archivo para ver cuantos bloques hay. Asumo block size de 4KB (si no se obtiene el dato del superblock)
        cant_bloques_inodo = (inodo.size \ 4096) + 1;

        // asumo que no hay ninguna dentry más grande que 1 bloque.
        // por lo que cargo de a 2 bloques para leer dentries

        char *bloque1;
        char *bloque2;

        for (int i = 0; i < cant_bloques_inodo-1; i++) {
            read_block(get_block_address(inodo,i), bloque1);
            read_block(get_block_address(inodo,i+1), bloque2);

            

        }


        // si encuentro un archivo, chequeo el nombre y el tamaño

            // si corresponde agrego a la estructura de salida

        // si encuentro un directorio agrego su inodo a la cola

    }
}
```