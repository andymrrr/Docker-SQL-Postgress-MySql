# Multi-Database Docker Compose

Este proyecto te permite levantar fácilmente múltiples bases de datos usando Docker Compose, con configuración personalizada para desarrollo y producción. Incluye **PostgreSQL**, **MySQL** y **SQL Server**.

## 🚀 Características

- **3 tipos de bases de datos:** PostgreSQL, MySQL y SQL Server
- **Ambientes separados:** Desarrollo y Producción para cada base de datos
- **Perfiles flexibles:** Levanta solo lo que necesitas
- **Configuración mediante variables de entorno**
- **Persistencia de datos** con volúmenes Docker

## 📋 Requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- (Opcional) [Git](https://git-scm.com/)

## ⚙️ Configuración

1. **Clona este repositorio** (opcional):

   ```bash
   git clone <URL-del-repositorio>
   cd Docker-SQL-Postgress-MySql
   ```

2. **Crea el archivo `.env`** con las variables de entorno:

   ```bash
   # Copia y personaliza las variables según tus necesidades
   ```

3. **Variables de entorno principales:**

   ```env
   # PostgreSQL Desarrollo
   POSTGRES_DEV_USER=postgres
   POSTGRES_DEV_PASSWORD=password
   POSTGRES_DEV_PORT=5432

   # PostgreSQL Producción
   POSTGRES_PROD_USER=postgres
   POSTGRES_PROD_PASSWORD=securepassword123
   POSTGRES_PROD_PORT=5433

   # MySQL Desarrollo
   MYSQL_DEV_USER=mysql
   MYSQL_DEV_PASSWORD=password
   MYSQL_DEV_PORT=3306

   # MySQL Producción
   MYSQL_PROD_USER=mysql
   MYSQL_PROD_PASSWORD=securepassword123
   MYSQL_PROD_PORT=3307

   # SQL Server Desarrollo
   SQLSERVER_DEV_PASSWORD=Password123!
   SQLSERVER_DEV_PORT=1433

   # SQL Server Producción
   SQLSERVER_PROD_PASSWORD=SecurePassword123!
   SQLSERVER_PROD_PORT=1434
   ```

## 🎯 Uso - Comandos Específicos

### **Levantar bases de datos individuales:**

```bash
# Solo PostgreSQL de desarrollo
docker-compose --profile postgres-dev up -d

# Solo PostgreSQL de producción
docker-compose --profile postgres-prod up -d

# Solo MySQL de desarrollo
docker-compose --profile mysql-dev up -d

# Solo MySQL de producción
docker-compose --profile mysql-prod up -d

# Solo SQL Server de desarrollo
docker-compose --profile sqlserver-dev up -d

# Solo SQL Server de producción
docker-compose --profile sqlserver-prod up -d
```

### **Levantar por tipo de base de datos:**

```bash
# Todas las PostgreSQL (dev y prod)
docker-compose --profile postgres up -d

# Todas las MySQL (dev y prod)
docker-compose --profile mysql up -d

# Todas las SQL Server (dev y prod)
docker-compose --profile sqlserver up -d
```

### **Levantar por ambiente:**

```bash
# Todas las de desarrollo
docker-compose --profile dev up -d

# Todas las de producción
docker-compose --profile prod up -d

# TODAS las bases de datos
docker-compose --profile all up -d
```

## 🔌 Conexiones

### **PostgreSQL:**

- **Desarrollo:** `localhost:5432`

  - Usuario: `postgres` (configurable)
  - Contraseña: `password` (configurable)
  - Base de datos: `testdb`

- **Producción:** `localhost:5433`
  - Usuario: `postgres` (configurable)
  - Contraseña: `securepassword123` (configurable)
  - Base de datos: `proddb`

### **MySQL:**

- **Desarrollo:** `localhost:3306`

  - Usuario: `mysql` (configurable)
  - Contraseña: `password` (configurable)
  - Base de datos: `testdb`

- **Producción:** `localhost:3307`
  - Usuario: `mysql` (configurable)
  - Contraseña: `securepassword123` (configurable)
  - Base de datos: `proddb`

### **SQL Server:**

- **Desarrollo:** `localhost:1433`

  - Usuario: `sa`
  - Contraseña: `Password123!` (configurable)

- **Producción:** `localhost:1434`
  - Usuario: `sa`
  - Contraseña: `SecurePassword123!` (configurable)

## 📊 Gestión

### **Ver estado de contenedores:**

```bash
docker ps
```

### **Detener servicios:**

```bash
# Detener todo
docker-compose down

# Detener un perfil específico
docker-compose --profile postgres-dev down
```

### **Ver logs:**

```bash
# Logs de todos los servicios activos
docker-compose logs

# Logs de un servicio específico
docker-compose logs postgres-dev
```

### **Limpiar volúmenes (¡CUIDADO - Borra datos!):**

```bash
docker-compose down -v
```

## 💾 Persistencia de Datos

Los datos se almacenan en volúmenes Docker separados:

- `pgdata_dev` y `pgdata_prod` para PostgreSQL
- `mysql_dev` y `mysql_prod` para MySQL
- `sqlserver_dev` y `sqlserver_prod` para SQL Server

Los datos persisten aunque elimines los contenedores.

## 🔐 Seguridad

- **Cambia las contraseñas por defecto** en producción
- **No compartas tu archivo `.env`** si contiene contraseñas reales
- Las contraseñas de SQL Server deben cumplir requisitos de complejidad

## 📝 Ejemplos de Uso Común

```bash
# Solo para desarrollo local
docker-compose --profile dev up -d

# Solo PostgreSQL para un proyecto específico
docker-compose --profile postgres up -d

# Setup completo para testing
docker-compose --profile all up -d

# Cleanup completo
docker-compose down && docker system prune -f
```

---

**¡Listo!** Ahora tienes un entorno completo con múltiples bases de datos configurables. 🎉
