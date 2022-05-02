# Metodología para la realización del Trabajo Final

Para realizar esta práctica, en primer lugar he creado un repositorio nuevo en Pontedatos con el nombre de mi usuario de GitHub, “Anabel Cuevas”. Para editarlo desde la terminal, he usado el comando ‘git clone’ para clonar el repositorio en una carpeta nueva de mi ordenador (creada a partir de ‘mkdir’). Esta carpeta es un repositorio git en mi ordenador, en *localhost*, que tiene el mismo contenido que el de la dirección desde donde lo he clonado. Sin embargo, en este repositorio solo hay un README.md vacío. Para copiar aquí todas las prácticas que hemos realizado a lo largo del curso, las tengo que copiar desde mi repositorio personal a este de Pontedatos. Para ello, he usado el comando ‘cp’. Este comando sirve para copiar un documento en un lugar nuevo. A continuación se ofrece un ejemplo:

‘cp /mnt/c/Users/anabe/Desktop/periodismodatos/anabel-cuevas/repositorio-anabelcuevas/practica-1-libre.md /mnt/c/Users/anabe/Desktop/periodismodatos/practicafinal/AnabelCuevas’

Después de ‘cp’ se encuentra la dirección del archivo que quiero copiar en la nueva carpeta, y después del espacio se encuentra la dirección de la carpeta “AnabelCuevas”, donde tengo enlazada la carpeta de GitHub. 

Antes de reunir las prácticas en esta carpeta, es necesario borrar el README.md creado anteriormente para que pueda ser sustituido por el README.md ya existente en mi repositorio personal. Para ello, usamos el comando ‘rn’ (rm README.md). 

Una vez reunidas las prácticas en esta carpeta, hay que actualizar los cambios en GitHub. Para ello, son necesarios varios comandos. En primer lugar ‘git status', para conocer los archivos que tenemos en el ordenador pero no en GitHub. A continuación es necesario ‘git add .’ para añadir todos los elementos nuevos al repositorio. Para darle un nombre a este cambio, se escribe ‘git commit -m “cambio1”’. Ahora con ‘git pull’ se actualiza de modo remoto el cambio. Finalmente con ‘git push’ se suben los cambios a GitHub (después de introducir el nombre y el token). 

Una vez comprobado en GitHub que los cambios se han hecho con éxito, en la sección de Settings del repositorio se activa la opción de Pages de GitHub, que permitirá crear una página web. 

El archivo README.md es el que GitHub emplea como index.html, es decir, lo que se ve al entrar en la página que se ha creado. Al solo verse el texto del README, es necesario enlazar el resto de prácticas para que estas puedan ser fácilmente accesibles. Para ello, se edita este README desde la terminal mediante nano empleando lenguaje markdown (una vez editado, se actualiza desde la terminal para que los cambios se vean reflejados en GitHub). 
