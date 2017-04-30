---
layout: post
title: 01 Concepto
date: dg 30 abr 2017 16:34:25 CEST 
---


# 00 Definición #

**Git** es un software de control de versiones diseñado por *Linus Torvalds* , pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente.

Se llama **control de versiones** a la gestión de los diversos cambios que se realizan sobre los elementos de algún producto o una configuración del mismo. Una versión, revisión o edición de un producto, es el estado en el que se encuentra el mismo en un momento dado de su desarrollo o modificación.

# 01 Características #

Un sistema de versiones debe proporcionar:

- Un mecanismo de almacenamiento
- Posibilidad de realizar cambios
- Registro histórico

Terminología:

- **repositorio**: lugar en el que se almacenan los datos actualizados e históricos de cambios, a menudo en un servidor.
- **módulo**: conjunto de directorios y/o archivos dentro del repositorio que pertenecen a un proyecto común.
- **version**: revisión determinada de la información que se gestiona.
- **tag**: etiqueta con el fin de clasificar el contenido para encontrarlo más rápidamente.
- **baseline**: línea base, revisión aprobada de un documento o fichero fuente, a partir del cual se pueden realizar los cambios siguientes.
- **branch**: rama o bifurcación en un instante de tiempo determinado la cual se desarrolla de forma independiente.
- **merge**: mezcla de ramas de código desarrollado con diferencias.
- **checkout**: despliegue, suele utilizarse para crear ramas nuevas.
- **conflicto**: ocurre cuando hay diferencias entre los archivos y el sistema no está programado para decidir qué parte del código debe dar por bueno.
- **resolver**: intervención manual para solucionar un conflicto.
- **changuelist**: lista de cambios
- **export**: similar a *checkout*. Crea un árbo de directorios limplio sni metadatos de control de versiones presentes en la copia de trabajo, que se encuentran en el directorio `.git`.
- **import**: acción de copia de un árbol de directorios local en el repositorio por primera vez.
- **integración**: puede ser por *fusión* o *merge* o por *integración inversa* para fundir ramas diferentes en el tronco o *trunk* principal.
- **sync**: actualización.
- **workspace**: copia local de los ficheros de un repositorio. Conceptualmente es un *cajón de arena* o `sandbox`.
- **congelar**: permitir los últimos commits para resolver buggs y suspender cualquier otro antes de la entrega.


# 02 Formas de colaborar #

Para colaborar debemos **clonar** el repositorio ya creado para disponer de una **copia local**.

## 1 De forma exclusiva ##

Esquema para poder realizar un cmbio en el que es necesario comunicar al repositorio el elemento que se desea modificar y el sistema se encargará de impedir que otro usuario pueda modificar dicho elemento. Una vez hecha la modificación se comparte al resto de colaboradores.

## 2 De forma colaborativa ##

Esquema en el que cada usuario modifica la copia local y cuendo el usuario decide compartir los cambios el sistema automáticamente intenta combinar las diversas modificaciones.

Suelen aparecer conflictos e inconsistencias que se deben solucionar de forma manual.


# 03 Arquitecturas de almacenamiento ##

- **Distribuidos**: cada usuario tiene su propio repositorio. Los repositorios puede intercambiar y mezclar revisiones. Es frecuente el uso de un repositorio en un servidor contra el que se sincronizan las copias locales.
- **Centralizados**: existe un repositorio centralizado de todo el código, del cual es responsable un único usuario (o conjunto de ellos) Se facilitan las tareas administrativas a cambio de reducir flexibilidad, pues todas las decisiones fuertes, como crear una nueva rama, necesitan la aprobación del responsable.


# 04 Tipos de ramas #

- **Master**: rama principal. Contiene el repositorio principal en producción, por lo que debe estar estable.
- **Development**: rama sacada de master. Es la rama de integración, todas las nuevas funcionalidades se deben integrar en esta rama. Cuando se realicen las integraciones y se corrijan los errores se mezclará con la rama *master*.
- **Features**: cada nueva funcionalidad se debe realizar en una rama nueva, especificada para esa funcionalidad. Se deben sacar de la rama `development`.
- **Hotfix**: los bugs que surgen en producción, por lo general se deben arreglar y publicar de forma urgente. Se sacan de la rama *master*. Una vez corregido el error se mezcal sobre la rama *master*.

