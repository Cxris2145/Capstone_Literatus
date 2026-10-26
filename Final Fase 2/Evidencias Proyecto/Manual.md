## 🚀 Guía de Instalación y Ejecución

## 🛠 Requisitos Previos

Asegúrate de tener instalados los siguientes programas:

| Herramienta | Versión recomendada | Enlace oficial |
|---|---|---|
| Git | 2.40+ | [Descargar Git](https://git-scm.com/downloads) |
| Python | 3.12+ | [Descargar Python](https://www.python.org/downloads/) |
| Node.js | 20.x LTS (incluye npm) | [Descargar Node.js](https://nodejs.org/) |
| PostgreSQL | 14 o superior (con pgAdmin) | [Descargar PostgreSQL](https://www.postgresql.org/download/) |

---

### Paso 1: Clonar el repositorio

```bash
git clone https://github.com/Cxris2145/LiteratusNovelistV2.git
cd LiteratusNovelistV2
```

### Paso 2: Configurar la base de datos (PostgreSQL)

1. Abre **pgAdmin** o conéctate mediante `psql`.
2. Crea una base de datos llamada `literatus_db`:

   ```sql
   CREATE DATABASE literatus_db;
   ```

3. Anota tu usuario y contraseña de PostgreSQL (en local suele ser el usuario `postgres` con la contraseña que definiste en la instalación).

### Paso 3: Configurar y ejecutar el backend (Django)

**3.1. Navegar a la carpeta del backend**

```bash
cd respaldos-software/LiteratusNovelist-main/Producto/backend
```

**3.2. Crear y activar el entorno virtual**

<details>
<summary><b>Windows (PowerShell)</b></summary>

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

> Si PowerShell bloquea la ejecución de scripts, ejecuta antes:
> `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`

</details>

<details>
<summary><b>macOS / Linux</b></summary>

```bash
python3 -m venv .venv
source .venv/bin/activate
```

</details>

**3.3. Instalar las dependencias**

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**3.4. Configurar las variables de entorno (`.env`)**

Copia la plantilla para crear tu `.env` local:

```bash
# Windows
copy .env.example .env

# macOS / Linux
cp .env.example .env
```

Luego ajusta los valores con tus credenciales locales:

```env
DEBUG=True
SECRET_KEY=django-insecure-clave-secreta-de-desarrollo-local
DATABASE_URL=postgres://postgres:TU_PASSWORD_AQUI@localhost:5432/literatus_db
ALLOWED_HOSTS=localhost,127.0.0.1
CORS_ALLOWED_ORIGINS=http://localhost:4200

# Opcionales para IA (puedes dejarlas vacías para desarrollo general)
GOOGLE_API_KEY=
DEEPSEEK_API_KEY=

# Configuración Webpay (ambiente de Integración / Pruebas)
WEBPAY_COMMERCE_CODE=597055555532
WEBPAY_API_KEY=579B532A7440BB0C9079DED94D31EA1615BACEB56610332264630D42D0A36B1C
WEBPAY_ENVIRONMENT=INTEGRACION
WEBPAY_RETURN_URL=http://localhost:8000/api/v1/finance/confirm/
FRONTEND_URL=http://localhost:4200
```

> ⚠️ **Importante:** las credenciales Webpay anteriores son públicas y corresponden **solo al ambiente de integración** de Transbank. Nunca subas credenciales de producción ni tu archivo `.env` al repositorio.

**3.5. Aplicar migraciones**

```bash
python manage.py migrate
```

**3.6. Crear un usuario administrador**

```bash
python manage.py createsuperuser
```

**3.7. Iniciar el servidor backend**

```bash
python manage.py runserver
```

✅ El backend quedará corriendo en `http://localhost:8000`

| Recurso | URL |
|---|---|
| Documentación Swagger / OpenAPI | `http://localhost:8000/api/schema/swagger-ui/` |
| Panel de administración Django | `http://localhost:8000/admin/` |
| API base | `http://localhost:8000/api/v1/` |

### Paso 4: Configurar y ejecutar el frontend (Angular)

Abre **otra terminal independiente**.

```bash
cd respaldos-software/LiteratusNovelist-main/Producto/frontend
npm install
npm start          # alternativa: npx ng serve
```

✅ El frontend quedará corriendo en `http://localhost:4200`

### Paso 5: Probar la aplicación

1. Abre tu navegador en `http://localhost:4200`.
2. Regístrate con una cuenta nueva o inicia sesión con tu usuario administrador.
3. Explora el catálogo, lee capítulos, conversa con los avatares IA y prueba la recarga de Tinta.

---

## 📱 Compilación Móvil (Capacitor / Android)

Requiere **Android Studio** y el **SDK de Android** instalados. Desde `Producto/frontend`:

```bash
npm run build
npx cap sync android
npx cap open android
```

Luego ejecuta el proyecto en un emulador o en un dispositivo físico con depuración USB activada.
