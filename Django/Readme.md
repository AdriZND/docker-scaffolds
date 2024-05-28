### Como utilizar este scaffold

Con este scaffold puedes crear una base para iniciar el desarrollo de un proyecto con Python, Django y una base de datos de PostgreSQL.

**1. Crea el directorio para tu proyecto**

**2. Copia los archivos a tu proyecto**

**3. Ejecuta**

```
docker compose run django django-admin startproject myproject .
```

**4. Da permisos a tu usuario**

Para poder modificar los archivos del contenedor
```
sudo chown -R $USER:$USER /ruta/a/tu/proyecto
sudo chmod -R 755 /ruta/a/tu/proyecto

```

**5. Configura myproject/settings.py para la BDD**

```
import os

DATABASES = {
    'default': {
        'ENGINE': os.environ.get('DB_DRIVER','django.db.backends.postgresql'),
        'USER': os.environ.get('PG_USER','postgres'),
        'PASSWORD':os.environ.get('PG_PASSWORD','postgres'),
        'NAME': os.environ.get('PG_DB','postgres'),
        'PORT': os.environ.get('PG_PORT','5432'),
        'HOST': os.environ.get('PG_HOST','localhost'), 
    }
}
```

**6. Ejecuta docker compose**

```
docker compose up --build -d
```

**7. Crea las apps que quieras con**

```
docker-compose run django python manage.py startapp myapp
```

Ya puedes trabajar con un entorno de Python, Django y PostgreSQL a través de contenedores sin tener nada instalado bare-metal en tu host.
