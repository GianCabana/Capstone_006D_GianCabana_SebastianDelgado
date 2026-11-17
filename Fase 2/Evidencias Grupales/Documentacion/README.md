# Documentación técnica de Kippu

Esta carpeta reúne los artefactos solicitados para la Fase 2 del Proyecto APT. Los diagramas usan Mermaid para que GitHub los muestre directamente junto con su explicación.

Código documentado: repositorio `GianCabana/kippu`, rama `main`, commit `3c48e1e`. Aplicación publicada en https://kippurestaurant.com.

| Documento | Estado | Evidencia principal |
|---|---|---|
| Arquitectura | Documentado | Seis dominios en tres aplicaciones Django, PostgreSQL y Webpay |
| Modelo de datos | Documentado | Modelos y migraciones hasta `0012` |
| Diagramas UML | Documentado | Casos de uso, clases, secuencia y componentes |
| Requisitos no funcionales | Documentado | Criterios y estado verificable |
| Despliegue | Publicado | Railway con Cloudflare delante, dominio y HTTPS |
| Pruebas | Documentado | 289 pruebas en PostgreSQL, sin omitidas; `check --deploy` y `pip-audit` |
| Innovación | Documentado | Problema, diferencia y valor |
| Evidencias | Documentado | 12 capturas en `evidencias/capturas/`, según `08_EVIDENCIAS.md` |
| Aportes de los integrantes | Documentado | Ejes de trabajo e historial de Git |

Las evidencias visuales de la demostración deben guardarse en `documentacion/evidencias/capturas/` siguiendo la lista de `08_EVIDENCIAS.md`.
