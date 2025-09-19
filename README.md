# Programacion de servicios y procesos
## Tarea:  Ejecucion y comprension de procesos en linux
## Alumno: Romén Gilberto García Gómez

En el siguiente archivo se han omitido los acentos para facilitar traducciones.

### BLOQUE 1: Conceptos basicos (Teoria)
#### 1. Define que es un proceso y en que se diferencia de un programa.
```
Un proceso es un programa en ejecucion con recursos asignados. El programa es un codigo estatico y el proceso es su propia ejecucion activa.
```

#### 2. Explica qué es el kernel y su papel en la gestión de procesos.
```
El kernel es el nucleo del sistema operativo, gestiona procesos y coordina el enlace entre hardware y software
```

#### 3. ¿Qué son PID y PPID? Explica con un ejemplo.
```
RESPUESTA
```

#### 4. Describe qué es un cambio de contexto y por qué es costoso.
```
RESPUESTA
```

#### 5. Explica qué es un PCB (Process Control Block) y qué información almacena.
```
RESPUESTA
```

#### 6. Diferencia entre proceso padre y proceso hijo.
```
RESPUESTA
```

#### 7. Explica qué ocurre cuando un proceso queda huérfano en Linux.
```
RESPUESTA
```

#### 8. ¿Qué es un proceso zombie? Da un ejemplo de cómo puede ocurrir.
```
RESPUESTA
```

#### 9. Diferencia entre concurrencia y paralelismo.
```
RESPUESTA
```

#### 10. Explica qué es un hilo (thread) y en qué se diferencia de un proceso.
```
RESPUESTA
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
