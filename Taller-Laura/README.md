PASOS REALIZADOS PARA LA SOLUCIÓN DEL TALLER

1. Inicialización de un repositorio Git:

   $ git init Taller-Laura

   - Se crea un repositorio Git vacío en la carpeta `Taller-Laura`.

2. Configuración del nombre de usuario y correo electrónico:
   
   $ git config --global user.name "Laura"
   $ git config --global user.email "laura.ricarde@correounivalle.edu.co"
   
   - Configura el nombre y el correo que Git asociará a los commits a nivel global (en todo el sistema).

3. Intento de cambiar a una nueva rama antes de entrar en el repositorio:
   
   $ git checkout -b feature
   
   - Falla porque el comando `checkout` se intentó ejecutar en un directorio que no es un repositorio de Git.

4. Cambiar al directorio correcto:
   
   $ cd Taller-Laura

   - Cambia al directorio `Taller-Laura` donde ya se había inicializado el repositorio Git.

5. Creación de una nueva rama:
   
   $ git checkout -b feature
   
   - Se crea y se cambia a la rama `feature`.

6. Crear un archivo y añadir contenido:
   
   $ echo "Texto inicial"> archivo.txt

   - Crea el archivo `archivo.txt` con el contenido "Texto inicial".

7. Añadir el archivo al área de preparación (staging):
   
   $ git add archivo.txt
   
   - Añade el archivo `archivo.txt` al área de staging, lista para el commit. Se muestra una advertencia sobre la conversión de finales de línea.

8. Primer commit:
   
   $ git commit -m "Commit inicial"
   
   - Guarda los cambios en la historia de Git con el mensaje "Commit inicial".

9. Modificación del archivo:
   
   $ echo "Texto agregado en feature" >> archivo.txt
   
   - Añade texto adicional al archivo `archivo.txt`.

10. Segundo commit:
    
    $ git commit -am "Segundo commit en feature"

    - Añade y confirma los cambios del archivo `archivo.txt` con el mensaje "Segundo commit en feature".

11. Tercer commit:
    
    $ echo "Nuevo texto agregado" >> archivo.txt
    $ git commit -am "Tercer commit en feature"
    
    - Se agrega más contenido y se realiza un nuevo commit.

12. Cambio a la rama `master`:
    
    $ git checkout master
    
    - Hubo un error porque la rama `master` no existía, por lo que se crea una nueva rama llamada `master`:
    
    $ git checkout -b master
    

13. Fusionar la rama `feature` en `master`:

    $ git merge feature

    - Se intenta fusionar, pero no hay cambios nuevos que fusionar.

14. **Revertir el último commit en `master`**:
    
    $ git reset --hard HEAD~1

    - Se deshace el último commit y se restablece el estado del repositorio al commit anterior.

15. Rebase de la rama `feature` en `master`:
    
    $ git rebase feature
    
    - Aplica los commits de la rama `feature` encima de `master`.

16. Creación de una nueva rama `hotfix` para corregir errores:
    
    $ git checkout -b hotfix
    
    - Se cambia a una nueva rama `hotfix` para hacer una corrección urgente.

17. Commit del hotfix:

    $ echo "Corrección urgente" >> archivo.txt
    $ git commit -am "Hotfix"

    - Se hace un commit con la corrección urgente.

18. Aplicar el `hotfix` a la rama `master` mediante cherry-pick:

    $ git cherry-pick hotfix

    - Aplica los cambios del commit `hotfix` en `master` sin fusionar toda la rama.

19. Generación de un conflicto de fusión:
    - En la rama `feature`:
    
    $ echo "Cambio en feature" > conflicto.txt
    $ git commit -am "Cambio en feature"

    - En la rama `master`:

    $ echo "Cambio en master" > conflicto.txt
    $ git commit -am "Cambio en master"

    - Luego, al intentar fusionar:
    
    $ git merge feature

    - Se produce un conflicto en el archivo `conflicto.txt`.

20. Resolución de conflictos:
    
    $ code conflicto.txt

    - Se abre el archivo en un editor para resolver manualmente el conflicto.

21. Confirmar la resolución del conflicto:
    
    $ git add conflicto.txt
    $ git commit -m "Corrección conflicto en conflicto.txt"
    

22. Crear un archivo `README.md`:
    
    $ touch README.md
    $ code README.md

    - Crea el archivo `README.md` y lo abre en un editor.

Este flujo demuestra cómo se trabaja con ramas, commits, fusiones, cherry-pick y cómo resolver conflictos en Git.

El conflicto se resolvió de la siguiente manera:

1. Detectar el conflicto: Al intentar fusionar las ramas `feature` y `master`, Git detectó que ambas modificaron el archivo `conflicto.txt`, causando un conflicto.

2. Abrir el archivo con conflicto: Laura abrió el archivo `conflicto.txt` en un editor, donde Git marcó las diferencias entre las dos ramas.

3. Resolver el conflicto manualmente: Editó el archivo para decidir cómo combinar los cambios de ambas ramas, eliminando las marcas de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`).

4. Guardar y agregar el archivo: Guardó los cambios y usó `git add` para marcar el archivo como resuelto.

5. Hacer commit: Finalmente, hizo un commit con un mensaje describiendo la resolución del conflicto. 

Así, la fusión fue completada correctamente.