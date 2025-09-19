# Programacion de servicios y procesos
## Tarea:  Ejecucion y comprension de procesos en linux
## Alumno: Romén Gilberto García Gómez

En el siguiente archivo se han omitido los acentos para facilitar traducciones.

### BLOQUE 1: Conceptos basicos (Teoria)
#### 1. Define que es un proceso y en que se diferencia de un programa.
```
Un proceso es un programa en ejecucion con recursos asignados. El programa es
un codigo estatico y el proceso es su propia ejecucion activa.
Fuente: GeeksforGeeks
```

#### 2. Explica qué es el kernel y su papel en la gestión de procesos.
```
El kernel es el nucleo del sistema operativo, gestiona procesos y coordina el
enlace entre hardware y software.
Fuente: LearnLinux.org.za
```

#### 3. ¿Qué son PID y PPID? Explica con un ejemplo.
```
PID: Procces ID: identificador unico de un proceso.
PPID: Parent Proccess ID: identificador del proceso padre de un proceso hijo.
EJEMPLO: Si ejecutas bash (PID 100) y con el lanzas python (PID 120), entonces el PPID de
python será 100.
Fuente: StackOverflow
```

#### 4. Describe qué es un cambio de contexto y por qué es costoso.
```
Un cambio de contexto es cuando la CPU guarda el estado de un proceso en un punto actual, y
luego se ejecuta otro. Esto puede resultar costoso porque implica tener que guardar y restaurar
registros.
Fuente: Delightly Linux
```

#### 5. Explica qué es un PCB (Process Control Block) y qué información almacena.
```
Es la estructura de datos donde el SO guarda informacion del estado de un proceso.
Fuente: Delightly Linux
```

#### 6. Diferencia entre proceso padre y proceso hijo.
```
El proceso padre crea al proceso hijo, el cual hereda parte de los recursos del padre.
Fuente: GeeksforGeeks
```

#### 7. Explica qué ocurre cuando un proceso queda huérfano en Linux.
```
Pasa a ser "adoptado" por el proceso 'init', el cual lo gestiona ahora.
Fuente: El documento de Pearson Higher Education
```

#### 8. ¿Qué es un proceso zombie? Da un ejemplo de cómo puede ocurrir.
```
Es un proceso hijo que ya finalizo, pero su padre no ha leido que ha terminado, asi que
sigue en la lista de procesos.
EJEMPLO: Un hijo finaliza, pero el padre no ejecuta wait(), asi que queda como zombi
Fuente: Wikipedia
```

#### 9. Diferencia entre concurrencia y paralelismo.
```
CONCURRENCIA: Ejecutar varios procesos por turnos, usando un solo procesador.
PARALELISMO: Ejecutarlos al mismo tiempo usando varios procesadores.
Fuente: GeeksforGeeks
```

#### 10. Explica qué es un hilo (thread) y en qué se diferencia de un proceso.
```
Es la unidad basica de ejecucion de un proceso.
Su diferencia con un proceso es que comparte memoria y recursos con el resto de hilos del
mismo proceso, en cambio, los procesos son independientes.
Fuente: Wikipedia
```


### BLOQUE 2: Practica con comandos en Linux
#### 11. Usa echo $$ para mostrar el PID del proceso actual.
Comando:
```
echo $$
```
Output:
```
67605
```

#### 12. Usa echo $PPID para mostrar el PID del proceso padre.
Comando:
```
echo $PPID
```
Output:
```
70384
```

#### 13. Ejecuta pidof systemd y explica el resultado.
Comando:
```
pidof systemd
```
Output:
```
3397
```
Explicacion:
```
Devuelve el ID del proceso systemd (Proceso principal de la maquina, se encarga del arranque del sistema).
```

#### 14. Abre un programa grafico y usa pidof para obtener sus PID.
Comando:
```
TODO
```
Output:
```
TODO
```

#### 15. Ejecuta ps -e y explica que significan sus columnas
Explicacion:
```
Se ven los procesos que se ejecutan en el sistema y su estado actual.
```

