# Guía de Inicio

## Requisitos

Antes de comenzar, asegúrate de tener instalado:

* Docker
* Docker Compose
* Git

Verifica con:

```bash
docker -v
docker compose version
git --version
```

---

## Clonar el repositorio

```bash
git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_PROYECTO>
```

---

## Configuración inicial

### 1. Copiar archivo de entorno

```bash
cp .env.example .env
```

### 2. Configurar variables

Edita el archivo `.env` según tu entorno:

```env
APP_NAME=Laravel
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=secret
```

### Recomendación
Pedir el `.env` para el uso de variables de entorno

---

##  Levantar contenedores

```bash
docker compose up -d --build
```

Verifica que estén corriendo:

```bash
docker ps
```

---

## Instalar dependencias

Accede al contenedor de la app:

```bash
docker compose exec app bash
```

Dentro del contenedor:

```bash
composer install
```

---

## Generar clave de aplicación

```bash
php artisan key:generate
```

---

## Migraciones y seeders

```bash
php artisan migrate
```

Opcional (si hay datos de prueba):

```bash
php artisan db:seed
```

---

## Permisos (importante en Linux)

```bash
chmod -R 775 storage bootstrap/cache
```

---

## Acceso a la aplicación

Abre en tu navegador:

```
http://localhost
```


---

##  Comandos útiles
### Detener contenedores

```bash
docker compose down
```

### Ver logs

```bash
docker compose logs -f
```

### Acceder al contenedor

```bash
docker compose exec app bash
```

---

## Problemas comunes

### Error 502 / Bad Gateway

* Verifica que el contenedor `app` esté corriendo
* Revisa logs:

  ```bash
  docker compose logs app
  ```

### Error de conexión a la BD

* Confirma que `DB_HOST=db`
* Asegúrate de que el contenedor `db` esté activo

### Permisos

* Ejecuta:

  ```bash
  chmod -R 775 storage bootstrap/cache
  ```

---
##  Notas

* No subas el archivo `.env` al repositorio
* Usa `.env.example` como referencia
* Si cambias dependencias:

  ```bash
  composer update
  ```

---

##  Flujo recomendado

1. Clonar repo
2. Configurar `.env`
3. Levantar Docker
4. Instalar dependencias
5. Migrar base de datos
6. Ejecutar proyecto

---

Levantar el proyecto se reduce a: clonar, configurar `.env`, levantar Docker, instalar dependencias y correr migraciones. Si algo falla, casi siempre es por variables de entorno, contenedores detenidos o permisos.
