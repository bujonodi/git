---
layout: post
title:  "02 Configurar entorno local para trabajar con Github"
date:   2017-05-01 13:47:00 +0200
---

# 01 Generar claves SSH #

Comprueba si tienes alguna **clave SSH** generada:

```
ls -l ~/.ssh
```

Las claves SSH se guardan en pares (una clave privada y una pública). Las dos deben tener el mismo nombre, solo que la pública debe acabar en `.pub`.

Si al ejecutar el comando anterior compruebas que ya tienes una clave creada, puedes saltarte lo que queda de esta sección y pasar a añadir dicha clave a tu cuenta de Github.

Si no tienes alguna clave creada puedes crear una ejecutando este comando:

```
ssh-keygen
```

En este momento te pedirá una serie de datos, que puedes omitir para que tome unos valores por defecto si pulsas `enter` en cada pregunta.

Para comprobar que las claves se han generado correctamente vuele a ejecutar:

```
ls -l ~/.ssh
```

o si has guardado las claves en otro directorio:

```
ls -l /path/directorio/claves
```

y podrás ver los dos ficheros de las claves.


# 02 Asignar las claves SSH a tu cuenta de Github #

Accede a tu cuenta de Github y entra en la configuracción (settings)

![Accede a settings](/img/02-01-seleccionar-settings.png  "accede a settings")

En el menú de la izquierda, entra en `SSH and GPG keys`

![Accede a SSH and GPG keys](/img/02-02-seleccionar-ssh-and-gpg-keys.png  "Accede a SSH and GPG keys")

Ahora pulsa sobre `New SSH key`

![Click en New SSH key](/img/02-03-click-on-new-ssh-key.png  "Click en New SSH key")

En el formulario que se te ha abierto, escribe un título para la clave, y en el apartado `key` tienes que pegar el contenido del fichero `.pub` que generaste en el apartado anterior. Para ello puedes abrir el fichero con cualquier editor de texto y copiar el contenido.

Pulsa sobre `Add SSH key` y ya está todo hecho.

![Pulsa en add SSH key](/img/02-04-copy-and-paste-public-key.png  "Pulsa en add SSH key")


# 03 Comprobar que la operación se ha realizado bien #

Ejecuta el siguiente comando desde la terminal

```
ssh -T git@github.com
```

y como respuesta te debe salir algo similar a ésto:

![Respuesta comando de comprobacion](/img/02-05-comando-realizado-correctamente.png  "Respuesta comando de comprobacion")
