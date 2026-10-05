# Aqua Luan — Bodega (v3, app nueva)

PWA de bodega en `bodegaaqualuan.elhyai.com`. Proyecto Firebase `luan-aqua`, el mismo que la app de pedidos y el dashboard.

## Flujo

|#|Etapa|Quién|Efecto en el stock|
|-|-|-|-|
|1|Recepción en planta|Persona 1|+ insumos (bultos, tapas, etiquetas)|
|2|Salida a producción|Persona 2|− insumos|
|3|Bodega de producto terminado|Persona 3|+ producto terminado (y **entrada** en el Inventario del dashboard)|
|4|Carga al camión|Persona 4|− producto terminado (traslado al camión; el dashboard no cambia porque la venta ya descuenta)|
|↩|Devolución del camión|Persona 4|+ producto terminado (solo producto LLENO no vendido)|
|!|Rotos / dañados|Cualquiera de la bodega|− insumos o − terminado (los de terminado también salen del dashboard)|
|±|Ajuste por conteo físico|Solo admin|corrige la diferencia|

Los envases vacíos de CAMBIO no entran a ningún stock.

## Usuarios

|Persona|Usuario de ingreso|Nombre inicial|Etapa|
|-|-|-|-|
|1|`recepcion`|PERSONA 1|Recepción|
|2|`produccion`|PERSONA 2|Producción|
|3|`terminado`|PERSONA 3|Producto terminado|
|4|`carga`|PERSONA 4|Carga + devolución|

Se crean desde **⚙ Admin → Usuarios** (botones “Persona 1…4”). El usuario de ingreso es el puesto y no cambia; el nombre se edita luego con el nombre real. Una persona puede tener varias etapas. Desactivar un usuario le bloquea el ingreso. La contraseña se cambia con la Cloud Function `resetAsesorPassword` que ya existe.

## Firestore

* `bodInsumos` — catálogo de insumos (id `CATEGORIA\_\_NOMBRE`), con mínimo para alertas.
* `bodMovimientos` — libro de movimientos; el stock se calcula sumándolos. Nada se borra: el admin **anula**.
* `productos` — el mismo catálogo de la app de pedidos.
* `inventarioMovimientos` — el mismo stock del dashboard (origen `bodega\_terminado`, `bodega\_dano`, `bodega\_ajuste`, `bodega\_anulacion`).
* Perfil en `usuarios`: `esBodega: true`, `activoBodega`, `rolesBodega: \[...]`.

Reglas completas en `firestore.rules`.

## Publicar

GitHub Pages, rama `main`, raíz. En cada versión nueva, sube `CACHE\_NAME` en `sw.js` y el `?v=` de `app.js` en `index.html`.

