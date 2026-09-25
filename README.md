# Ohana Envíos — Prototipo de interfaz

Prototipo navegable del sistema de gestión y trazabilidad de envíos para **Ohana Envíos**, una empresa de cadetería de Montevideo.

Proyecto Integrador — Analista en Tecnologías de la Información, Universidad ORT Uruguay.

---

## Qué es esto

Un prototipo de **pantallas y navegación** para validar flujos con el cliente antes de construir el sistema. No tiene backend: los datos viven en memoria y se reinician al recargar.

Sirve para responder preguntas de diseño que en un documento quedan abstractas: ¿el cadete puede confirmar una entrega con una sola mano? ¿Qué datos necesita Fernando para habilitar un cliente? ¿Cuánta información debe verse antes de tocar un botón?

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
| CU15 | Gestionar usuarios, roles y clientes | Admin → Usuarios |
| CU16 | Ver etiquetas, custodia, incidencias y reasignación | Detalle de envío |
| CU17 | Planificar rutas por paradas | Admin → Rutas |

## Decisiones de dominio que el prototipo hace visibles

**Un envío puede contener N bultos.** Todos los bultos de un mismo envío viajan juntos, hacia el mismo destino y con la misma etiqueta. Si los bultos van a lugares distintos, se registran como envíos separados.

**El código es alfanumérico y pertenece al envío.** Los bultos muestran el mismo código del envío, por ejemplo `A1053`, para mantener una referencia compacta y fácil de comunicar. El formato previsto permite reiniciar la numeración al llegar a `9999` cambiando la letra del bloque.

**Asignar no es lo mismo que custodia.** Asignar un envío define responsabilidad operativa; la custodia física recién cambia cuando el cadete confirma el retiro. Se ve en el historial de cada envío.

**No hay retiro o entrega parcial dentro del envío.** El cadete retira o entrega el envío completo. El prototipo muestra los bultos para validar identificación física, no para separar destinos.

**Planificación por jornada y por paradas.** Los envíos traen fecha de retiro desde el alta. La ruta puede mezclar retiros y entregas según convenga a la eficiencia operativa.

## Qué NO incluye

- Persistencia: al recargar vuelve al estado inicial
- Autenticación real
- Integración con servicios de rutas (Circuit u otros)
- Portal público, notificaciones y reportes reales
- Carga real de archivos o fotos: comprobantes, firmas y evidencias son visuales y siempre opcionales

## Preguntas abiertas para el cliente

El prototipo existe para resolver estas dudas con evidencia, no en abstracto:

1. ¿Qué datos exactos debe pedir Ohana antes de habilitar un cliente?
2. ¿Cuándo se permite editar, reprogramar o cancelar un envío ya creado?
3. ¿En qué casos un paquete pasa por depósito y cómo se registra la transferencia de custodia?
4. ¿La planilla de carga masiva trae una sola dirección de retiro o varias?
5. ¿Qué información debe aparecer en la etiqueta imprimible final?

## Stack

HTML, CSS y JavaScript sin dependencias ni build. Un solo archivo.

Tipografía: [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans).
