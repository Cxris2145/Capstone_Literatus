# ✅ Definition of Done (DoD) - Criterios de Terminado

Para que una tarjeta pase de la columna "Auditoría Humana (QA)" a "Integrado (Done)" en nuestro tablero Scrumban, debe cumplir obligatoriamente con los siguientes criterios:

1. **Auditoría Anti-Alucinaciones:** El código generado por los agentes de IA fue revisado manualmente por un desarrollador distinto al que generó el prompt (generalmente QA/Eithan) y no contiene llamadas a librerías inexistentes ni lógicas inventadas.
2. **Aislamiento de Ramas:** El desarrollo se realizó en una rama independiente (`feature/nombre-tarea`) y no directamente en `main`.
3. **Pruebas Locales (Build Success):** 
   - El backend en Django compila sin errores (`python manage.py runserver`).
   - Las migraciones de PostgreSQL se aplicaron correctamente (`makemigrations` / `migrate`).
   - El frontend en Angular compila sin errores en consola (`npm start`).
4. **Cumplimiento de RNF:** Ninguna llave de API (Gemini, Webpay, DeepSeek) quedó expuesta en el código fuente; todas consumen variables del archivo `.env`.
5. **Aprobación de Integración:** La rama fue fusionada (Merged) a `main` sin conflictos de código.