# /app /usr /lib  descarga la version de node en docker
#FROM --platform=linux/amd64 node:19.2-alpine3.16 Para cambia el tipo de arquitectura

#PARA CREAR DIFERENTES AEQUITECTURAS EN UN SOLO ARCHIVO $buildplatform
#FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16 

#PARA CONSTRUIR UNA UNICA ARQUITECTURA
FROM node:19.2-alpine3.16 

# cd app Genera la carpeta donde se ejecutara la imagen
WORKDIR /app

#Dest /app Revisa las dependencias necesarias
COPY package.json ./

#Instalar las dependencias Ejecuta las dependencias 
RUN npm install

#Dest /app Copia todas las dependencias de nuestro archivo, excluyendo el dockerignore
COPY . .

#Realizar testing Ejecuta el test
RUN npm run test

#Eliminar archivos y directorios no necesarios en PROD, ejecuta un comando en consola
RUN rm -rf tests && rm -rf node_modules  

#Unicamente las dependencias de prod, ejecuta unicamente las dependencias que necesitamos
RUN npm install --prod

#Comando run de la imagen
CMD [ "node", "app.js" ]