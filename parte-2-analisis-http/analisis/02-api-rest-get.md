# Análisis 2: Petición GET — example.com

## Información general
- URL:https://jsonplaceholder.typicode.com/posts/999
- Método: GET
- Código de estado: [404 Not Found]

## Headers de Request
| Header | Valor |
|--------|-------|
| Host | [jsonplaceholder.typicode.com] |
| User-Agent | [Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/151.0.0.0 Safari/537.36] |
| Accept | [text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8] |

## Headers de Response
| Header | Valor | Significado |
|--------|-------|-------------|
| Content-Type | [application/json; charset=utf-8] | [indica que la página es tipo aplicación] |
| Cache-Control | [max-age=43200] | [indica que un recurso puede ser almacenado en caché y reutilizado durante 43,200 segundos, lo que equivale a 12 horas desde el momento en que fue generado en el servidor de origen] |

## Tiempos de carga
| Fase | Tiempo (ms) |
|------|------------|
| DNS Lookup | [No sale] 
| TTFB | [177.35 ms] 

Conclusión general: los datos muestran una petición mal dirigida o a un recurso inexistente dentro de la API pública JSONPlaceholder, con una respuesta de error correctamente formateada como JSON pero con políticas de caché que quizás no son ideales para un error 404.