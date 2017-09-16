### Taller 3
**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Docente:** Daniel Barragán C.
**Estudiante:** Alejandro Bueno Cardona - A00335472
**Tema:** Llamadas al sistema (syscalls)  
**Correo:** daniel.barragan at correo.icesi.edu.co


### Objetivos
* Conocer y explicar la función de las llamadas al sistema en un sistema operativo

### Prerrequisitos
* Virtualbox o WMWare
* Máquina virtual con sistema operativo CentOS7
* Aplicativo strace

### Descripción
El tercer taller del curso sistemas operativos trata sobre las llamadas al sistema y su importancia para el sistema operativo

### Actividades

1. Empleando el aplicativo **strace** obtenga 5 llamadas al sistema para uno o varios comandos de linux. Explique por qué los comandos seleccionados emplean las llamadas al sistema encontradas, para ello debe emplear los manuales de Linux en Internet o del sistema operativo (comando **man**). Debe incluir la explicación de los parámetros que reciben las llamadas al sistema encontradas. Consigne capturas de pantalla donde muestre las llamadas al sistema obtenidas (sugerencia: emplear -etrace para filtrar los resultados)

**Comando:** ls

| Syscall | Uso en ls | Parámetros | 
|---|---|---|
| execve | Ejecuta el programa asociado (ls) | **filename:** Nombre del programa a ejecutar, debe ser binario ejecutable . **argv:** Arreglo de strings pasados al programa, el primero suele ser el filename asociado. **envp:** Arreglo de strings con formato key=vaulue, pasados como ambiente al programa. |
| openat | Abrir el directorio actual | **dirfd:** Descriptor de diretorio. Si directorio es relativo = AT_FDCWD. **pathname:** Dirección de directorio objetivo. **flags:** Flags para indicar el procesamiento del directotrio, por ejemplo, O_DIRECTORY indica que quiere abrir y ver su contenido. |
| getdents | Leer el contenido del directorio abierto por openat | **fd:** File descriptor que retorna openat. **dirp:** Id del buffer de lectura del directorio. **count:** Tamaño del buffer. |
| close | Cerrar el directorio | **fildes:** File descriptor del directorio a cerrar. |
| munmap | Eliminar dirección en memoria | **addr:** Dirección de memoria. **len:** Tamaño en memoria. |


2. Realice la compilación del código fuente adjunto y su ejecución empleando el aplicativo **strace**. Identifique las llamadas al sistema encargadas de enviar y recibir datos a través de la red. A partir de los manuales de Linux en Internet o del sistema operativo explique las llamadas al sistema encontradas y sus parámetros.



## Referencias

* http://man7.org/linux/man-pages/man2/syscalls.2.html  
* https://jvns.ca/blog/2014/09/18/you-can-be-a-kernel-hacker/
