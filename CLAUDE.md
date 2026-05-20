# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Proyecto

Landing pages estáticas para **RFL FIT 35** — programa de nutrición y ejercicio de 60 días de Adrian Lopez. Sin framework, sin build system, sin dependencias: HTML + CSS inline puro.

## Estructura

- `index.html` — Sales page principal (tema oscuro, naranja `#FF6B00` / `#FF8C00`)

El archivo `plan.html` vive en el repo separado **rfltraining/plataforma** como `index.html` (tema verde `#2D6A4F`, fondo crema).

## Deploy a GitHub

Git instalado (Apple Git 2.50.1). Repos clonados en el Desktop.

Usuario GitHub: `rfltraining`  
Token: guardado por el usuario — pedirlo si no está disponible.

### Repos locales

- `/Users/adrianlopezgmail.com/Desktop/PLAN60DIAS` → `github.com/rfltraining/PLAN60DIAS`
- `/Users/adrianlopezgmail.com/Desktop/plataforma` → `github.com/rfltraining/plataforma`

### Workflow normal

```bash
# En el repo correspondiente:
git add archivo.html
git commit -m "descripción"
git push origin main
```

### Configurar token (si git push falla por auth)

```bash
git remote set-url origin https://TOKEN@github.com/rfltraining/REPO.git
```

## Estilo CSS

Todo el CSS está inline dentro de cada HTML. Fuentes: `Playfair Display` (títulos) y `DM Sans` (cuerpo), cargadas desde Google Fonts.
