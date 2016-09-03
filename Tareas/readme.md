# Tareas Cortas 

| Tarea        | Descripción |
| ------------- |-------------|
|1 | Leer el capítulo 1 del libro "Mining of Massive Data Sets", y resolver los ejercicios 1.2.1, 1.3.1 y 1.3.2 de dicho capítulo.|
|2 | Ejercicios del cápitulo 2. 2.3.1, 2.3.2, 2.3.5      |  
|3 | Ejercicios 3.2.1, 3.2.2, 3.2.3, 3.3.1, 3.3.2, 3.3.3, 3.3.5, y 3.3.7 del libro Mining of Massive Data Sets   | 

# Tareas Programadas 

## Tarea 1 

__Introducción__ 

Las tablas de hash distribuidas son la base de todo sistema de recuperacion de información en Grid que debe garantizar acceso rápido sobre un conjunto grande de datos distribuidos sobre un conjunto de servidores que puede estar variando constantemente. Son la
base de BigTable, Bitorrent, HBase y muchos mas.

En esta tarea se aprenden los algoritmos básicos de tablas de hash distribuidas utilizando el lenguaje de programacion Erlang. 

__Especificación de la tarea__

Basado en el artículo visto en clase _CHORD: a scalable peer to peer lookup protocol for internet applications_. Usted debe programar un módulo en erlang que impemente un _key-value store_ distribuido utilizando dicho protocolo. Para ello el modulo debe tener las siguientes funciones:

```
startRing(Nodo, Nombre, RingSize, PollingSecs, SuccessorCount)
% iniciativa el anillo de procesos que forman parte del CHORD,
% RingSize es una potencia de 2.
starProc(Nodo, Nombre, NodoStart, NombreStart)
% el nombre de cada proceso debe ser unico dentro de cada nodo.
stopProc(Nodo, Nombre)
% para e l proceso, actualiza las tablas de los demas
killProc(Nodo, Nombre)
% para el proceso sin actualizar tablas (el proceso se cae)
addKeyValue(Nodo, Nombre, LLave, Valor) -> ok | error
% agrega una llave en el anillo
delKey(Nodo, Nombre, Llave) -> ok | error
getValue(Nodo, Nombre, Llave) -> Valor
```

* El programa debe correr en una sesión de Erlang distribuido, para ello debe correr cada máquina virtual con el comando con valores apropiados para el nombre y el cookie.
```
>erl -name <nombre>-setcookie <cookie>
```
* Cada nodo debe registrar los procesos que corren utilizando la funcion de erlang `erlang:hash/2` y la función `register`
* Los nodos deben implemenar polling para revisar periodicamente que no se hayan caído miembros del anillo Chord.
* Debe implementar algun tipo de redundancia en el algoritmo tal que se permite recuper de fallas como la muerte repentina de un nodo.
* El número de identificación del proceso (su ubicación dentro de anillo) se obtiene haciendo un hash de la lista que contiene `[nodo, nombre]`.

__Evaluación__

* 05 % Documentación
* 75 % Funcionalidad
* 25 % Correctitud del programa
 
__FECHA DE ENTREGA: _9 DE SETIEMBRE___

