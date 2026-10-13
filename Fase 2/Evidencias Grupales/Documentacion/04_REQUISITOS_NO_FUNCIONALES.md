# Requisitos no funcionales de Kippu

| Código | Categoría | Requisito verificable | Estado |
|---|---|---|---|
| RNF01 | Seguridad | Toda modificación interna usa POST y CSRF; los paneles operativos exigen usuario staff | Implementado y cubierto por pruebas |
| RNF02 | Seguridad | El servidor calcula cantidades, opciones y montos desde datos vigentes; no confía en el total enviado por el navegador | Implementado y cubierto por pruebas |
| RNF03 | Seguridad | Las credenciales se cargan desde variables de entorno y `.env` no se versiona | Implementado; revisar secretos antes de publicar |
| RNF04 | Integridad | La autorización Webpay se compara con monto, orden y sesión antes de crear el pago | Implementado y cubierto por pruebas simuladas |
| RNF05 | Concurrencia | Los flujos de pago y cierre usan transacciones y bloqueos de filas | Implementado; pendiente ejecutar 4 pruebas en PostgreSQL |
| RNF06 | Rendimiento | La carta de una mesa debe responder en menos de 2 segundos con 50 usuarios concurrentes en el equipo de demostración | Pendiente de prueba de carga |
| RNF07 | Disponibilidad | Ante una respuesta incierta de Webpay no se crea un segundo cobro y el intento queda para revisión | Implementado y cubierto por pruebas simuladas |
| RNF08 | Escalabilidad | Los datos se separan por local y los números de mesa pueden repetirse entre locales | Implementado y cubierto por pruebas |
| RNF09 | Portabilidad | El proyecto debe levantarse con Docker Compose usando la configuración publicada | Preparado; pendiente validar en segundo computador |
| RNF10 | Usabilidad | Carta y carrito deben ser utilizables desde un teléfono y permitir operar sin JavaScript mediante redirecciones normales | Implementado; pendiente evidencia visual final |
| RNF11 | Compatibilidad | La interfaz debe funcionar en una versión reciente de Chrome o Edge y en un teléfono de la misma red | Pendiente de matriz de navegadores |
| RNF12 | Mantenibilidad | Los cambios de modelo deben incluir migración y las funcionalidades críticas deben incluir pruebas | Implementado en la versión revisada |

## Medición pendiente

Para cerrar RNF06, RNF09, RNF10 y RNF11 se debe conservar una captura o registro con fecha, equipo, versión y resultado. No deben marcarse como cumplidos solamente por disponer del código.
