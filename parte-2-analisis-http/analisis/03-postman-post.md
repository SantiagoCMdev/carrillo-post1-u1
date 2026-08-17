# Análisis 3: Petición POST — jsonplaceholder.typicode.com

## Información general
- URL: https://jsonplaceholder.typicode.com/posts
- Método: POST
- Código de estado: [201 Created]
- Tiempo total: [437 ms]
- Tamaño de respuesta: [1.32 KB]

## Body de la Request (raw JSON)
```json
{
  "title": "Laboratorio Programacion Web",
  "body": "Analisis de peticiones HTTP con Postman.",
  "userId": 1
}
```

## Body de la Response (JSON)
```json
{
  "title": "Laboratorio Programacion Web",
  "body": "Analisis de peticiones HTTP con Postman.",
  "userId": 1,
  "id": 101
}
```

## Análisis del resultado
| Elemento | Valor | Significado |
|----------|-------|--------------|
| Código de estado | 201 Created | Indica que el recurso se creó exitosamente en el servidor. Es la respuesta estándar esperada tras un POST exitoso, a diferencia del 200 OK que se usa típicamente en GET. |
| Campo "id" agregado | 101 | El servidor asignó automáticamente un identificador nuevo al recurso creado, confirmando que fue registrado (aunque en JSONPlaceholder esta creación es simulada, no persiste realmente). |
| Content-Type enviado | application/json | El body se envió correctamente en formato JSON, tal como lo espera la API. |

## Observaciones
- La API JSONPlaceholder simula la creación del recurso: aunque devuelve un código 201 y un "id" nuevo, los datos **no se guardan realmente** en el servidor (es una API de pruebas/mock).
- El **id: 101** es predecible porque JSONPlaceholder siempre tiene 100 posts precargados, así que cualquier "creación" nueva recibe el id 101.
- El tiempo de respuesta (437 ms) es más alto que en las peticiones GET vistas antes, lo cual es normal en un POST porque el servidor debe procesar y validar el body enviado, no solo devolver un recurso existente.

## Tests automatizados (pestaña "Scripts" → Post-res)

### Código de los tests
```javascript
pm.test("Status 201 Created", () => {
  pm.response.to.have.status(201);
});

pm.test("Respuesta incluye id asignado", () => {
  const json = pm.response.json();
  pm.expect(json).to.have.property("id");
  pm.expect(json.title).to.equal("Laboratorio Programacion Web");
});
```

### Resultado de la ejecución
| Test | Resultado | Qué valida |
|------|-----------|------------|
| Status 201 Created | ✅ PASSED | Verifica que el código de estado de la respuesta sea exactamente 201, confirmando que el recurso fue creado correctamente. |
| Respuesta incluye id asignado | ✅ PASSED | Verifica dos cosas: (1) que el JSON de respuesta tenga la propiedad `id` (prueba de que el servidor asignó un identificador al recurso creado), y (2) que el campo `title` devuelto coincida exactamente con el valor enviado en el body de la petición. |

### Métricas de esta ejecución
- Código de estado: 201 Created
- Tiempo de respuesta: 340 ms
- Tamaño de respuesta: 1.32 KB

## Observaciones sobre los tests
- Ambos tests pasaron exitosamente, lo cual confirma automáticamente (sin revisión manual) que la API se comportó como se esperaba.
- El primer test valida el **código de estado** (capa de protocolo HTTP), mientras que el segundo valida el **contenido del body** (capa de datos/aplicación). Es una buena práctica combinar ambos niveles de verificación, ya que un 201 no garantiza por sí solo que los datos devueltos sean correctos.
- El uso de `pm.expect(json).to.have.property("id")` en lugar de comprobar un valor fijo (como `id: 101`) es más robusto, porque no depende de que el id sea siempre el mismo número — solo confirma que el servidor asignó alguno.
- Automatizar estas validaciones con tests es más confiable y reproducible que revisar la respuesta manualmente cada vez, especialmente útil si esta petición se vuelve a ejecutar en el futuro (por ejemplo, en una colección o pipeline de pruebas).