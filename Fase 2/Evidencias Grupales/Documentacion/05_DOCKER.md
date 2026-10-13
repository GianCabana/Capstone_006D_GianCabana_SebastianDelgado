# Ejecución de Kippu con Docker

La configuración crea dos servicios: `web` para Django y `db` para PostgreSQL. El contenedor web espera el estado saludable de PostgreSQL, aplica las migraciones y ejecuta el servidor de demostración.

## Preparación

```powershell
Copy-Item .env.docker.example .env.docker
```

Edite `.env.docker`. Para teléfonos de la misma red use la IPv4 del computador en `PUBLIC_BASE_URL` y en `DJANGO_ALLOWED_HOSTS`.

## Inicio

```powershell
docker compose --env-file .env.docker up --build
```

En otra consola:

```powershell
docker compose --env-file .env.docker exec web python manage.py createsuperuser
docker compose --env-file .env.docker exec web python manage.py cargar_casa_causa
```

## Detención

```powershell
docker compose --env-file .env.docker down
```

Para borrar también la base y las imágenes cargadas se puede usar `docker compose down -v`, pero esta operación elimina los datos persistentes y no debe ejecutarse durante una demostración.

## Alcance

Esta configuración usa `runserver` y credenciales de demostración. No reemplaza un despliegue productivo con HTTPS, servidor WSGI, respaldo, monitoreo y secretos gestionados.
