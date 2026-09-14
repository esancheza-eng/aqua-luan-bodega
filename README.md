# Aqua Luan — Bodega

App del bodeguero: login + 4 pantallas (Entrada, Salida, Stock, Historial).

- Repo: https://github.com/esancheza-eng/aqua-luan-bodega
- Misma base Firebase que el dashboard (`luan-aqua`)
- Escribe en `inventarioMovimientos` (se ve en Inventario del dashboard)

## Publicar

1. Settings → Pages → Deploy from branch `main` / root
2. Dominio sugerido: `bodega.elhyai.com` (archivo `CNAME`)
3. Firebase Auth → Authorized domains → agregar `bodega.elhyai.com`

## Usuario

En Firestore, colección `usuarios`, el perfil debe tener:

```
esBodeguero: true
esAdmin: false
esSecretaria: false
rol: BODEGUERO
```
