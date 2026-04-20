# Simulador: Elige tu reacción
### Autogestión Emocional en Escenarios Profesionales

> **Herramienta educativa interactiva** para identificar y reflexionar sobre estilos de afrontamiento emocional en contextos laborales y académicos. Basada en neurociencia aplicada, modelo SCARF (Rock, 2008) y teorías de motivación (Maslow, Herzberg, Ryan & Deci).

---

## 📋 Tabla de Contenidos

1. [Descripción pedagógica](#descripción-pedagógica)
2. [Características técnicas](#características-técnicas)
3. [Estructura del proyecto](#estructura-del-proyecto)
4. [Instalación local](#instalación-local)
5. [Despliegue en GitHub Pages](#despliegue-en-github-pages)
6. [Guía de personalización](#guía-de-personalización)
7. [Accesibilidad (WCAG 2.1 AA)](#accesibilidad-wcag-21-aa)
8. [Compatibilidad de navegadores](#compatibilidad-de-navegadores)
9. [Rendimiento](#rendimiento)
10. [Licencia](#licencia)

---

## Descripción pedagógica

### Objetivos de aprendizaje

Al completar la simulación, el estudiante será capaz de:

- **OA1** — Identificar su estilo dominante de afrontamiento emocional (ataque, huida, regulación) ante situaciones de alta presión profesional.
- **OA2** — Distinguir las bases neurológicas de cada reacción: sistema nervioso simpático (ataque), eje HPA/cortisol (huida) y corteza prefrontal dorsolateral (regulación).
- **OA3** — Conectar cada tipo de respuesta con sus consecuencias organizacionales en términos de estatus, autonomía, cohesión de equipo y rendimiento.
- **OA4** — Formular estrategias de mejora personalizadas a partir del análisis de su perfil de afrontamiento.

### Marco teórico

| Teoría / Modelo | Aplicación en la herramienta |
|-----------------|------------------------------|
| Modelo SCARF (Rock, 2008) | Estructura los 5 dominios de amenaza/recompensa social presentes en cada escenario |
| Teoría de la Autodeterminación (Ryan & Deci) | Base de los constructos de autonomía y competencia |
| Jerarquía de Maslow | Permite situar las amenazas en niveles de necesidades |
| Teoría bifactorial de Herzberg | Diferencia factores de higiene vs. motivadores en el feedback |
| Neurofisiología del estrés | Fundamenta las explicaciones de amígdala, cortisol y prefrontal |

### Diseño instruccional

La herramienta sigue el ciclo **Experiencia → Reflexión → Conceptualización → Experimentación** (Kolb, 1984):

1. **Experiencia** — Escenario narrativo inmersivo (alta fidelidad psicológica).
2. **Reflexión** — Selección explícita de reacción propia.
3. **Conceptualización** — Feedback inmediato con base neurocientífica.
4. **Experimentación** — Informe personalizado con área de oportunidad accionable.

---

## Características técnicas

- ✅ **Vanilla JS** — Sin dependencias de framework (React, Vue, Angular).
- ✅ **CSS custom properties** — Tematización completa sin preprocesador.
- ✅ **Canvas 2D API** — Gráfico de barras nativo, sin librería de charts.
- ✅ **localStorage** — Persistencia automática del progreso entre sesiones.
- ✅ **jsPDF** (CDN, cargado diferido) — Exportación de informes en PDF.
- ✅ **Módulos JSDoc** — 100% de funciones documentadas.
- ✅ **Sin console.log** en producción.
- ✅ **Sin eval()** ni código inseguro.

---

## Estructura del proyecto

```
simulador/
├── index.html              # HTML semántico principal (punto de entrada)
├── css/
│   └── simulador.css       # Estilos completos con custom properties
├── js/
│   └── app.js              # Lógica de aplicación (modular, JSDoc)
├── docs/
│   ├── ACCESSIBILITY.md    # Informe de cumplimiento WCAG 2.1 AA
│   ├── BROWSER_COMPAT.md   # Resultados de pruebas en navegadores
│   └── PERFORMANCE.md      # Informe de optimización de rendimiento
└── README.md               # Este archivo
```

---

## Instalación local

### Requisitos previos

- Navegador moderno (Chrome ≥ 90, Firefox ≥ 88, Safari ≥ 14, Edge ≥ 90).
- Servidor local de archivos estáticos (para evitar restricciones CORS en Chrome con `file://`).

### Opción A — Extensión Live Server (VS Code)

```bash
# 1. Clona el repositorio
git clone https://github.com/TU_USUARIO/simulador-autogestion.git
cd simulador-autogestion

# 2. Abre en VS Code
code .

# 3. Instala la extensión "Live Server" (ritwickdey.liveserver)
# 4. Haz clic derecho en index.html → "Open with Live Server"
```

### Opción B — Python (sin dependencias)

```bash
# Python 3
python -m http.server 8080

# Luego visita: http://localhost:8080
```

### Opción C — Node.js (npx, sin instalación global)

```bash
npx serve .
# Luego visita: http://localhost:3000
```

---

## Despliegue en GitHub Pages

### Paso 1 — Crear repositorio en GitHub

```bash
# Inicializa git (si aún no está inicializado)
git init
git add .
git commit -m "feat: initial release v2.0.0 — production-ready educational simulator"
```

### Paso 2 — Conectar con GitHub

```bash
# Reemplaza TU_USUARIO y TU_REPO con tus datos
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git branch -M main
git push -u origin main
```

### Paso 3 — Habilitar GitHub Pages

1. En el repositorio, ve a **Settings → Pages**.
2. En **Source**, selecciona `Deploy from a branch`.
3. Rama: `main`, Directorio: `/ (root)`.
4. Haz clic en **Save**.
5. Después de ~2 minutos, la URL estará disponible en:
   `https://TU_USUARIO.github.io/TU_REPO/`

### Paso 4 — Flujo de trabajo continuo (CI/CD básico)

Para deploys automáticos en cada push:

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

---

## Guía de personalización

### Cambiar colores del tema

Edita las variables en `css/simulador.css` bajo `:root { ... }`:

```css
:root {
  --color-ataque:     #f43f5e;  /* Color para respuesta de ataque */
  --color-huida:      #f59e0b;  /* Color para respuesta de huida */
  --color-regulacion: #10b981;  /* Color para respuesta de regulación */
  --color-indigo:     #6366f1;  /* Color de acento principal */
}
```

### Añadir nuevos escenarios

Agrega un objeto al array `SCENARIOS` en `js/app.js` siguiendo esta estructura:

```javascript
{
  title: 'Título del Escenario',
  context: 'Contexto narrativo completo aquí...',
  options: [
    {
      text: 'Texto completo de la opción de ataque.',
      type: 'ataque',
      short: 'Ataque (sistema simpático)',
      ariaLabel: 'Opción A: descripción para lector de pantalla'
    },
    // ... opciones huida y regulacion con la misma estructura
  ],
  feedback: {
    ataque: 'Retroalimentación para respuesta de ataque.',
    huida: 'Retroalimentación para respuesta de huida.',
    regulacion: 'Retroalimentación para respuesta de regulación.'
  },
  neuro: 'Base neural del escenario.'
}
```

> ⚠️ **Importante:** actualiza también `TOTAL_SCENARIOS` si añades más de 3 escenarios.

### Cambiar tipografía

Reemplaza las fuentes en `index.html` (etiqueta `<link>` de Google Fonts) y las variables en el CSS:

```css
:root {
  --font-body:    'Tu Fuente', sans-serif;
  --font-display: 'Tu Fuente Display', serif;
}
```

---

## Accesibilidad (WCAG 2.1 AA)

Ver informe completo en [`docs/ACCESSIBILITY.md`](docs/ACCESSIBILITY.md).

| Criterio WCAG | Nivel | Estado |
|---------------|-------|--------|
| 1.1.1 Contenido no textual | A | ✅ Todos los íconos tienen `aria-label` o `aria-hidden` |
| 1.3.1 Info y relaciones | A | ✅ Estructura semántica con `<section>`, `<nav>`, `<article>` |
| 1.4.3 Contraste mínimo | AA | ✅ Ratio mínimo 4.5:1 (texto pequeño), 3:1 (texto grande) |
| 2.1.1 Teclado | A | ✅ Totalmente navegable con Tab + Enter + dígitos 1-3 |
| 2.4.1 Omitir bloques | A | ✅ Skip link implementado |
| 2.4.3 Orden del foco | A | ✅ Secuencia lógica de tabulación |
| 2.4.7 Foco visible | AA | ✅ `:focus-visible` con anillo de contraste |
| 3.1.1 Idioma de la página | A | ✅ `lang="es"` en `<html>` |
| 4.1.2 Nombre, función, valor | A | ✅ `aria-pressed`, `aria-live`, `role` correctos |

---

## Compatibilidad de navegadores

Ver informe completo en [`docs/BROWSER_COMPAT.md`](docs/BROWSER_COMPAT.md).

| Navegador | Versión mínima | Estado |
|-----------|---------------|--------|
| Chrome | 90+ | ✅ Completo |
| Firefox | 88+ | ✅ Completo |
| Safari | 14+ | ✅ Completo |
| Edge | 90+ | ✅ Completo |
| Chrome Mobile | 90+ | ✅ Completo |
| Safari iOS | 14+ | ✅ Completo |

**Nota:** `ctx.roundRect()` (Canvas 2D) requiere Chrome 99+, Firefox 112+, Safari 15.4+. Para navegadores anteriores, el gráfico degrada graciosamente a rectángulos con esquinas rectas.

---

## Rendimiento

Ver informe completo en [`docs/PERFORMANCE.md`](docs/PERFORMANCE.md).

| Métrica | Valor objetivo | Estado |
|---------|---------------|--------|
| First Contentful Paint | < 1.2 s | ✅ ~0.8 s (red rápida) |
| Time to Interactive | < 2 s | ✅ ~1.1 s |
| Total JS (sin jsPDF) | < 30 KB | ✅ ~18 KB |
| Total CSS | < 12 KB | ✅ ~9 KB |
| Sin bloqueo de render | — | ✅ Fuentes + jsPDF diferidos |
| localStorage | Síncrono | ✅ Envuelto en try/catch |

---

## Control de versiones (Convenciones)

```
feat:     nueva funcionalidad
fix:      corrección de error
docs:     actualización de documentación
style:    cambios de formato/CSS sin lógica
refactor: refactorización sin cambio de comportamiento
perf:     mejora de rendimiento
a11y:     mejora de accesibilidad
```

Ejemplo:
```bash
git commit -m "fix: prevent chart re-render on non-report screens"
git commit -m "feat: add scenario 4 — conflict management under deadline"
git commit -m "a11y: improve focus management on screen transitions"
```

---

## Licencia

MIT License — libre uso educativo, modificación y redistribución con atribución.

---

*Desarrollado siguiendo estándares WCAG 2.1 AA, SCORM-ready, y mejores prácticas de tecnología educativa.*
