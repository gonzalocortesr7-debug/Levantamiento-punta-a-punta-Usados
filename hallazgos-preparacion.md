# Hallazgos — Preparación (Macro-etapa 2)

Fecha del levantamiento: 2026-04-20
Alcance: tramo operacional interno que transforma una unidad adquirida (desde cualquiera de los 6 orígenes) en una publicación competitiva en la vitrina digital de clicar.cl.

---

## Contexto

La macro-etapa **Preparación** es una de las más críticas del journey porque determina la **calidad visible** con la que una unidad llega al cliente final. El mayor punto de dolor actual es el pipeline de fotos: cuando una unidad no logra a tiempo su foto Impel con cabina virtual, termina publicándose con fotos de inspección mecánica que "ensucian" la vitrina, o —peor— sin foto, lo que la manda al fondo del catálogo con un placeholder.

### Snapshot del inventario (data real)

| Métrica | Valor | % |
|---|---|---|
| **Inventario total** | 2.574 uds | 100% |
| No disponibles para publicar | 580 uds | 22,5% |
| Disponibles para publicar | 1.990 uds | 77,5% |
| — Publicadas | 1.790 uds | 89,9% del disponible · 69,5% del total |
| — No publicadas | 200 uds | 10,1% del disponible |

### Funnel de publicabilidad

```
Inventario total (2.574)
   │
   ├─ No disponibles (580, 22,5%)
   │     ├─ Reservadas: 403 (Uds reservadas 345, Ferry Truck 57, Acopio 1)
   │     ├─ Problemas legales: 166
   │     ├─ UFM (SAIS / Falla mecánica): 9
   │     └─ No disponible: 2
   │
   └─ Disponibles (1.990, 77,5%)
         ├─ Publicadas (1.790, 89,9%)
         └─ No publicadas (200, 10,1%)
                ├─ En acopio: 166 (83%) ← causa dominante
                ├─ Sin precio: 17 (8,5%)
                ├─ Otras razones: 15 (7,5%)
                └─ Concesionario VN: 2 (1%)
```

### Orígenes de ingreso activos (5)

VPP · Compras B2B empresa · Compras B2B no empresa · Test Car · Consignados.

*Nota: la distribución % por origen aún no está cuantificada y se requiere para identificar orígenes críticos.*

### Pipeline de fotos (cobertura real del stock publicado — 1.790 uds)

| Tier | Tipo | Unidades | % |
|---|---|---|---|
| Tier 1+2 (agrupado) | Foto Impel | **1.211** | **67,7%** |
| Tier 3 | Foto inspección | 375 | 20,9% |
| Tier 4 | Sin foto (placeholder) | 204 | 11,4% |
| — | **Backlog visible (Tier 3 + 4)** | **579** | **32,3%** |

> **Limitación del BI:** el reporte vigente agrupa Tier 1 (cabina virtual 360) y Tier 2 (fondo limpio) bajo la misma categoría "IMPEL". La adopción específica de cabina virtual 360 no es cuantificable con este reporte — requiere pedir a Impel un breakdown.

### Cobertura Impel por zona

| Zona | Stock | Impel % | Inspección % | Sin foto % |
|---|---|---|---|---|
| Sur | 202 | **74,8%** ← mejor | 16,3% | 8,9% |
| Longitudinal | 266 | 68,8% | 21,4% | 9,8% |
| Temuco | 156 | 70,5% | 20,5% | 9,0% |
| Concepción | 232 | 67,7% | 18,5% | 13,8% |
| Metropolitana | 934 | **65,3%** ← peor | 22,5% | **12,2%** ← peor |

### Jerarquía real de calidad de foto (4 tiers)

| Tier | Tipo de foto                                      | Ubicación en catálogo         | Estado actual                                   |
|------|---------------------------------------------------|-------------------------------|-------------------------------------------------|
| 1    | **Foto Impel + cabina virtual 360**               | Páginas 1-2, orden refrescado | Implementado hace ~1 semana (2026-04-13). Adopción marginal. |
| 2    | **Foto Impel fondo limpio** (sin cabina virtual)  | Páginas 1-2                   | Salida estándar de Impel hoy. Mayoría del stock. |
| 3    | **Foto de inspección mecánica**                    | Auditada diariamente (medio)  | Uso "de relleno" mientras no hay foto Impel. Ensucia la vitrina. |
| 4    | **Sin foto** (placeholder "Estamos preparando esta imagen") | Fin del catálogo              | Se prefiere cuando la foto de inspección es muy mala. |

> **Aclaración terminológica:** la "cabina" en Impel NO es física. Es una capa de post-procesamiento sobre la foto tomada. La versión "fondo limpio" (Tier 2) ha sido la salida estándar; la "cabina virtual 360" (Tier 1) es una incorporación reciente que permite el look tipo estudio con pedestal giratorio y branding CLICAR.