#### 16. Ejecuta ps -f y observa la relacion entre procesos padre e hijo.
Explicacion:
```
Tienen igual tiempo.
```

#### 17. Usa ps -axf o pstree para mostrar el árbol de procesos y dibujalo.
Comando:
```
pstree
```

#### 18. Ejecuta top o htop y localiza el proceso con mayor uso de CPU.
Comando:
```
htop
```
Proceso:
```
/usr/lib/firefox/firefox (0.6%)
```

#### 19. Ejecuta sleep 100 en segundo plano y busca su PID con ps.
PID:
```
75550
```

#### 20. Finaliza un proceso con kill y comprueba con ps que ya no esta.
Comando:
```
kill firefox
```


### BLOQUE 3: Procesos y jerarquia
#### 21. Identifica el PID del proceso init/systemd y explica su funcion.
PID:
```
3397
```
Explicacion:
```
Proceso principal de la maquina, se encarga del arranque del sistema.
```

#### 22. Explica que ocurre con el PPID de un proceso hijo si su padre termina antes.
Respuesta:
```
El hijo se convierte en un proceso huerfano y su PPID se reasigna al proceso init.
```

#### 23. Ejecuta un programa que gener evarios procesos hijos y observa sus PIDs con ps.
```
TODO
```

#### 24. Haz que un proceso quede en estado suspendido con ```Ctrl+Z``` y renaudalo con ```fg```.
Comandos:
```CTRL>Z```
```fg```
Explicacion:
```
Se suspende y se renauda el proceso
```

#### 25. Lanza un proceso en segundo plano con & y observalo con jobs.
Comando:
```
firefox &
```
Output:
```
[2] 25166
[1]   Salida 127              prueba
```
Comando para visualizar el proceso:
```
jobs
```
Salida:
```
[3]+  Hecho                   firefox
```

#### 26. Explica la diferencia entre los estados de un proceso: Running, Sleeping, Zombie, Stopped
Respuesta:
```
RUNNING: Se esta ejecutando en la CPU y esta atcivo.
SLEEPING: No se esta ejecutando directamente, pero esta esperando a que suceda algo o que se
libere espacio para despertar.
ZOMBIE: El proceso ha terminado su ejecucion pero su padre no lo ha leido, por lo que sigue
saliendo en la tabla de procesos.
STOPPED: El proceso esta cerrado y finalizado.
```

#### 27. Usa ps -eo pid,ppid,stat,cmd para mostrar los estados de varios procesos.
Comando:
```
ps -eo pid,ppid,stat,cmd
```
Output:
```
Listado de procesos
```

#### 28. Ejecuta watch -n 1 ps -3 y observa como cambian los procesos en tiempo real.
Comando:
```
watch -n 1 ps -3
```

#### 29. Explica la diferencia entre ejecutar un proceso con & y con nohup.
Respuesta:
```
Al ejecutar un comando con & se ejecuta en segundo plano y se queda ligado a la sesion actua,
por lo que si cierras la terminal se cerrara el proceso. Y con nohup se hará en primer plano
y ligado al sistema, por lo que si cerramos sesion podra seguir ejecutandose
```

#### 30. Usa ulimit -a para ver los limites de recursos de procesos en tu sistema.
Comando:
```
ulimit -a
```
Output:
```
real-time non-blocking time  (microseconds, -R) unlimited
core file size              (blocks, -c) 0
data seg size               (kbytes, -d) unlimited
scheduling priority                 (-e) 0
file size                   (blocks, -f) unlimited
pending signals                     (-i) 125413
max locked memory           (kbytes, -l) 4026308
max memory size             (kbytes, -m) unlimited
open files                          (-n) 1024
pipe size                (512 bytes, -p) 8
POSIX message queues         (bytes, -q) 819200
real-time priority                  (-r) 0
stack size                  (kbytes, -s) 8192
cpu time                   (seconds, -t) unlimited
max user processes                  (-u) 125413
virtual memory              (kbytes, -v) unlimited
file locks                          (-x) unlimited
```
Explicacion:
```
Vemos los limites de los procesos del sistema, algunos tienen su limite marcado, otros estan marcados
como ilimitados.
```
