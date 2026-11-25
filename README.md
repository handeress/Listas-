# Listas

Listas de chequeo personales de Andrés: mercado, herramientas para llevar, compras, cosas por hacer. Se pueden compartir para trabajarlas con otra persona.

- App: https://handeress.github.io/Listas-/ (código público, sin datos). Prueba sin datos: `?demo`.
- Datos propios: repo privado `handeress/Bitacora-datos`, carpeta `listas-personales/` (un archivo por lista). Usa la misma llave de la Bitácora; si no la encuentra, se pega en Ajustes (punto de arriba a la derecha).
- Listas compartidas: repo privado `handeress/Listas-compartidas`, carpeta `c/`, **cifradas** (AES-GCM). La clave de cada lista va solo en el enlace que se comparte, así quien recibe una lista no puede abrir las demás.

## Uso

- Inicio: listas, buscar y **+** para crear. Mantener presionada una lista → borrar.
- Fila: círculo de selección · categoría (ícono; toca para elegir) · texto · ✓ hecho · ✕ cancelado · **+** nota (texto, enlaces, imágenes; se ve en color si tiene algo).
- Flechas de arriba: ordenan por categoría, texto, hecho o cancelado (otra vez = al revés). El círculo de arriba selecciona todo.
- Botones con selección: borrar (con deshacer), marcar hecho, marcar cancelado, mover a otra lista.
- **+10** agrega espacios. Compartir: «Trabajar juntos» (enlace sincronizado), «Enviar solo una copia» (texto), «Dejar de compartir».

## Tableros (segundo tipo)

Se crean con el **+ cuadrado** del inicio (el redondo crea listas). Tienen secciones con título editable y plegable, y tarjetas en 2 columnas (más en el PC): círculo de selección, + de nota, ícono grande, nombre, detalle corto, ✓ y ✕. Hay «+ tarjeta» al final de cada sección y «+ sección» al final. Mover sirve para cambiar de sección o pasar a otra lista o tablero. La flecha ↑↓ ordena cada sección. Una sección sin tarjetas llenas se puede quitar con la ✕ roja.

En el archivo: `"tipo":"tablero"`, `"secs":{"<id>":{"id","nombre","o","t"}}` y cada ítem lleva `"sec"` y `"sub"` (detalle). Claude puede mandar un tablero por el buzón: `{"tipo":"tablero","nombre":"…","secciones":[{"nombre":"…","items":[{"txt":"…","cat":"🔦","sub":"…"}]}]}`.

## Formato de una lista (`listas-personales/<id>.json`, lo escribe la app)

```json
{"id":"…","nombre":"Mercado","t":1764000000000,"items":{
  "<idItem>":{"id":"…","txt":"Leche","cat":"🛒","est":"hecho|cancelado|","nota":{"txt":"…","imgs":["data:image/jpeg;base64,…"]},"o":0,"t":1764000000000}},
 "quit":{"<idItemBorrado>":1764000000000},"borrada":false}
```

Cada ítem lleva su hora de cambio (`t`); al sincronizar gana el cambio más reciente de cada ítem. `quit` son los ítems borrados.

## Lo que manda Claude: `listas-personales/buzon/<id>.json`

```json
{"nombre":"Compras despiece cocina","items":["Tornillos 1 1/2\"",{"txt":"Cola D3","cat":"🔩","nota":"Galón"}]}
```

La app la crea una sola vez como lista `claude-<id>`. Claude no escribe en los archivos de las listas.

## Versiones

Subir `VERSION` en index.html y `CACHE` en sw.js en cada cambio. Para actualizar en el celular: cerrar y abrir dos veces con internet.

- 1.0 (24/11/2026): listas con selección, categoría, hecho, cancelado y nota; ordenar, mover, +10, buscar, compartir cifrado, sin señal, buzón de Claude.
- 1.1 (24/11/2026): engranaje para Ajustes (naranja = por enviar, rojo = error), ✓ guardar y ✕ descartar los cambios desde que se abrió la lista, línea bajo cada texto, filas más juntas, fondo verde en las hechas.
- 1.7 (24/11/2026): botón copiar (abajo, junto a compartir): solo los textos con «- » para viñetas de WhatsApp, sin las canceladas.
- 1.6 (24/11/2026): tarjetas cuadradas al estilo de la referencia (taupe y gris claro alternados, nombre arriba a la izquierda, ícono grande, detalle subrayado abajo).
- 1.5 (24/11/2026): número fijo por ítem a la izquierda (flecha para volver a ese orden) y puntos a la derecha para arrastrar y reordenar.
- 1.4 (24/11/2026): botón embudo (a la derecha de la barra): pendientes arriba, hechas y canceladas al final, automático mientras esté encendido; también en tableros.
- 1.3 (24/11/2026): tableros de tarjetas por secciones; 40 íconos.
- 1.2 (24/11/2026): hechas en taupe claro; al abrir la app entra a la última lista usada.
