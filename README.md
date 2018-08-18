# aucarvideo

## Desarrollar

1. Crear la base de datos para el proyecto usando contenedores

Intalar Docker:

```sh
sudo apt-get update
```

```sh
sudo apt-get install docker
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

1. Abre la terminal ubicado en el escritorio usando **Ctrl+Alt+T**.
2. Descarga el proyecto usando el siguiente comando.

```sh
git clone https://github.com/DonAurelio/aucarvideo.git
```
3. Entra a la carpeta del proyecto usando el siguiente comando

```sh
cd aucarvideo
```





