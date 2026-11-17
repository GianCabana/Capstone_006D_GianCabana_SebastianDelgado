# Aportes de los integrantes

El trabajo se repartió en dos ejes (D-06, Roles y reparto del trabajo). Cada eje tiene un responsable, que construye, prueba y explica su parte:

| Eje | Responsable | Dominios |
|---|---|---|
| Eje A | Sebastián Delgado | Carta, Mesas, Pedidos, modelo de datos, panel del personal y documentación |
| Eje B | Gian Cabana | Pagos (Webpay y caja), Cocina, Entregas, Transbank, seguridad y despliegue |

El historial final de la rama `main`, en el commit `3c48e1e`, identifica 58 commits de Sebastián Delgado y 23 commits de Gian Cabana, sin contar los commits de unión (merge). Para la entrega se conserva una captura del historial final (`12_commits_equipo.png`).

## Gian Cabana · Eje B

El historial y el desarrollo compartido asocian a Gian con la construcción funcional de mesas, carrito, pedidos, pagos, Webpay, recuperación de intentos, cierre de cuentas, locales, opciones, propina, mayoría de edad, pruebas y documentación de instalación.

En la etapa final de la Fase 2 (pull requests #3 a #7 del repositorio de código), Gian preparó y publicó la aplicación: `DEBUG` desde variables de entorno y archivos estáticos con WhiteNoise, la revisión de seguridad con `check --deploy` y `pip-audit`, y la publicación en https://kippurestaurant.com con Railway y Cloudflare. También hizo que el reloj de cocina y entregas cuente desde el pago y que el nombre del pedido aparezca en el comprobante y en el aviso de pago en caja.

## Sebastián Delgado · Eje A

El historial identifica trabajo en el sistema visual, reorganización de plantillas y archivos estáticos, carta, carrito, pantallas Webpay, cocina, entregas, actualización parcial de pedidos, configuración de hosts, cierre automático por inactividad, nombre del pedido, apertura o cierre del servicio por QR, imágenes de productos y carga inicial de datos.

En la etapa final de la Fase 2 agregó el tope de unidades por producto en el carrito, actualizó el README del código y revisó y unió los pull requests del Eje B. También programó el pago en caja (13-10-2026) como apoyo al Eje B.

## Evidencia recomendada

```powershell
git shortlog -sne main
git log --oneline --format="%h %an %s" main
```

La evaluación individual debe basarse en commits y explicación oral. Este documento resume el historial; no reemplaza la revisión del repositorio.
