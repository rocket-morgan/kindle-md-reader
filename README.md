# Kindle Markdown Reader

Servidor minimalista (Node + Express) para navegar y leer archivos Markdown desde una carpeta local ("vault"), con HTML simple apto para Kindle (Paperwhite / browser experimental).

## Features
- Autenticación simple por usuario/contraseña (cookie de sesión)
- Navegación de carpetas y archivos `.md`
- Render Markdown → HTML minimal (sin JS) + controles de zoom (+/-) vía cookie
- Protección contra path traversal
- Configurable vía variables de entorno

## Config
Crea un `.env` (ver `.env.example`):
```
PORT=3000
VAULT_PATH=/ruta/a/tu/vault
AUTH_USER=kindle
AUTH_PASS=changeme
SESSION_SECRET=replace-me
```

## Run
```
npm install --include=dev
npm start
# abre http://localhost:3000
```

## Test rápido con Playwright
```
# requiere que el server esté corriendo (ej: PORT=4000)
NODE_PATH=./node_modules node /tmp/pw-check.js
```

## Notas Kindle
- HTML sin JS ni CSS complejo
- Font-size ajustable (+/-) persistido en cookie
- No se sirven imágenes ni assets externos; solo Markdown

Licencia: MIT
