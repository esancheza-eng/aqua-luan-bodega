# Aqua Luan — Control de Bodega / Conductor

PWA que digitaliza la hoja **Hoja_Control_Conductor_AquaLuan**.

- Repo: https://github.com/esancheza-eng/aqua-luan-bodega
- Firebase: proyecto `luan-aqua` (mismo que pedidos/dashboard)
- Colecciones nuevas:
  - `controlesBodega` — despachos diarios
  - `productosControl` — catálogo editable
  - `alertasBodega` — alertas de faltantes / diferencias
  - `auditoriaBodega` — quién creó/modificó/cerró

## Roles
ADMINISTRADOR, BODEGUERO, ASESOR, CONDUCTOR, SUPERVISOR (campo `rol` o flags en `usuarios`).

Asesores se leen de Firestore `usuarios`. Fallback: Jefferson, Luis, Vicente, Wilson.

## Publicar
GitHub Pages branch `main` / root. Dominio `bodega.elhyai.com`.
