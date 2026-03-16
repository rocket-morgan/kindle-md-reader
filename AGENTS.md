# AGENTS.md — kindle-md-reader

## Qué es
Servidor Node/Express que lista carpetas y archivos Markdown, renderiza HTML minimal apto para Kindle, con auth simple y controles de zoom (+/-).

## Rutas
- `/login` → auth (usuario/clave)
- `/browse` → listado de carpetas/archivos `.md`
- `/file/<path>` → render Markdown
- `/health` → OK JSON
- `/font/up` y `/font/down` → ajustan font-size (cookie `fs`)

## Config (env)
- `PORT` (default 3000)
- `VAULT_PATH` (default `/root/synchthing/Obsidian.md` en dev)
- `AUTH_USER` (default `kindle`)
- `AUTH_PASS` (default `changeme`)
- `SESSION_SECRET` (default `secret`)

## Seguridad
- Cookie de sesión base64 `ks`; auth en texto plano (usar detrás de HTTPS/túnel).
- Sanitiza HTML (sanitize-html) y protege path traversal.

## Dev
```
npm install --include=dev
PORT=4000 AUTH_PASS=pass SESSION_SECRET=secret node server.js
```

Playwright smoke test (requiere server arriba en 4000):
```
NODE_PATH=./node_modules node /tmp/pw-check.js
```
