# Pac-Man 3D Arcade — PWA para Vercel

Juego original en un solo `index.html`, sin scripts ni recursos externos.
Todo el juego es CSS + JavaScript inline propio.

## Archivos (todos en la raíz del proyecto)
- `index.html` — juego + `<link rel="manifest">` y registro de `sw.js` en `<head>`
- `manifest.json` — `start_url: "/"`, `scope: "/"`, `display: "standalone"`, iconos `any` y `any maskable`
- `icon-192.png` / `icon-512.png` — Pac-Man amarillo sobre azul oscuro, arte dentro de la zona segura maskable (80%)
- `sw.js` — precachea `/`, `index.html`, manifest, iconos y `debug.html`; el juego funciona sin conexión
- `vercel.json` — `Content-Type` correcto para manifest y `sw.js`, `Service-Worker-Allowed: /`, `sw.js` sin caché
- `debug.html` — abre `/debug.html` en Vercel y verifica manifest, iconos, SW y HTTPS

## Desplegar en Vercel
1. Sube el contenido de esta carpeta como un proyecto nuevo (o `vercel deploy` / `vercel --prod`).
2. Abre la URL, luego `/debug.html`: todo debe salir PASS.
3. En Chrome/Android: menú ⋮ → "Instalar app" / "Agregar a pantalla de inicio".
   En iOS Safari: Compartir → "Añadir a pantalla de inicio" (iOS no usa el prompt automático).
4. Si cambias el juego, sube la versión en `sw.js` (`CACHE = 'pacman-3d-v2'`, etc.) para que se actualice la caché.

Nota: el Service Worker solo funciona por HTTPS (Vercel ya lo da) o en `localhost`, no con `file://`.
