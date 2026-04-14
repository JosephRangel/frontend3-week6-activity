# 🛒 TechStore - Frontend III (Semana 6)

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](#)
[![Vite](https://img.shields.io/badge/Vite-B73BFE?logo=vite&logoColor=fff)](#)
[![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB)](#)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwind-css&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/Docker-2CA5E0?logo=docker&logoColor=white)](#)
[![Vercel](https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white)](#)

Repositorio oficial de la actividad de la Semana 6 para la asignatura de Desarrollo Frontend III. **TechStore** es una plataforma de e-commerce construida con arquitecturas modernas, diseñada para demostrar el manejo avanzado de estado, optimización de estilos con clases de utilidad, contenedorización y despliegue continuo en la nube.

## 🚀 Arquitectura y Características Principales

* **Catálogo de Productos:** Integración dinámica de datos para mostrar un inventario de artículos.
* **Estilizado de Utilidades:** Diseño de interfaces altamente responsivas y escalables utilizando **Tailwind CSS**, manteniendo un archivo CSS global mínimo.
* **Gestión de Estado Complejo:** Arquitectura para manejar el flujo del carrito de compras.
* **Despliegue Automatizado:** Pipeline de CI/CD que conecta el código directamente desde GitHub hasta la red global de Vercel.

## 🛠️ Stack Tecnológico

* **Core:** React 18 + Vite
* **Estilos:** Tailwind CSS
* **Contenedores:** Docker
* **Infraestructura Cloud:** Vercel
* **Integración Continua:** GitHub Actions (Pruebas automáticas y versionado)

## 💻 Instalación y Desarrollo Local

Para trabajar en el proyecto desde tu máquina local, sigue estos pasos:

1. **Clonar el repositorio:**
```bash
git clone [https://github.com/JosephRangel/frontend3-week6-activity.git](https://github.com/JosephRangel/frontend3-week6-activity.git)
cd frontend3-week6-activity
```

2. **Instalar dependencias:**
```bash
npm install
```

3. **Ejecutar el servidor en modo desarrollo:**
```bash
npm run dev
```
La aplicación estará disponible en `http://localhost:5173`.

## 🐳 Contenedores con Docker

Este proyecto está preparado para ser encapsulado en una imagen de Docker. Para manipular las imágenes y publicarlas, es necesario autenticarse previamente.

1. **Autenticación en Docker Hub:**
   Antes de descargar o subir imágenes privadas/públicas vinculadas a tu cuenta, inicia sesión en la terminal:
```bash
docker login
```
*(Ingresa tu nombre de usuario y contraseña o Access Token cuando se te solicite).*

2. **Construir la imagen de producción:**
```bash
docker build -t techstore-app .
```

3. **Ejecutar el contenedor:**
```bash
docker run -d -p 8080:80 --name techstore-container techstore-app
```
Accede a la aplicación lista para producción en `http://localhost:8080`.

## ☁️ Despliegue en la Nube (Vercel)

La aplicación está configurada para desplegarse automáticamente en Vercel cada vez que se aprueba una nueva versión. Si necesitas replicar esta configuración en un proyecto nuevo, estos son los pasos de integración:

1. **Enlace con GitHub:**
* Crea una cuenta en Vercel e inicia sesión con GitHub.
* Selecciona **"Add New Project"** e importa este repositorio (`frontend3-week6-activity`).

2. **Configuración del Proyecto (Vite):**
   Vercel detectará automáticamente que el proyecto utiliza Vite. Confirma que los ajustes sean los siguientes:
* **Framework Preset:** Vite
* **Build Command:** `npm run build`
* **Output Directory:** `dist`

3. **Optimización del Pipeline (Ignorar PRs):**
   Para evitar que Vercel consuma minutos de construcción en Pull Requests o commits intermedios, el repositorio cuenta con un archivo `vercel.json` en la raíz. Este archivo le indica a la plataforma que **solo debe desplegar** cuando detecte el commit oficial del *Release* generado por nuestro bot automatizado:

```json
{
  "github": {
    "silent": true
  },
  "ignoreCommand": "if [ \"$VERCEL_ENV\" != \"production\" ]; then exit 0; elif git log -1 --pretty=%B | grep -q \"chore\"; then exit 1; else exit 0; fi"
}
```

## ⚙️ Flujo de CI/CD (GitHub Actions)

El repositorio mantiene estándares empresariales de integración y despliegue continuo:

* **Protección de Rama Principal:** Todo cambio en `main` debe pasar por un proceso de revisión y validación automática mediante *Pull Requests*.
* **Validación de Código:** Cada PR dispara un *workflow* que verifica reglas de calidad y pruebas estructurales.
* **Automatización de Releases:** Tras una fusión exitosa, nuestro bot genera automáticamente una nueva versión semántica y actualiza el registro de cambios (`CHANGELOG.md`). Una vez creado este commit de release, Vercel lo detecta y publica la aplicación en vivo.

---
**Profesor:** Jose Antonio Rangel Reyes  
**Credenciales:** Maestro en Ingeniería de Desarrollo de Software | Ing. en Tecnologías de la Información y Comunicación  
**Institución:** Cesun Universidad  
**Materia:** Desarrollo Frontend III