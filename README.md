# Calculadora de Toros de Reemplazo

App web instalable (PWA) para calcular toros requeridos, reemplazos y toretes a criar en rebaños bovinos. Funciona sin conexión una vez instalada.

## Qué calcula

| Paso | Fórmula |
|---|---|
| Vacas directo a toro | Vacas a encaste − inseminadas |
| Vacías post IA | Inseminadas × (1 − fertilidad IA) |
| Toros requeridos | Vacías IA × % toros repaso + directo a toro × % toros monta directa (redondeo hacia arriba) |
| Toros aptos | Toros evaluados − descarte voluntario − descarte involuntario |
| Reemplazos | Toros requeridos − toros aptos |
| Toretes a criar / adquirir | Reemplazos ÷ (1 − % pérdida en crianza) (redondeo hacia arriba) |
| Toretes en crianza | Toretes por año × edad de trabajo (2 o 3 años), máximo |

Las vacas inseminadas se pueden ingresar en número o como % del encaste.

## Informe

- **Imprimir:** abre la ventana de impresión con el informe en una hoja A4.
- **Descargar PDF:** genera el PDF directamente (también sin conexión). En el celular abre el menú Compartir para enviarlo por WhatsApp o correo; en el computador lo descarga.
- El campo *Predio / cliente* aparece en el encabezado del informe y en el nombre del archivo.

## Publicar en GitHub Pages

### Opción A: desde el navegador (sin instalar nada)

1. En GitHub: **New repository** → nombre, por ejemplo `toros-reemplazo` → **Public** → **Create repository**.
2. En el repositorio vacío: **uploading an existing file**.
3. Arrastra **todo el contenido de esta carpeta** (incluida la carpeta `icons`) → **Commit changes**.
   - El archivo `.nojekyll` está oculto en Mac/Windows; si no se sube, no pasa nada.
4. **Settings → Pages** → *Source*: **Deploy from a branch** → Branch: **main** / **(root)** → **Save**.
5. En 1–2 minutos la app queda en `https://TU-USUARIO.github.io/toros-reemplazo/`.

### Opción B: con git

```bash
cd toros-reemplazo-github
git init -b main
git add .
git commit -m "Calculadora de toros de reemplazo"
git remote add origin https://github.com/TU-USUARIO/toros-reemplazo.git
git push -u origin main
```

Luego activa Pages como en el paso 4.

## Instalar en el celular

- **Android (Chrome):** abrir el link → menú ⋮ → **Instalar app**.
- **iPhone (Safari):** abrir el link → **Compartir** → **Agregar a inicio**.

Abrirla una vez con señal; después funciona sin internet.

## Actualizar

1. Modifica `index.html`.
2. En `sw.js` sube la versión: `toros-reemplazo-v2` → `toros-reemplazo-v3`.
3. Sube los cambios (commit). Los teléfonos toman la nueva versión al abrir la app con señal.

Si no cambias la versión en `sw.js`, algunos teléfonos pueden seguir mostrando la versión anterior.

## Estructura

```
index.html             App completa (HTML, CSS y JS, sin dependencias)
manifest.webmanifest   Nombre, colores e íconos para instalar
sw.js                  Service worker: funcionamiento sin conexión
icons/                 Íconos de la app
vendor/                jsPDF 2.5.2 (licencia MIT, ver vendor/jspdf-LICENSE.txt)
```
