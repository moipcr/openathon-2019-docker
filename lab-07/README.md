#Paso 1. Clonar el proyecto Events-UI a la máquina virtual

Vamos a clonar el proyecto Events-UI en la misma máquina virtual que hemos usado en los laboratorios anteriores. Para ello ejecutaremos el siguiente comando en la carpeta raiz home del usuario:

cd
git clone https://github.com/pacobull/event-ui

Accederemos a su interior con el siguiente comando cd o similares dependiendo de sistema:

cd event*

#Paso 2. Hacer pull de las imágenes Docker que usaremos como base.

Imagen de Node.js: Contiene una instalación de Node.js que vamos a necesitar para "compilar" la aplicación.
Imagen de Nginx: Contiene una instalación de Nginx que usaremos como servidor web para publicar nuestra aplicación.
Para hacer el pull de ambas imágenes tan solo tenemos que ejecutar los siguientes comandos en nuestro terminal:

docker pull node

docker pull nginx

Si todo va bien, después de completar la descarga, ambas imágenes deben aparecer en nuestra lista tras ejecutar el siguiente comando:

docker images

Como resultado obtendremos ambas imagenes (node y nginx)


#Paso 3. Revisemos el fichero de configuración para Nginx.

https://github.com/moipcr/openathon-2019-docker/blob/master/lab-07/nginx.conf

#Paso 4. Revisemos el fichero Dockerfile.
Es necesario crear este Dockerfile para que dockers sepa desplegar correctamente el proyecto en el contenedor

https://github.com/moipcr/openathon-2019-docker/blob/master/lab-07/Dockerfile

#Paso 5. Crear la nueva imagen a partir del fichero Dockerfile.

docker build -t events-ui --build-arg ARG_API_URL=localhost .

#Paso 6. Ejecutar nuestra nueva imagen para generar un nuevo contenedor.
Para ellos vamos a ejecutar el siguiente comando:

docker run -d -p 80:80 --name "EventsUI" events-ui


y voilá!!


