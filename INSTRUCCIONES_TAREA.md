# Instrucciones de la tarea diaria del boletín

Esta tarea se ejecuta **cada mañana** en el PC de Norma. Carpeta del proyecto:
`C:\Users\norma\22q13 org\newsletter-pms`

## 1. Buscar novedades (todos los días)

1. Lee `data/sitios.json`. Contiene `actualizado` (fecha ISO) y `entradas` (lista). Toda URL que ya esté ahí se considera conocida.
2. Busca en internet (WebSearch; WebFetch si hace falta comprobar una página) webs y perfiles de redes sociales sobre el **síndrome de Phelan-McDermid**, **SHANK3** y la **deleción 22q13**, en **todos los idiomas**. Rota idiomas y redes cada día para cubrirlo todo a lo largo de la semana. Como mínimo:
   - Inglés, español, portugués, francés, italiano, alemán, neerlandés, lenguas nórdicas, polaco, ruso/ucraniano, turco, hebreo, árabe, japonés, chino y coreano (usa el nombre del síndrome en cada idioma y en su propio alfabeto).
   - Redes: Facebook (páginas y grupos), Instagram, TikTok, YouTube, X, LinkedIn, Reddit, Bluesky/Threads, podcasts, blogs de familias.
   - Prioriza lo **reciente** (búsquedas con el año en curso, «nuevo», «lanza», «crea», noticias de la semana).
3. Añade solo lo que **no esté ya** en `entradas` (compara la URL normalizada: sin `www.`, sin barra final, sin parámetros de seguimiento). **Nunca inventes una URL**: solo URLs vistas en resultados de búsqueda o abiertas.
4. Cada entrada nueva lleva exactamente estas claves:
   ```json
   {"name": "...", "url": "https://...", "type": "web|facebook|instagram|x|youtube|tiktok|linkedin|reddit|blog|podcast|registro|investigacion|otro",
    "language": "código ISO 639-1", "country": "ISO 3166 alfa-2 o INT", "topics": ["PMS","SHANK3","22q13"],
    "description": "una frase corta en español", "created": "AAAA-MM, AAAA o null", "first_seen": "AAAA-MM-DD (hoy)"}
   ```
   No pongas `"inicial": true` en las entradas nuevas: esa marca es solo para el listado de partida y hace que no salgan resaltadas.
5. Pon en `actualizado` la fecha y hora de hoy (`AAAA-MM-DDTHH:MM`), aunque no haya novedades. Guarda el JSON en UTF-8 y comprueba que sigue siendo válido.

## 2. Edición semanal (solo los miércoles)

Si hoy es **miércoles**, añade una edición a `data/ediciones.json` → `ediciones`:
```json
{"numero": <anterior + 1>, "fecha": "AAAA-MM-DD", "resumen": "3-5 frases en español con lo más destacado de la semana", "nuevas": ["urls con first_seen de los últimos 7 días"]}
```
Si ya existe una edición con la fecha de hoy, actualízala en vez de duplicarla.

## 3. Publicar

En la carpeta del proyecto, ejecuta:
```
git add -A
git commit -m "Actualización AAAA-MM-DD: N novedades"
git push
```
Si `git push` falla (sin conexión, credenciales caducadas…), no reintentes en bucle: explica el error en el resumen final.

## 4. Resumen final

Termina con un resumen breve en español: cuántas novedades, cuáles (nombre + idioma) y si se ha publicado bien.
