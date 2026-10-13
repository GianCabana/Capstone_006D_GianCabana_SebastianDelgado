# Pendientes antes de entregar Kippu

## Prioridad alta

- Ejecutar toda la suite con PostgreSQL para incluir las 4 pruebas de concurrencia.
- Probar `docker compose up --build` en el computador de presentación.
- Completar un pago de integración de Transbank y guardar evidencia sin información sensible.
- Agregar capturas enumeradas según `08_EVIDENCIAS.md`.
- Confirmar que `.env`, `db.sqlite3`, `__pycache__`, archivos ZIP y RAR no estén versionados.
- Completar nombres, sección y docente en los Word.

## Calidad y seguridad

- Ejecutar una prueba de rendimiento y conservar sus resultados.
- Ejecutar revisión de dependencias y configuración de despliegue.
- Confirmar que los UUID de mesa no se publiquen fuera de la demostración.
- Ensayar el cierre de cuentas con y sin propina.
- Revisar los estados de Webpay abandonado antes de una demostración nueva.

## Hallazgos de repositorio

La rama revisada contenía `db.sqlite3` y archivos `__pycache__` versionados aunque `.gitignore` los excluye. Este paquete no los incluye. Deben retirarse del seguimiento de Git en la rama antes de la entrega.

El ZIP anterior tenía una versión donde el cierre comparaba el pago solo con el subtotal. La rama `diseno-kippu` ya suma `pedido.propina`, por lo que ese defecto está corregido en el código revisado.
