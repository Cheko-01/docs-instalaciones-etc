#### Entrar al proyecto

```bash
cd nombre-del-repo
```



#### Revisar archivos clave

Busca si existen:

- `docker-compose.yml` (configuración de contenedor)
- `Dockerfile`
- `.env.example`



#### Configurar variables de entorno

Copia el archivo `.env`

```bash
cp .env.example .env
```

Luego edítalo si es necesario (Recomendación: pedir el .env para algunas credenciales necesarias)



#### Levantar los contenedores

```bash
docker compose up -d --build
```



#### Instalar dependencias de Laravel

```bash
docker compose exec app bash
```

```bash
composer install
```

```bash
npm install
```



##### Posibles soluciones a fallos

```bash
chown -R www-data:www-data /var/www/html/storage
```

```bash
chown -R www-data:www-data /var/www/html/bootstrap/cache
```

```bash
chmod -R 775 /var/www/html/storage
```

```bash
chmod -R 775 /var/www/html/bootstrap/cache
```

Laravel usa estas carpetas para:

- `/storage` - logs, archivos subidos, caché
- `/bootstrap/cache` - archivos de caché del framework

Si el servidor web no tiene permisos, pasan errores como:

- **Permission denied**
- **Failed to open stream**
- **Laravel no guarda logs**