# PostgreSQL Docker Compose

Este proyecto te permite levantar fácilmente un contenedor de PostgreSQL usando Docker Compose, con configuración personalizada a través de variables de entorno.

## Requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- (Opcional) [Git](https://git-scm.com/)

## Configuración

1. **Clona este repositorio** (opcional):

   ```sh
   git clone <URL-del-repositorio>
   cd PosgressDocker
   ```

2. **Edita el archivo `.env`** para personalizar el usuario, contraseña, puerto y nombre del contenedor:

   ```env
   POSTGRES_USER=admin
   POSTGRES_PASSWORD=admin123
   POSTGRES_PORT=5432
   POSTGRES_CONTAINER_NAME=postgres_container
   ```

3. **Verifica el archivo `docker-compose.yml`** (ya está configurado para usar las variables del `.env`).

## Uso

1. **Levanta el contenedor de PostgreSQL**:

   ```sh
   docker-compose up -d
   ```

2. **Verifica que el contenedor esté corriendo**:

   ```sh
   docker ps
   ```

3. **Conéctate a la base de datos** usando un cliente PostgreSQL, por ejemplo:

   - Host: `localhost`
   - Puerto: el valor de `POSTGRES_PORT` (por defecto 5432)
   - Usuario: el valor de `POSTGRES_USER`
   - Contraseña: el valor de `POSTGRES_PASSWORD`

## Persistencia de datos

Los datos de PostgreSQL se almacenan en un volumen Docker llamado `pgdata`, por lo que no se perderán aunque el contenedor se elimine.

## Detener y eliminar el contenedor

Para detener el contenedor:

```sh
docker-compose down
```

Esto detendrá y eliminará el contenedor, pero los datos permanecerán en el volumen `pgdata`.

---

**Nota:** No compartas tu archivo `.env` si contiene contraseñas reales.