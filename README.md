# Acortador de enlaces (GitHub Pages)

Un acortador de URLs **sin servidor**: funciona solo con archivos estáticos en
GitHub Pages. Pensado para generar enlaces cortos que se escriben en etiquetas
**NFC** (por ejemplo, para abrir un reporte de Power BI).

Ya viene cargado un enlace de ejemplo con el código `powerbi`.

---

## Cómo se ve un enlace corto

```
https://TU-USUARIO.github.io/TU-REPO/powerbi
```

Al abrirlo, redirige automáticamente al enlace largo guardado en `links.json`.

---

## Puesta en marcha (una sola vez)

1. Crea un repositorio nuevo en GitHub (por ejemplo `links`).
   - Debe ser **público** para usar GitHub Pages gratis. (Con cuenta GitHub Pro,
     también funciona en privado.)
2. Sube estos 4 archivos al repositorio:
   - `index.html`  → generador y lista de enlaces
   - `404.html`    → el que hace la redirección de rutas limpias
   - `links.json`  → la base de datos (código → enlace largo)
   - `README.md`   → este archivo
3. En el repositorio ve a **Settings → Pages**.
   - En *Source* elige la rama `main` y la carpeta `/ (root)`.
   - Guarda. En uno o dos minutos te dará la dirección
     `https://TU-USUARIO.github.io/TU-REPO/`.

Listo. Abre esa dirección y verás el generador.

---

## Cómo agregar un enlace corto nuevo

**Opción fácil (desde la página):**
1. Abre `https://TU-USUARIO.github.io/TU-REPO/`.
2. Pega el enlace largo, escribe un código corto (o déjalo vacío) y una
   descripción.
3. Pulsa **Agregar enlace** → te muestra el enlace corto.
4. Pulsa **Descargar links.json actualizado**.
5. Sube ese `links.json` al repositorio, reemplazando el anterior
   (en GitHub: abre `links.json` → ✏️ *Edit* → pega el contenido, o súbelo con
   *Add file → Upload files*).

En cuanto se actualiza `links.json`, el enlace corto ya funciona.

**Opción manual (editando el archivo):**
Edita `links.json` y agrega una entrada:

```json
{
  "powerbi": {
    "url": "https://app.powerbi.com/...",
    "label": "Reporte Power BI",
    "created": "2026-11-06"
  },
  "inventario": {
    "url": "https://.../otro-reporte",
    "label": "Inventario del taller",
    "created": "2026-11-06"
  }
}
```

---

## Cómo escribirlo en la etiqueta NFC

En la app **NFC Tools**: pestaña *Escribir* → *Añadir un registro* → **URL/URI** →
pega tu enlace corto (`https://TU-USUARIO.github.io/TU-REPO/powerbi`) → escribe
en la etiqueta. Al escanear con cualquier celular, abrirá el reporte.

---

## Notas importantes

- **`links.json` es público.** Cualquiera que vea el repositorio puede leer los
  enlaces de destino. No son secretos (abrir un reporte de Power BI sigue
  pidiendo iniciar sesión), pero si es contenido **interno de la empresa**,
  revisa la política de TI antes de publicarlo. Si hace falta privacidad, lo
  mejor es alojar esto en un servidor propio (tu home-lab) en vez de GitHub.
- **No pongas enlaces tipo "embed" con token** (los que llevan credenciales
  dentro de la URL) en un sitio público.
- El enlace corto solo **redirige**; no da acceso ni salta la seguridad del
  reporte.
