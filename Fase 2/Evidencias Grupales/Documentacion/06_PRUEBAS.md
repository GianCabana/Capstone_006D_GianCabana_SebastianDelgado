# Pruebas de Kippu

## Resultado de revisión

Se revisó la rama `diseno-kippu` en el commit `47190fe`. La suite encontró 198 pruebas. En una base SQLite temporal se ejecutaron 194 correctamente y se omitieron 4 pruebas de concurrencia porque SQLite no admite el bloqueo `SELECT FOR UPDATE` requerido por esos casos. El registro completo está en `evidencias/resultado_pruebas_revision.txt`.

La revisión bloqueó llamadas externas y las pruebas de Webpay usaron dobles de prueba. Por ello, este resultado no demuestra un pago real ni una prueba integral contra PostgreSQL.

## Cobertura existente

- Carta, diseño, archivos estáticos e imágenes.
- Locales, mesas y separación del catálogo.
- Carrito con HTMX, límites y protección CSRF.
- Opciones, recargos, propina y mayoría de edad.
- Pago previo, rechazo, cancelación y recuperación.
- Reintento con token nuevo e idempotencia.
- Cocina, entregas, caja y cierre de cuenta.
- Nombre de pedido y servicio abierto o cerrado por QR.

## Pruebas pendientes

| Tipo | Prueba | Evidencia requerida |
|---|---|---|
| Integración | Ejecutar las 198 pruebas con PostgreSQL | Salida completa del comando y versión de PostgreSQL |
| Integración externa | Completar un pago en Webpay de integración | Capturas sin datos sensibles y comprobante |
| Rendimiento | Medir carta y carrito con 50 usuarios durante 2 minutos | Script, equipo, percentiles y errores |
| Seguridad | Ejecutar `manage.py check --deploy` con configuración de producción | Resultado y justificación de advertencias |
| Seguridad | Revisar dependencias y secretos versionados | Informe de `pip-audit` y búsqueda de secretos |
| Compatibilidad | Probar Chrome o Edge y un teléfono | Matriz con versión y resultado |
| Recuperación | Reiniciar Docker conservando PostgreSQL | Registro antes y después del reinicio |

## Comandos

```powershell
python manage.py check
python manage.py makemigrations --check --dry-run
python manage.py test
```
