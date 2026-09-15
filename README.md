# Aqua Luan — Control de Bodega / Conductor

PWA que digitaliza la hoja **Hoja_Control_Conductor_AquaLuan**.

- Repo: https://github.com/esancheza-eng/aqua-luan-bodega
- Firebase: proyecto `luan-aqua` (mismo que pedidos/dashboard)
- Colecciones nuevas:
  - `controlesBodega` — despachos diarios
  - `productosControl` — catálogo editable
  - `alertasBodega` — alertas de faltantes / diferencias
  - `auditoriaBodega` — quién creó/modificó/cerró

Usa también `inventarioMovimientos` (stock del dashboard) al cerrar/reabrir.

## Roles
ADMINISTRADOR, BODEGUERO, ASESOR, CONDUCTOR, SUPERVISOR.

Asesores desde Firestore `usuarios`. Fallback: Jefferson, Luis, Vicente, Wilson.

## Inventario al cerrar (v2)
Al cerrar: salidas de producto y envases + entradas de retornos/vacíos.
Al reabrir (admin): se eliminan esos movimientos para no duplicar stock.

## Publicar
GitHub Pages branch `main` / root. Dominio `bodega.elhyai.com`.
