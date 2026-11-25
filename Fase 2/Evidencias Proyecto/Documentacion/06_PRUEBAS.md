# Pruebas de Kippu

## Resultado de las pruebas automáticas

Se ejecutó la suite completa sobre la rama `main` en el commit `a325aef` (24-11-2026), con **PostgreSQL**. Resultado: 339 pruebas correctas, **ninguna omitida**. Las pruebas de concurrencia, que necesitan el bloqueo `SELECT FOR UPDATE` de PostgreSQL, ya corren junto con el resto. La salida completa queda en `evidencias/resultado_pruebas_final.txt`.

Las pruebas de Webpay usan dobles de prueba del SDK de Transbank. Por ello, este resultado no demuestra por sí solo un pago en el ambiente de integración; esa prueba se registra aparte (ver Pruebas pendientes).

## Cobertura existente

- Carta, diseño, archivos estáticos e imágenes.
- Locales, mesas y separación del catálogo.
- Carrito con HTMX, límites por producto y protección CSRF.
- Opciones, recargos, propina y mayoría de edad.
- Pago previo con Webpay, rechazo, cancelación y recuperación.
- Reintento con token nuevo e idempotencia.
- Pago en caja: pedido por pagar, cobro por el personal, cancelación y vencimiento a los 30 minutos.
- Cocina, entregas, caja y cierre de cuenta; el reloj de cocina y entregas cuenta desde el pago.
- Nombre del pedido, también en el comprobante de Webpay y en el aviso de pago en caja.
- Servicio abierto o cerrado por QR.
- Configuración de publicación: `DEBUG` desde variables de entorno, ajustes de HTTPS, origen de confianza de CSRF y entrega de fotos sin salir de la carpeta `/media`.

## Pruebas de seguridad

Ejecutadas el 05-11-2026 durante la preparación del despliegue y repetidas el 15-11-2026 sobre `main` (commit `b5cb067`) para la evidencia. La salida del 15-11, con el estado antes y después de las correcciones, está en `evidencias/seguridad_check_deploy_pip_audit.txt`.

### `manage.py check --deploy`

Con la configuración de producción (`DEBUG` apagado), Django informó cuatro advertencias: HSTS sin configurar (W004), sin redirección a HTTPS (W008) y cookies de sesión y CSRF sin el atributo `Secure` (W012 y W016). Se corrigieron con la variable `DJANGO_HTTPS`, que se activa solo en el sitio publicado. Quedan dos advertencias, justificadas:

| Advertencia | Motivo para no activarla todavía |
|---|---|
| W005 · HSTS en subdominios | El dominio se publicó recién y no está definido qué subdominios tendrá |
| W021 · Precarga de HSTS | La lista de precarga exige HSTS de al menos un año y es difícil de revertir; por ahora HSTS dura una hora |

### `pip-audit`

| Paquete | Resultado | Acción |
|---|---|---|
| Pillow 12.3.0 | 39 vulnerabilidades conocidas el 05-11 (42 el 15-11, porque la base de vulnerabilidades sumó avisos nuevos) | Corregido: actualizado a 13.0.0, que no registra vulnerabilidades |
| marshmallow 3.26.1 | 1 vulnerabilidad (PYSEC-2026-1605 / CVE-2025-68480, consumo excesivo de CPU en `Schema.load(many=True)`); `pip-audit` la lista dos veces con el mismo identificador | Justificado: la exige `transbank-sdk` 6.1.0, la última versión publicada. Kippu no la usa directamente; el SDK la usa para leer respuestas de Transbank, no datos del cliente |

## Pruebas pendientes

| Tipo | Prueba | Evidencia requerida |
|---|---|---|
| Integración externa | Completar un pago en Webpay de integración en el sitio publicado | Capturas sin datos sensibles y comprobante |
| Rendimiento | Medir carta y carrito con 50 usuarios durante 2 minutos | Script, equipo, percentiles y errores |
| Seguridad | Revisar secretos versionados en el historial del repositorio | Resultado de la búsqueda y acciones tomadas |
| Compatibilidad | Probar Chrome o Edge y un teléfono | Matriz con versión y resultado |
| Recuperación | Volver a desplegar el servicio y confirmar que la base y las fotos se conservan | Registro antes y después del despliegue |

## Comandos

```powershell
python manage.py check
python manage.py makemigrations --check --dry-run
python manage.py test
python manage.py check --deploy
pip-audit -r requirements.txt
```
