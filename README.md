# 🎮 Proyecto Eureka - Juego Educativo

Aplicación web interactiva / juego educativo optimizado para despliegue en servidor VPS utilizando **Dokploy** y **Docker Compose**.

---

## 🚀 Despliegue en Dokploy

Este repositorio está 100% preparado y optimizado para ser desplegado automáticamente en Dokploy.

### Pasos para desplegar en Dokploy:

1. **Crear una nueva Aplicación o Servicio Compose**:
   - En tu panel de **Dokploy**, ve a tu proyecto y haz clic en **Create Service**.
   - Selecciona **Compose** (o **Application**).

2. **Vincular el Repositorio de GitHub**:
   - **Repository URL**: `https://github.com/Johann3421/Juego_Educativo.git`
   - **Branch**: `main`
   - **Build Type**: `Docker Compose` (usa `docker-compose.yml`) o `Dockerfile`.

3. **Configurar el Dominio y Puertos**:
   - Dokploy detectará el servicio `app` exponiendo el puerto `80`.
   - Asigna tu dominio o subdominio en la pestaña **Domains** de Dokploy y habilita el certificado SSL automático con Let's Encrypt.

4. **Desplegar**:
   - Haz clic en **Deploy**. ¡Listo! Dokploy descargará el código, construirá la imagen con Nginx y lo pondrá en producción.

---

## 🛠️ Ejecución Local con Docker

Si deseas probar el proyecto localmente antes de desplegar:

```bash
# Construir y levantar el contenedor
docker compose up --build -d

# Ver el estado
docker compose ps

# Abrir en el navegador
# http://localhost:93
```

Para detener el contenedor:
```bash
docker compose down
```

---

## 📁 Estructura del Proyecto

```text
├── Dockerfile              # Imagen Docker ligera basada en nginx:alpine
├── docker-compose.yml      # Configuración de Docker Compose lista para Dokploy
├── nginx.conf              # Configuración de Nginx optimizada (Gzip, MIME, Cache, Healthcheck)
├── .dockerignore           # Exclusión de archivos innecesarios en el build de Docker
├── .gitignore              # Archivos ignorados por Git
├── index.html              # Entrada principal de la aplicación web
├── main.js                 # Lógica de la aplicación / motor web
├── package.bin             # Paquete binario de assets y recursos del juego
├── manifest.webmanifest    # Manifiesto PWA
└── app-icon-*.png          # Íconos de la aplicación
```

---

## ⚡ Optimizaciones incluidas
- **Servidor Nginx ultraligero y de alto rendimiento**.
- **Soporte para Range Requests (HTTP 206)** para descarga eficiente del archivo `package.bin` (36MB).
- **Compresión Gzip activada** para recursos HTML, JS y JSON.
- **Cabeceras de seguridad y caché optimizadas** (los cambios en `index.html` se reflejan de inmediato).
- **Healthcheck endpoint** en `/healthz` para monitoreo continuo en el VPS.
