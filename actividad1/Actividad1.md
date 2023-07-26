# Tipos de Kernel

## Monolitico: 
### Es un kernel grande que contiene todas las tareas y por ende es el único responsable de la gestión de la memoria y de los procesos. Es un núcleo grande y complejo la cual permite que se integren nuevos módulos.
<br>

## Microkernel: 
### Este se ha diseñado de un tamaño relativamente pequeño con el objetivo de presentarse algún fallo el sistema operativo este no falle por completo, por lo que este a su vez esta dividido en varios módulos.
<br>

## Hibrido: 
### Esta es la mezcla entre monolítico y microkernel, dentro de los cuales tienen las mismas ventajas de ambos kerneles con la diferencia que el Hibrido puede ser modular, llevando a este kernel a ser mas eficiente y rápido.
<br>

## Exonúcleos: 
### Estos utilizan bibliotecas para su funcionamiento, por lo que funcionan perfecto al momento de realizar muchas funcionalidades, esto debido a que tienen acceso directo hacia el hardware del sistema.
<br>

# Diferencias

Kernel | Diferencias
:--- | :---
`Monolitico` | -	No se puede modularizar. <br> -	Los procedimientos son visibles. <br> -	Pueden cargarse más módulos.
`Microkernel` | -	Se pueden agregar módulos más pequeños. <br> -	Se puede modularizar.
`Hibrido` | -	Utiliza lo mejor de ambos kenels anteriores. <br> - Ofrece un equilibrio entre el rendimiento y la seguridad.
`Exokernel` | -	El usuario puede agregar bibliotecas para el rendimiento. <br> -	Pueden agregarse módulos creados por terceros.
<br>


# Modo Usuario vrs Modo Kernel

Modo Usuario | Modo Kernel
| :--- | :--- |
Tiene el modo restringido a la interfaz de llamadas al sistema | Tiene acceso ilimitado al hardware
Puede producirse errores en modo usuario y el sistema se recuperará mediante el modo Kernel. | Si se produce un error en modo kernel puede hacer caer todo el sistema.
Se conoce también como modo sin privilegios, modo restringido o modo esclavo | Se conoce como modo maestro, modo privilegiado o modo sistema.
Todos los procesos tienen un espacio de direcciones separados | Todos los procesos comparten un único espacio de direcciones.
Las aplicaciones tienen menos privilegios | Las aplicaciones tienen mas privilegios 
Debe de acceder a los programas del kernel ya que contiene restricciones | No hay restricciones para acceder a los programas.
Solo puede hacer referencias a la memoria asignada para el modo usuario | Puede hacer referencia a ambas áreas de la memoria.


