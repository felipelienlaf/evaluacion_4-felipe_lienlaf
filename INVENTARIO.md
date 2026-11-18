# Inventario de Migración: Evaluación 2 → Evaluación 4 (React + TypeScript)

Este documento detalla los elementos recuperados desde el repositorio original de la Evaluación 2 (`felipelienlaf/portafolio-frontend`), lo que se conservó sin cambios y lo que se corrigió o amplió en la migración a React.

---

## 1. Elementos Recuperados y Conservados de la E2

| Elemento / Sección | Origen en E2 (`portafolio-frontend`) | Destino en E4 (`evaluacion_4-felipe_lienlaf`) | Estado |
| :--- | :--- | :--- | :--- |
| **Cabecera y marca personal** | `<header class="header">` con logo `"Felipe."` y subtítulo `"Ingeniería Civil en Informática"` | `src/components/Header.tsx` | Conservado y componentizado con props tipadas |
| **Sección Sobre mí** | `<section id="sobre-mi">` con foto circular (`foto-perfil.jpg`) y biografía en dos párrafos | `src/pages/SobreMiPage.tsx` + `src/data/perfilData.ts` | Conservado con datos desacoplados en TypeScript |
| **Proyecto destacado E2** | `<article class="card-proyecto">` (`Mi Primer Portafolio Web` con `proyecto1.png` y tags `HTML5`, `CSS3`) | `src/components/ProyectoCard.tsx` + `src/data/proyectosData.ts` | Conservado e integrado con filtro por etiquetas |
| **Formulario de contacto** | `<form class="form-contacto">` con campos `nombre`, `email` y `mensaje` | `src/pages/ContactoPage.tsx` | Conservado con validación controlada y alerta de éxito |
| **Pie de página** | `<footer class="footer">` con copyright 2026 UC Temuco | `src/components/Footer.tsx` | Conservado como componente reutilizable |
| **Paleta de colores y tipografía** | Variables CSS (`--primary-color`, `--secondary-color`, `--accent-color`, `--bg-color`) y fuente Google Fonts `Poppins` | `src/index.css` e `index.html` | Conservado fielmente |
| **Diseño responsivo** | Breakpoints `@media (min-width: 768px)` y `(min-width: 1024px)` | `src/index.css` | Conservado y ampliado para el menú móvil |

---

## 2. Elementos Corregidos y Mejorados en la E4

1. **Corrección del selector universal en CSS:** En `css/styles.css` de la E2 la primera regla tenía `- { box-sizing: border-box; }` en lugar de `* { box-sizing: border-box; }`. Se corrigió para garantizar el modelo de caja uniforme en todos los navegadores.
2. **Migración de anclas a React Router (`react-router-dom`):** En la E2 se navegaba mediante `#sobre-mi`, `#trabajos` y `#contacto` en un único `index.html`. En la E4 cada sección es una vista independiente (`/`, `/proyectos`, `/contacto`) más una ruta `*` (`NotFoundPage`) para URLs inexistentes.
3. **Interactividad añadida (en E2 no existía archivo `.js`):**
   - **Menú móvil desplegable:** Estado local `menuAbierto` en `Header.tsx` con atributos ARIA.
   - **Modo claro / oscuro:** Estado global mediante `ThemeContext` (`src/context/ThemeContext.tsx`) persistido en `localStorage`.
   - **Filtro de proyectos por tecnología:** Estado `tagSeleccionado` en `ProyectosPage.tsx`.
   - **Validación y confirmación en formulario:** Validación de longitud mínima y formato de correo en `ContactoPage.tsx`, reemplazando el envío estático `action="#"` de la E2.
4. **Consumo de API pública de GitHub:** Se añadió el custom hook `useGithubRepos.ts` que consulta `https://api.github.com/users/felipelienlaf/repos` con tipado estricto (sin `any`), manejo explícito de estados (`loading`, `error`, éxito), `AbortController` y caché en memoria.