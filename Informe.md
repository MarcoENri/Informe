# Práctica Servidor Web en Docker Playground Marco Enriquez

## 1. Título
Práctica servidor web en Docker Playground.

## 2. Tiempo de duración
Duración estimada: 8 minutos.

## 3. Fundamentos

Docker es una plataforma que permite la creación y gestión de contenedores. Un contenedor es una unidad ligera y ejecutable de software que incluye todo lo necesario para ejecutar una aplicación, como el código, las bibliotecas y las dependencias. A diferencia de las máquinas virtuales tradicionales, los contenedores comparten el sistema operativo del host, lo que los hace más eficientes en términos de recursos.

En esta práctica, se utilizará Docker Playground, una herramienta que permite ejecutar contenedores de Docker en línea sin necesidad de instalar software en el equipo local. El objetivo es levantar un servidor web Nginx dentro de un contenedor y configurar una página web básica. Nginx es un servidor web y proxy inverso de alto rendimiento, utilizado comúnmente para servir contenido estático y manejar grandes cantidades de tráfico.

Para realizar esta práctica, se utilizarán comandos básicos de Docker como `docker run`, que permite ejecutar un contenedor, y `docker exec`, que permite interactuar con un contenedor en ejecución. Además, se configurarán archivos dentro del contenedor, como el archivo `index.html` que será servido por Nginx.

![Captura de pantalla 2024-10-14 091452](https://github.com/user-attachments/assets/d433a844-9d46-485b-888c-8b8df7537511)


## 4. Conocimientos previos

Para realizar esta práctica, el estudiante debe tener conocimientos en:

- Comandos básicos de Linux, como `cd`, `ls`, `echo`, etc.
- Navegación en terminal y manejo de archivos.
- Conocimiento básico sobre contenedores y el uso de Docker.
- Uso de un navegador web para acceder a Docker Playground.

## 5. Objetivos a alcanzar

- Implementar contenedores utilizando Nginx.
- Manipular archivos de configuración dentro de un contenedor.
- Levantar un servidor web y servir una página estática desde un contenedor de Docker.

## 6. Equipo necesario

- Computador con acceso a internet.
- Un navegador compatible (Google Chrome, Firefox, etc.).
- Cuenta en Docker Playground (play-with-docker.com).
- Docker versión 20.x o superior (si se realiza de forma local).

## 7. Material de apoyo

- [Documentación oficial de Docker](https://docs.docker.com/)
- Guía proporcionada por el instructor.
- [Cheat Sheet de comandos Linux](https://www.cheatography.com/davechild/cheat-sheets/linux-command-line/)

## 8. Procedimiento

### Paso 1: Acceso a Docker Playground
Accede a [Docker Playground](https://labs.play-with-docker.com/), inicia sesión o crea una cuenta y selecciona la opción para crear una nueva instancia.

### Paso 2: Crear un contenedor de Nginx
Ejecuta el siguiente comando para iniciar un contenedor de Nginx:

![Captura de pantalla 2024-10-14 091439](https://github.com/user-attachments/assets/eb851e5f-e48a-4f02-86b4-dc528b89b922)


```bash
docker run -d -p 8081:80 --name nginx-site nginx
```

Este comando descargará la imagen de Nginx y creará un contenedor, exponiendo el puerto 80 dentro del contenedor al puerto 8081 del host.

### Paso 3: Ingresar al contenedor
Ejecuta el siguiente comando para acceder al contenedor y modificar el archivo `index.html`:

```bash
docker exec -it nginx-site /bin/bash
```

Dentro del contenedor, crea un archivo HTML básico para que sea servido por Nginx:

![Captura de pantalla 2024-10-14 091503](https://github.com/user-attachments/assets/80e429b2-24e0-4f76-940b-ad4e628efc2c)


```bash
echo "<html><body><h1>Hola, bienvenido a mi sitio web</h1></body></html>" > /usr/share/nginx/html/index.html
```

### Paso 4: Verificar el sitio web
Abre un navegador y accede a `http://<IP>:8081` (donde `<IP>` es la dirección IP de tu instancia de Docker Playground).

![Captura de pantalla 2024-10-14 091510](https://github.com/user-attachments/assets/8f9c49e4-5223-49b9-b9b0-158f1322b742)


### Paso 5: Finalizar el contenedor
Si ya no es necesario continuar con la práctica, puedes detener y eliminar el contenedor con los siguientes comandos:

```bash
docker stop nginx-site
docker rm nginx-site
```



## 9. Resultados esperados

Al finalizar la práctica, debería lograr levantar un servidor web Nginx dentro de un contenedor de Docker y servir una página HTML simple. El resultado esperado es ver el contenido HTML cuando se accede a la URL proporcionada por Docker Playground.

![Captura de pantalla 2024-10-14 091439](https://github.com/user-attachments/assets/ab93346b-a6e5-4280-bf74-404cf122f53e)

![Captura de pantalla 2024-10-14 091503](https://github.com/user-attachments/assets/8f2c2afa-3068-46b5-89e5-40a3b4f11cc8)

![Captura de pantalla 2024-10-14 091510](https://github.com/user-attachments/assets/ba86b85f-534b-4ad6-a0b3-a0a5940df57c)

## 10. Bibliografía

- Docker Inc. (2024). Docker Documentation. Recuperado de https://docs.docker.com/
