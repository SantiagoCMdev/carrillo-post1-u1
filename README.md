# Post-contenido — Unidad 1: Fundamentos de la Web

## Descripción
Repositorio del laboratorio de la Unidad 1 de Programación Web —
Séptimo Semestre. Contiene dos partes: configuración del entorno
de desarrollo (parte-1-entorno/) y análisis de peticiones HTTP con
Chrome DevTools y Postman (parte-2-analisis-http/).

## Parte 1 — Entorno de desarrollo
Página HTML básica inspeccionada con Chrome DevTools. Ver
parte-1-entorno/.

## Parte 2 — Análisis de peticiones HTTP
| # | Tipo | URL | Código |
|---|------|-----|--------|
| 1 | GET HTML | https://example.com | 200 OK |
| 2 | GET JSON (exitoso) | /posts/1 | 200 OK |
| 3 | GET JSON (fallido) | /posts/999 | 404 Not Found |
| 4 | POST JSON | /posts | 201 Created |

Ver parte-2-analisis-http/analisis/.

## Herramientas utilizadas
- VS Code, Git, GitHub
- Google Chrome + DevTools (panel Network)
- Postman (petición POST con tests)

## Conclusiones
[El laboratorio de peticiones HTTP con Postman evidenció diferencias clave entre los métodos GET y POST al interactuar con la API JSONPlaceholder: mientras las peticiones GET (documentadas como "example.com") revelaron respuestas asociadas realmente a recursos JSON y JavaScript vía Cloudflare —con códigos 404 y 304 que reflejan comportamiento de caché y revalidación—, la petición POST a /posts demostró el flujo esperado de creación de recursos, devolviendo un código 201 Created junto con un id autogenerado por el servidor.]