---

## Ruta de la macro-etapa

```
Orígenes (6) ──▶ Ingreso a Quiter + ubicación ──▶ Precio ──▶ Publicación ──▶ Foto Impel ──▶ Orden en catálogo
```

Los 6 orígenes de ingreso son: VPP, VPP's, Compras B2B empresa, Compras B2B no empresa, Consignados, Test Car.

---

## Sub-etapas

### 1. Ingreso a Quiter + ubicación física
Registro de la unidad en Quiter con asignación de ubicación física, segmentado por origen.

**KPIs (TBD):**
- Volumen mensual de unidades ingresadas (TBD)
- Distribución % por origen (VPP / VPP's / B2B empresa / B2B no empresa / Consignados / Test Car) (TBD)
- Tiempo recepción física → registro en Quiter (TBD, horas)
- % unidades con ubicación correctamente asignada en sistema (TBD)
- % discrepancias ubicación sistema vs. ubicación real en auditoría (TBD)

### 2. Ingreso de precio de venta
Asignación del valor comercial a la unidad. Gate obligatorio antes de publicar.

**KPIs (TBD):**
- Tiempo Quiter → precio cargado (TBD, horas)
- % unidades con precio asignado dentro de SLA interno (TBD)
- % unidades con ajuste de precio dentro de los primeros 30 días en stock (TBD)
- Dispersión precio publicado vs. tasación ofrecida al cliente en etapa anterior (TBD, %)

### 3. Publicación en sitio web
La unidad pasa a ser visible en el catálogo.

**KPIs (TBD):**
- Lead time Quiter → publicación efectiva (TBD, horas)
- % unidades en stock publicadas vs. stock total (TBD)
- % fichas publicadas con todos los campos obligatorios completos (TBD)
- % unidades despublicadas y re-publicadas por errores de data (TBD)

### 4. Producción y post-procesado de foto Impel ⭐ CRÍTICA
Ciclo completo desde la toma de foto de producto hasta el procesamiento Impel (fondo limpio y/o cabina virtual 360).

**KPIs (TBD):**
- Capacidad instalada del pipeline Impel (TBD, unidades/día)
- Throughput real (TBD, unidades/día) y utilización vs. capacidad (TBD, %)
- Backlog de unidades publicadas esperando foto Impel (TBD)
- Tiempo publicación → foto Impel lista (TBD, días)
- **% fotos Impel con tratamiento de cabina virtual 360** (TBD) ← KPI nuevo desde 2026-04-13
- **% unidades que NUNCA reciben foto Impel** (TBD)
- Distribución % de causas raíz de no-procesamiento (TBD): capacidad / daño estético / operacional / otras
- Tasa de rework de fotos rechazadas (TBD, %)

### 5. Clasificación y orden en catálogo ⭐ CRÍTICA (efecto visible)
Resultado operativo del pipeline. Determina dónde y cómo aparece la unidad en el catálogo.

**KPIs (TBD) — el más importante es la distribución de tiers:**
- Distribución % del stock publicado por tier (TBD):
  - Tier 1 · cabina virtual 360 — objetivo aspiracional: ≥X%
  - Tier 2 · Impel fondo limpio — aceptable
  - Tier 3 · foto inspección — objetivo: ≤Y%
  - Tier 4 · sin foto (placeholder) — objetivo: ≈0%
- Días en stock promedio por tier (TBD) ← evidencia del impacto comercial
- Tasa de conversión (leads, visitas, reservas) por tier (TBD)
- Tiempo de permanencia promedio en Tier 3 antes de upgrade (TBD, días)
- Tiempo de permanencia promedio en Tier 4 antes de upgrade (TBD, días)
- % páginas top del catálogo (páginas 1-3) con unidades Tier 3 presentes (TBD)
- % páginas del catálogo con al menos un placeholder Tier 4 visible (TBD)

---

## Hallazgos iniciales

### Con data real (snapshot actual)

1. **22,5% del inventario está inmovilizado**: 580 de 2.574 unidades no son elegibles para publicar. El 69% de esas no-disponibles son **reservadas** (403 uds, incluyendo 345 reservadas + 57 Ferry Truck + 1 Acopio). Requiere entender cuántas son reservas comerciales activas vs. reservas fantasma.

2. **La vitrina solo muestra 69,5% del inventario**: 1.790 de 2.574 unidades están publicadas. Entre el no-disponible (580) y el retenido-disponible (200) se pierden 784 unidades en el camino.

3. **"En acopio" domina las retenciones del stock disponible**: 166 de 200 unidades retenidas (83%) están en estado "En acopio", una categoría que hoy funciona como cajón de sastre y requiere desagregarse en causas accionables (recién llegado, pendiente limpieza, pendiente documentación, etc.).

4. **17 unidades bloqueadas por falta de precio**: gate operacional concreto. Representan 8,5% de las retenciones y son el bloqueo más fácil de resolver con un SLA claro.

5. **166 unidades con problemas legales**: volumen relevante que requiere cruce con el área legal para entender tipología (dominio, deuda, siniestro, etc.) y priorizar resolución.

6. **9 unidades en UFM (SAIS / Falla mecánica)**: bajo volumen pero flag de calidad de compra en origen — ¿qué criterio permitió ingresarlas?

7. **"Otras razones" (15 uds) y "Concesionario VN" (2 uds)** deberían disolverse: la primera por ser una categoría sin accionabilidad clara, la segunda por ser volumen marginal que indica stock que no debería estar en este pool.

### Sobre el pipeline de fotos (sin datos aún)

8. **La cabina virtual 360 es una capacidad muy reciente** (implementada ~2026-04-13). La adopción masiva todavía no ocurre; la mayoría del stock sigue saliendo con foto Impel fondo limpio (Tier 2).

9. **Cuando una unidad se publica antes de tener foto Impel lista, se rellena con foto de inspección mecánica.** Estas fotos fueron capturadas en ambientes reales (estacionamiento con otros autos, matrículas visibles, árboles, etc.) y no están diseñadas para uso comercial. El resultado es que la vitrina digital proyecta una imagen inconsistente con el posicionamiento premium del producto.

10. **Cuando la foto de inspección es considerada muy fea, el negocio prefiere publicar sin foto** (placeholder "Estamos preparando esta imagen"). Esto manda la unidad al fin del catálogo, donde prácticamente pierde visibilidad.

11. **Evidencia concreta en producción (2026-04-20):** en `clicar.cl/seminuevos-lujo?page=6` (página 6 del catálogo de lujo), los 3 primeros vehículos del grid son placeholders sin foto: Lexus RX 2.5 LUX Hybrid ($58.190.000), Volvo XC90 2.0 T8 Hybrid ($46.990.000) y BMW X5 3.0 M Sport ($85.890.000). Se trata de unidades premium de alto ticket donde el impacto del "sin foto" es máximo.

12. **El criterio "mejor sin foto que con foto fea" es subjetivo y no documentado.** Cada operador decide cuándo una foto de inspección es "aceptable" y cuándo no. No hay umbrales objetivos ni checklist.

13. **No existen indicadores activos del pipeline de fotos.** No se mide backlog, capacidad instalada, throughput, ni SLA entre publicación y foto Impel lista. Lo que no se mide, no se gestiona.

14. **Los 5 orígenes de ingreso conviven en un mismo pipeline aguas abajo,** pero no está claro si reciben el mismo SLA de preparación. Unidades de origen VPP o Test Car podrían tener flujos distintos que Consignados o Compras B2B, con impactos en tiempos que hoy no se ven.

---

## Mejoras a trabajar (borrador inicial)

### Corto plazo (próximos 30 días)
- Instrumentar el pipeline de fotos: medir backlog, throughput, tiempo publicación → Impel.
- Definir SLA explícito de "publicación → foto Impel lista" (ej. <48h).
- Documentar criterios objetivos para publicar con foto de inspección vs. sin foto (checklist: iluminación, entorno, matrícula visible, ángulo, daño visible).
- Priorizar cabina virtual 360 en el stock premium (lujo, tickets altos).

### Mediano plazo (60-90 días)
- Escalamiento de cabina virtual 360 al 100% del stock procesable por Impel.
- Dashboard operativo de tiers en tiempo real (distribución, backlog, alertas).
- Alerta automática cuando un auto lleva >N días en Tier 3 o Tier 4.
- Regla de negocio: no publicar unidades de segmentos premium sin foto Impel lista.

### Largo plazo
- Integración automática CRM ↔ Impel: al publicarse en sitio, la unidad entra automáticamente al pipeline de foto con SLA.
- Reutilización de fotos de inspección de alta calidad (captura guiada ya en sucursal) para producir tier intermedio si Impel no alcanza.
- Auditoría automatizada de vitrina con detección de "suciedad visual" (IA sobre fotos publicadas).

---

## Preguntas abiertas para el equipo

- ¿Cuál es la capacidad real actual del pipeline Impel?
- ¿Cuántas unidades por día se están logrando con cabina virtual 360 desde su implementación?
- ¿Existe algún número oficial de tiempo promedio entre "publicada" y "con foto Impel lista"?
- ¿Qué % del stock premium termina en Tier 3 o Tier 4?
- ¿Hay SLA contractual o interno con Impel? ¿Qué ocurre cuando se incumple?
- ¿Los 6 orígenes tienen el mismo flujo aguas abajo o hay variantes operacionales?
- ¿Qué rol juega el equipo de Marketing/Contenido en la auditoría diaria de fotos de inspección publicadas?
