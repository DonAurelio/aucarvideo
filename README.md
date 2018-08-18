# aucarvideo

## Prepara tu ambiente de desarrollo

1. Crear la base de datos para el proyecto usando contenedores

Intalar Docker:

```sh
sudo apt-get update
```

```sh
sudo apt-get install docker.io
```

Crea la base de datos usando docker:

```sh
sudo docker run --name aucarvideo_db -e POSTGRES_PASSWORD=postgres -d postgres
```

Verifica que el servidor de base de datos esta corriendo usando el siguiente comando:

```sh
sudo docker ps
```
El comando anterior debería mostrar algo parecido a lo siguiente:

```sh
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
54504cdafc1d        postgres            "docker-entrypoint.s…"   48 seconds ago      Up 41 seconds       5432/tcp            aucarvideo_db
```

Vamos a ver cual es la ip del servidor de base de datos con el siguiente comando:

```sh
sudo docker inspect aucarvideo_db | grep IPAddress
```
Debería salir algo parecido a lo siguiente, donde la IP del servidor de base de datos es 
**172.17.0.2**. Finalmente ésta es la IP que debes indicar a la aplicación en Python para encontrar la base de datos.

```sh
"SecondaryIPAddresses": null,
"IPAddress": "172.17.0.2",
        "IPAddress": "172.17.0.2",
```

2. Descarga el código fuente del proyecto **ubicado en el Escritorio**.

```sh
git clone https://github.com/DonAurelio/aucarvideo.git
```

Entra a la carpeta del proyecto:

```sh
cd aucarvideo
```

2. Crear un ambiente virtual en Python para u proyecto.

Instala el gestor de paquets de Python:

```sh
sudo apt-get install python-pip
```
Instala el ambiente virtual de Python:

```sh
sudo pip install virtualenv
```

Crea un ambiente virtual desarrollo con la versión de Python 3.6

```sh
virtualenv --python=python3.6 .env
```

Verifica que el ambiente se haya creado con el comando **ll**:

```sh
ll
```

Deberia a parcer algo parecido a esto:

```sh
drwxr-xr-x 5 some some 4096 ago 17 21:18 ./
drwxr-xr-x 7 some some 4096 ago 17 20:13 ../
drwxr-xr-x 3 some some 4096 ago 17 21:18 aucarvideo/
drwxr-xr-x 6 some some 4096 ago 17 20:16 .env/
drwxr-xr-x 8 some some 4096 ago 17 21:19 .git/
-rw-r--r-- 1 some some 1203 ago 17 20:15 .gitignore
-rw-r--r-- 1 some some 1868 ago 18 15:10 README.md
```

Verifica que la carpea **.env** este en el salida anterior. Luego activa el ambiente de desarrollo:

```sh
source .env/bin/activate
```

Si el comando anterior funciona bien debería haber cambiado el prompt the to consola:

```sh
some@lightning:~/Desktop/aucarvideo$
(.env) some@lightning:~/Desktop/aucarvideo$
```

Verifica que el archivo **requeriments.txt** este presente en la carpeta del proyecto.

```sh
ls
```

Instala los requerimientos de l apliación:

```sh
pip3.6 install -r requeriments.txt
```

Para correr la aplicación **debes estar dentro del ambiente** usa el comando y además dentro de la carpeta **aucarvideo**.

```sh
./manage.py runserver localhost:8000
```
Entra navegador usando el siguiente link https://localhost:8000.

## Cuando te sientes de desarrollar

1. Descarga la última versión del proyecto.

```sh
git pull origin master
```

2. Inicia la base de datos

```sh
sudo docker start aucarvideo_db
```

3. Verifica que esté corriendo. 

```sh
sudo docker ps
```

4. Inicia la aplicación.

```sh
./manage.py runserver localhost:8000
```

## Cuando hagas algo muy bueno

1. Añade los cambios que hiciste.

```sh
git add -A
```

2. Coloca un pequeño compentario a tus cambios. 

```sh
git commit -m "Un breve comentario"
```

3. Sube los cambios al reposirotio.

```sh
git push origin master
``` 

