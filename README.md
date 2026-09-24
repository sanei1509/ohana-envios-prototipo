# Ohana Envíos — Prototipo de interfaz

Prototipo navegable del sistema de gestión y trazabilidad de envíos para **Ohana Envíos**, una empresa de cadetería de Montevideo.

Proyecto Integrador — Analista en Tecnologías de la Información, Universidad ORT Uruguay.

---

## Qué es esto

Un prototipo de **pantallas y navegación** para validar flujos con el cliente antes de construir el sistema. No tiene backend: los datos viven en memoria y se reinician al recargar.

Sirve para responder preguntas de diseño que en un documento quedan abstractas: ¿el cadete puede confirmar una entrega con una sola mano? ¿Hace falta entrega parcial? ¿Cuánta información necesita ver antes de tocar un botón?

## Cómo verlo

Abrí `index.html` en cualquier navegador. No requiere instalación ni dependencias.

Está diseñado **mobile-first** — se ve mejor en un teléfono o con las herramientas de desarrollo en vista móvil (390 × 844).

## Roles

El selector de arriba cambia entre los tres perfiles:

| Rol | Qué hace |
|---|---|
| **Admin** | Fernando: planifica jornadas, asigna cadetes, carga envíos y planillas |
| **Cadete** | Martín: ve sus tareas, confirma retiros y entregas |
| **Cliente** | Boutique Amalia: consulta el estado de sus envíos |

## Casos de uso cubiertos

| CU | Nombre | Dónde |
|---|---|---|
| CU01 | Registrar envío | Admin → Nuevo |
| CU02 | Buscar y consultar envío | Admin → Envíos |
| CU03 | Planificar jornada | Admin → Inicio |
| CU04 | Asignar o reasignar envío | Admin → Inicio → Asignar |
| CU05 | Consultar tareas asignadas | Cadete → Tareas |
| CU06 | Confirmar retiro | Cadete → Confirmar retiro |
| CU08 | Confirmar entrega | Cadete → Confirmar entrega |
| CU09 | Cargar envíos masivamente | Admin → Cargar |
| CU11 | Consultar historial del envío | Detalle de cualquier envío |
| CU13 | Gestionar repartidores | Admin → Equipo |
| CU14 | Consultar envíos del cliente | Cliente → Envíos |

## Decisiones de dominio que el prototipo hace visibles

**Un envío contiene N bultos.** El código, el estado y la custodia viven a nivel bulto, no del envío. Esto habilita el **retiro y la entrega parcial**: el cadete puede llevarse 3 de 4 cajas y el sistema lo representa correctamente.

**Asignar no es lo mismo que custodia.** Asignar un envío define responsabilidad operativa; la custodia física recién cambia cuando el cadete confirma el retiro. Se ve en el historial de cada envío.

**Estado derivado.** El estado del envío se calcula a partir de sus bultos: todos entregados → entregado; algunos → entrega parcial.

**Planificación por jornada.** Los envíos traen fecha de retiro desde el alta. Se puede planificar hoy, mañana o cualquier día hábil de las próximas dos semanas. Los envíos que quedaron sin resolver de días anteriores aparecen marcados, con dos salidas: reprogramar o devolver al remitente.

## Qué NO incluye

- Persistencia: al recargar vuelve al estado inicial
- Autenticación real
- Integración con servicios de rutas (Circuit u otros)
- Etiquetas imprimibles, portal público, notificaciones y reportes

## Preguntas abiertas para el cliente

El prototipo existe para resolver estas dudas con evidencia, no en abstracto:

1. ¿Se admite entrega parcial o los bultos de un envío viajan siempre juntos?
2. ¿El código identificatorio es del envío, del bulto, o ambos?
3. ¿Los paquetes pasan por depósito o el mismo cadete hace retiro y entrega?
4. ¿La planilla de carga masiva trae una sola dirección de retiro o varias?
5. ¿"Frágil" corresponde al envío completo o puede ser de un bulto en particular?

## Stack

HTML, CSS y JavaScript sin dependencias ni build. Un solo archivo.

Tipografía: [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans).
