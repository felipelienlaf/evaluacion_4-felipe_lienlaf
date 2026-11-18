# Declaración de Uso de Inteligencia Artificial — Evaluación N°4

**Asignatura:** Desarrollo de Frontend (`ICINF1107`)  
**Estudiante:** Felipe Lienlaf  
**Sesión de referencia:** Sesión 27 — Uso responsable y transparente de IA en desarrollo frontend  

---

## 1. Herramientas utilizadas
- **Google Gemini (asistente conversacional en navegador):** Utilizado como apoyo para planificar la arquitectura de carpetas en React + TypeScript, diseñar el custom hook de consumo de API y estructurar la documentación técnica del repositorio.
- **Visual Studio Code:** Entorno de desarrollo local utilizado para editar los archivos, revisar errores de compilación con `tsc` y ejecutar pruebas en el navegador.

---

## 2. Para qué se usaron
- Organizar la migración del portafolio estático de la Evaluación 2 (`HTML5` + `CSS3`) hacia componentes modulares en React con tipado estricto en TypeScript (sin `any`).
- Implementar el flujo de trabajo con Git (creación de rama de desarrollo, commits convencionales y estructura de Pull Request hacia `main`).
- Diseñar el hook `useGithubRepos.ts` con `fetch`, `useEffect`, `AbortController` y caché en memoria para consumir la API pública de GitHub.
- Añadir interactividad accesible en React (rutas con `react-router-dom`, `ThemeContext` para modo oscuro, menú móvil y validación de formulario).

---

## 3. Prompts principales empleados
1. *"Esta es la rúbrica de Evaluación N°4 y mi repositorio nuevo `evaluacion_4-felipe_lienlaf`. ¿Debo continuar el proyecto 3 o crear uno nuevo desde cero?"*
2. *"Necesito mover mi proyecto fuera de OneDrive para evitar bloqueos de archivos y trabajar ordenado en mi rama `felipelienlaf`."*
3. *"Este es mi `index.html` y `styles.css` de la Evaluación 2. Ayúdame a migrarlo a React + TypeScript manteniendo exactamente los colores y estructura, agregando React Router, Context API y consumo de la API de GitHub."*

---

## 4. Qué se recibió como respuesta
- Una guía paso a paso para clonar y configurar el proyecto con Vite + React + TypeScript fuera de OneDrive (`C:\Proyectos\portfolio-e4`).
- La estructura modular dividida en `src/types/portfolio.ts`, `src/data/`, `src/context/ThemeContext.tsx`, `src/hooks/useGithubRepos.ts`, `src/components/` y `src/pages/`.
- La hoja de estilos `src/index.css` basada en las variables de color y reglas responsivas de la Evaluación 2, extendida con soporte para `[data-theme='dark']` y estados de carga/error de la API.
- Plantillas base para `README.md`, `INVENTARIO.md` y el Pull Request.

---

## 5. Qué se ajustó y cómo se verificó
- **Ajustes realizados:**
  - Se verificaron y ajustaron las rutas de las imágenes locales (`foto-perfil.jpg` y `proyecto1.png`) dentro de `public/img/` para que coincidieran exactamente con los recursos de la Evaluación 2.
  - Se tomó la captura de pantalla del portafolio original (`docs/captura-e2.png`) y se enlazó en el `README.md`.
  - Se ajustó la configuración de importaciones de tipos (`import type`) para cumplir con `verbatimModuleSyntax` en TypeScript 6.
- **Cómo se verificó:**
  - Ejecución de `npm run build` (`tsc -b && vite build`) comprobando cero errores de tipado en TypeScript.
  - Pruebas manuales en `npm run dev` navegando entre `/`, `/proyectos`, `/contacto` y una ruta inexistente (`/ruta-prueba`) para validar el componente `NotFoundPage`.
  - Prueba de estados de API (carga inicial, renderizado de repositorios de `@felipelienlaf` y caché al cambiar de pestaña) y validación del formulario de contacto con campos vacíos y válidos.
  - Auditoría de accesibilidad y rendimiento con Chrome Lighthouse.

---

## 6. Reflexión final
El uso de Inteligencia Artificial aceleró la estructuración inicial del proyecto en React + TypeScript y me permitió aplicar patrones profesionales como la separación de datos en archivos `.ts`, el uso de `AbortController` en `useEffect` y el manejo centralizado del tema con `Context API`. Sin embargo, fue indispensable comprender cada archivo generado, corregir errores de entorno (como el bloqueo de OneDrive y las rutas de activos estáticos) y validar personalmente la compilación con TypeScript y el comportamiento en el navegador. La IA funciona mejor como un copiloto técnico cuando uno mantiene el control sobre la arquitectura, revisa el código línea por línea y comprende cómo fluyen los datos y el estado en la aplicación.