# pythonVue

Este proyecto es una aplicación web desarrollada utilizando Django como framework backend y Vue.js para el frontend, ofreciendo una experiencia de usuario rica y dinámica. Este esqueleto básico puede servir como punto de partida para aplicaciones más complejas.

## Pre-requisitos

Antes de comenzar, asegúrate de tener instalado Python (versión 3.x), pip, virtualenv, Node.js y npm en tu sistema. Estas herramientas son esenciales para la configuración del entorno de desarrollo tanto del backend como del frontend.

## Configuración del entorno de desarrollo

### Backend

1. **Crear un entorno virtual**
   
   ```bash
   virtualenv -p python3 env
   source env/bin/activate
   ```

2. **Instalar Django**

   ```bash
   pip install django
   ```

3. **Crear el proyecto Django**

   Reemplaza `[nombre_del_proyecto]` con el nombre que desees para tu proyecto.

   ```bash
   django-admin startproject [nombre_del_proyecto]
   ```

4. **Crear una aplicación Django**

   ```bash
   django-admin startapp book
   ```

5. **Crear y correr migraciones**

   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Ingresar a la consola de Django**

   ```bash
   python manage.py shell
   ```

7. **Instalar Django REST Framework**

   ```bash
   pip install djangorestframework
   ```

8. **Manejo de CORS**

   Asegúrate de instalar las dependencias necesarias para manejar Cross-Origin Resource Sharing (CORS).

   ```bash
   pip install django-cors-headers
   ```

### Frontend

1. **Crear el proyecto Vue.js**

   ```bash
   vue init webpack frontend
   cd frontend
   ```

2. **Uso de Bootstrap Vue**

   ```bash
   npm install bootstrap-vue
   ```

3. **Instalar Axios para solicitudes HTTP**

   ```bash
   npm install axios
   ```

4. **Instalar librería de alertas SweetAlert**

   ```bash
   npm install sweetalert
   ```

## Ejecución del proyecto

Para ejecutar el proyecto, necesitarás iniciar tanto el servidor backend como el servidor de desarrollo frontend.

- **Backend**

  Desde el directorio raíz del proyecto Django:

  ```bash
  python manage.py runserver
  ```

- **Frontend**

  Dentro del directorio `frontend`:

  ```bash
  npm run dev
  ```

Esto iniciará el servidor de desarrollo de Vue.js, generalmente accesible a través de `http://localhost:8080`.

## Contribuir

Las contribuciones son bienvenidas. Por favor, siente libre de forkear el repositorio y enviar tus pull requests.