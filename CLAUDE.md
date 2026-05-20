# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Proyecto

Landing pages estáticas para **RFL FIT 35** — programa de nutrición y ejercicio de 60 días de Adrian Lopez. Sin framework, sin build system, sin dependencias: HTML + CSS inline puro.

## Estructura

- `index.html` — Sales page principal (tema oscuro, naranja `#FF6B00` / `#FF8C00`)

El archivo `plan.html` vive en el repo separado **rfltraining/plataforma** como `index.html` (tema verde `#2D6A4F`, fondo crema).

## Deploy a GitHub

**Git no está instalado** en este Mac (requiere Xcode Command Line Tools). Todo el deploy se hace via GitHub REST API con `curl`.

Usuario GitHub: `rfltraining`  
Token: guardado por el usuario — pedirlo si no está disponible.

### Subir/actualizar un archivo

```bash
# 1. Obtener SHA del archivo actual (necesario para updates)
SHA=$(curl -s -H "Authorization: token TOKEN" \
  "https://api.github.com/repos/rfltraining/PLAN60DIAS/contents/index.html" \
  | grep '"sha"' | head -1 | sed 's/.*"sha": "\([^"]*\)".*/\1/')

# 2. Encodear y subir (usar archivo temp para evitar "argument list too long")
CONTENT=$(base64 -i index.html | tr -d '\n')
printf '{"message":"Update index.html","sha":"%s","content":"%s"}' "$SHA" "$CONTENT" > /tmp/upload.json
curl -s -X PUT \
  -H "Authorization: token TOKEN" \
  -H "Content-Type: application/json" \
  -d @/tmp/upload.json \
  "https://api.github.com/repos/rfltraining/PLAN60DIAS/contents/index.html"
rm /tmp/upload.json
```

Para **nuevo archivo** (sin `sha`) o repo **plataforma**, cambiar la URL y omitir el campo `sha`.

### No hacer deletes en paralelo

Borrar dos archivos del mismo repo simultáneamente causa conflicto de SHA. Hacerlos secuencialmente.

## Estilo CSS

Todo el CSS está inline dentro de cada HTML. Fuentes: `Playfair Display` (títulos) y `DM Sans` (cuerpo), cargadas desde Google Fonts.
