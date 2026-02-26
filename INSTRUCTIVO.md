# Instructivo: Sitio Web con Quarto + GitHub Pages

## ¿Cómo funciona?

Agregas un archivo `.qmd` a la carpeta `lecciones/`, haces push, y el sitio se actualiza solo en ~2 minutos.

---

## Setup Inicial (una sola vez)

### Paso 1: Crear el repositorio en GitHub

1. Ve a [github.com/new](https://github.com/new)
2. Nombre del repo: `este-es-mi-curso` (o el que prefieras)
3. Márcalo como **Public**
4. **NO** inicialices con README
5. Click en **Create repository**

### Paso 2: Subir el proyecto

Descomprime el ZIP, abre Terminal en esa carpeta y ejecuta:

```bash
cd quarto-curso
git init
git add .
git commit -m "setup inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/este-es-mi-curso.git
git push -u origin main
```

### Paso 3: Verificar

- Ve a **Actions** en tu repo y espera que el workflow termine (✅ verde)
- Tu sitio estará en: `https://TU_USUARIO.github.io/este-es-mi-curso/`

> **Nota:** El workflow activa GitHub Pages automáticamente. No necesitas configurar nada en Settings.

---

## Agregar una Nueva Lección

### Opción A: Desde Terminal (recomendado)

```bash
# 1. Copia la plantilla
cp lecciones/_plantilla.qmd lecciones/leccion-02.qmd

# 2. Edita el archivo (con cualquier editor)
#    Cambia: title, description, date
#    Escribe tu contenido debajo

# 3. Sube a GitHub
git add .
git commit -m "agregar leccion 02"
git push
```

### Opción B: Directo desde GitHub (sin Terminal)

1. Ve a tu repo → carpeta `lecciones/`
2. Click en **Add file** → **Create new file**
3. Nombre: `leccion-02.qmd`
4. Pega el contenido (copia de `_plantilla.qmd` y modifica)
5. Click en **Commit changes**

---

## Formato Obligatorio del Encabezado

Cada archivo `.qmd` DEBE tener esto al inicio:

```yaml
---
title: "Lección 2: Nombre de la Lección"
description: "De qué trata esta lección"
date: "2026-02-25"
---
```

Los 3 campos son obligatorios. Sin ellos la lección no aparece en la tabla.

---

## Markdown Rápido

```markdown
## Título de sección
### Subtítulo

Texto con **negrita** y *cursiva*.

- Viñeta uno
- Viñeta dos

1. Numerada uno
2. Numerada dos

[Un enlace](https://ejemplo.com)
```

Código:

````markdown
```r
library(tidyverse)
```
````

---

## Convención de Nombres

Archivos: `leccion-01.qmd`, `leccion-02.qmd`, ..., `leccion-10.qmd`

Siempre con cero adelante (01, 02... 09) para que se ordenen bien.

---

## Estructura del Proyecto

```
quarto-curso/
├── _quarto.yml              ← Config del sitio (NO tocar)
├── index.qmd                ← Página de inicio
├── lecciones.qmd            ← Lista automática (NO tocar)
├── lecciones/
│   ├── _plantilla.qmd       ← Plantilla para copiar
│   ├── leccion-01.qmd       ← Lección 1
│   └── leccion-02.qmd       ← Lección 2...
└── .github/workflows/
    └── deploy.yml            ← Automatización (NO tocar)
```

---

## Checklist Antes de Hacer Push

- [ ] El archivo está en `lecciones/`
- [ ] El nombre termina en `.qmd`
- [ ] Tiene `title`, `description` y `date` en el encabezado
- [ ] La fecha es `"YYYY-MM-DD"` (entre comillas)
- [ ] El encabezado empieza y termina con `---`

---

## Solución de Problemas

| Problema | Solución |
|----------|----------|
| Lección no aparece | Verifica los 3 campos del encabezado |
| Error en deploy | Revisa que `---` estén correctos en el .qmd |
| Sitio no carga | Ve a Settings → Pages → selecciona GitHub Actions |
| Cambios no se ven | Ejecuta `git push` de nuevo |
