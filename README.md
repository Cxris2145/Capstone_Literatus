<div align="center">

# 📚 Literatus Novelist V2

**Plataforma de lectura interactiva que combina literatura digital, biblioteca personal, economía virtual e inteligencia artificial conversacional para transformar obras clásicas en experiencias inmersivas.**

[![Demo](https://img.shields.io/badge/Demo-novelatus.tech-6C4AB6?style=for-the-badge)](https://www.novelatus.tech/)
[![Django](https://img.shields.io/badge/Django-REST_API-092E20?style=for-the-badge&logo=django)](https://www.djangoproject.com/)
[![Angular](https://img.shields.io/badge/Angular-17-DD0031?style=for-the-badge&logo=angular)](https://angular.dev/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14+-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

🌐 **Demo en vivo:** [https://www.novelatus.tech/](https://www.novelatus.tech/)

</div>

---

## 👥 Integrantes del Equipo

- **Christopher Guerrero**
- **Luis Faúndes**
- **Eithan Santibáñez**
- **Matías Morales**

> Para mayor detalle sobre arquitectura, diseño y actas de proyecto, consulta las carpetas [`Documentacion/`](respaldos-software/LiteratusNovelist-main/Documentacion) y [`Gestion/`](respaldos-software/LiteratusNovelist-main/Gestion).

---

## 📋 Tabla de Contenidos

- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Stack Tecnológico](#-stack-tecnológico)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Requisitos Previos](#-requisitos-previos)
- [Guía de Instalación y Ejecución](#-guía-de-instalación-y-ejecución)
  - [Paso 1: Clonar el repositorio](#paso-1-clonar-el-repositorio)
  - [Paso 2: Configurar la base de datos (PostgreSQL)](#paso-2-configurar-la-base-de-datos-postgresql)
  - [Paso 3: Configurar y ejecutar el backend (Django)](#paso-3-configurar-y-ejecutar-el-backend-django)
  - [Paso 4: Configurar y ejecutar el frontend (Angular)](#paso-4-configurar-y-ejecutar-el-frontend-angular)
  - [Paso 5: Probar la aplicación](#paso-5-probar-la-aplicación)
- [Compilación Móvil (Capacitor / Android)](#-compilación-móvil-capacitor--android)
- [Automatizaciones y Scripts Adicionales](#-automatizaciones-y-scripts-adicionales)
- [Solución de Problemas Comunes](#-solución-de-problemas-comunes)

---

## 📖 Descripción del Proyecto

**Literatus Novelist** es una aplicación full-stack diseñada para enriquecer la experiencia de lectura de obras clásicas de dominio público:

| Módulo | Qué hace |
|---|---|
| 📚 **Catálogo y Biblioteca Personal** | Adquisición de obras, control de propiedad digital, progreso de lectura y marcadores. |
| 📖 **Lector Inmersivo** | Lectura por capítulos HTML, audios asociados y temas visuales (Claro, Sepia, Oscuro). |
| 🤖 **Personajes con IA** | Conversación en tiempo real con avatares de personajes y autores clásicos impulsados por LLMs (Google Gemini / DeepSeek). |
| 🪙 **Economía Virtual** | Saldo de "Tinta" para desbloquear libros e interacciones con IA. |
| 💳 **Pasarela de Pago** | Integración con Transbank Webpay Plus para recargas de Tinta. |
| 📊 **Panel Administrativo** | Dashboard para gestión de autores, libros, géneros, métricas y avatares IA. |

---

## 🧰 Stack Tecnológico

| Capa | Tecnologías |
|---|---|
| **Backend** | Django + Django REST Framework, autenticación JWT, drf-spectacular (OpenAPI/Swagger) |
| **Frontend** | Angular 17 (SPA / PWA), TypeScript |
| **Base de Datos** | PostgreSQL 14+ |
| **IA** | Google Gemini · DeepSeek |
| **Pagos** | Transbank Webpay Plus |
| **Móvil** | Capacitor (build Android nativo) |
| **Automatización** | Python (scraping de libros y generación de portadas) |

---

## 📁 Estructura del Repositorio

```text
LiteratusNovelist/
├── .gitignore                      # Exclusiones de Git (node_modules, venv, .env, etc.)
├── README.md                       # Guía principal de instalación y ejecución
└── respaldos-software/
    ├── Automatizaciones/           # Scripts de scraping de libros y generación de portadas
    │   ├── Creacion de Portadas_basicas/
    │   └── scraper_elejandria_libros.py
    ├── books/                      # Biblioteca de libros y portadas descargadas
    └── LiteratusNovelist-main/
        ├── Documentacion/          # Arquitectura, manuales, actas, QA y casos de prueba
        ├── Gestion/                # Documentos de gestión e integrantes
        └── Producto/
            ├── backend/            # API REST Django (Python)
            │   ├── ai_engine/      # Módulo de IA y chat con personajes
            │   ├── catalog/        # Catálogo de libros, autores y capítulos
            │   ├── config/         # Configuración de Django (settings, urls, wsgi)
            │   ├── core/           # Modelos base, utilidades y paginación
            │   ├── dashboard/      # Métricas y administración
            │   ├── finance/        # Integración Webpay Plus y transacciones
            │   ├── json_data/      # Datos auxiliares e importaciones
            │   ├── library/        # Inventario y progreso de usuario
            │   ├── media/          # Archivos estáticos de medios
            │   ├── scripts/        # Scripts de seed y utilidades
            │   ├── users/          # Autenticación JWT y perfiles
            │   ├── manage.py       # CLI de Django
            │   ├── requirements.txt
            │   └── .env.example    # Plantilla de variables de entorno
            └── frontend/           # Aplicación SPA / PWA (Angular 17)
                ├── android/        # Proyecto nativo Android (Capacitor)
                ├── src/            # Código fuente Angular
                ├── angular.json
                ├── capacitor.config.ts
                └── package.json
```

---

## 🛠 Requisitos Previos

Asegúrate de tener instalados los siguientes programas:

| Herramienta | Versión recomendada | Enlace oficial |
|---|---|---|
| Git | 2.40+ | [Descargar Git](https://git-scm.com/downloads) |
| Python | 3.12+ | [Descargar Python](https://www.python.org/downloads/) |
| Node.js | 20.x LTS (incluye npm) | [Descargar Node.js](https://nodejs.org/) |
| PostgreSQL | 14 o superior (con pgAdmin) | [Descargar PostgreSQL](https://www.postgresql.org/download/) |

---

## 🤖 Automatizaciones y Scripts Adicionales

Dentro de `respaldos-software/Automatizaciones/` encontrarás herramientas auxiliares:

- **`scraper_elejandria_libros.py`** — Script en Python para extraer metadatos, textos y portadas de libros clásicos de dominio público.
- **`Creacion de Portadas_basicas/`** — Cuaderno Jupyter y scripts para generar portadas de libros de forma automatizada mediante modelos de IA.

---

## ❓ Solución de Problemas Comunes

<details>
<summary><b>❌ <code>psycopg2.OperationalError: could not connect to server</code></b></summary>

- Verifica que el servicio de PostgreSQL esté iniciado (`services.msc` en Windows).
- Revisa que usuario, contraseña, puerto (`5432`) y nombre de la base de datos en `.env` sean correctos.

</details>

<details>
<summary><b>❌ <code>Blocked by CORS policy</code></b></summary>

Asegúrate de tener en el `.env` del backend:

```env
CORS_ALLOWED_ORIGINS=http://localhost:4200
```

</details>

<details>
<summary><b>❌ PowerShell: "La ejecución de scripts está deshabilitada"</b></summary>

Ejecuta en PowerShell como administrador:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

</details>

<details>
<summary><b>❌ Conflictos de dependencias al hacer <code>npm install</code></b></summary>

Si hay conflictos entre versiones de Angular y Capacitor:

```bash
npm install --legacy-peer-deps
```

</details>

---

<div align="center">

**Literatus Novelist V2** · Proyecto académico desarrollado por Christopher Guerrero, Luis Faúndes, Eithan Santibáñez y Matías Morales.

</div>
