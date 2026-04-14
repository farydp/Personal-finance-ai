# 💰 Contador Personal de Finanzas IA — Claude Project

Sistema de gestión financiera personal construido sobre Claude Projects. Actúa como contador personal inteligente con registro en lenguaje natural, control de deudas, recordatorios de pago y análisis de hábitos — diseñado para ingresos variables e irregulares en el contexto colombiano.

> **Caso de uso real:** Control financiero para trabajador independiente con ingresos variables (Uber, clases, freelance) sin empleo fijo.

---

## ¿Qué hace este proyecto?

### Registro en lenguaje natural
No hay formularios ni apps que llenar. Solo describes lo que pasó:
```
"Pagué la luz por $85.000"
"Hice un Uber y me gané $35.000"  
"Mi papá me prestó $200.000"
"Almorcé por $12.000 en el corriente"
```
El sistema clasifica, asocia a la cuenta correcta y actualiza saldos automáticamente.

### Control de deudas por prioridad
Clasifica deudas en tres niveles:
- 🔴 **Obligatorias** — Tarjetas, servicios, arriendo. Se pagan sí o sí
- 🟡 **Comprometidas** — Préstamos personales con familia o amigos
- 🟢 **Flexibles** — Negociables o aplazables si es necesario

### Recordatorios con presión real
No es un recordatorio genérico. El sistema escala la presión:
- 5 días antes → mención suave
- 2 días antes → presión directa con monto exacto
- Día del vencimiento → alerta urgente

### Análisis basado en datos reales
No consejos genéricos. Observaciones como: *"gastaste $180.000 en comida esta semana, 40% más que la anterior"* o *"¿seguro que necesitas eso? Tienes $XXX pendientes en Nu"*.

### Persistencia con Google Sheets MCP
Cuando se conecta Google Sheets MCP, cada transacción se registra en tiempo real en una hoja estructurada con 5 pestañas: Transacciones, Cuentas, Deudas, Pagos Recurrentes y Resumen Mensual.

---

## Estructura del proyecto

```
finanzas-ia/
├── README.md                        ← Este archivo
├── system-prompt.md                 ← Instrucciones del sistema
├── project-goal.md                  ← Objetivos y contexto del usuario
└── skills/
    ├── categories.md                ← Categorías de gastos e ingresos + clasificación automática
    ├── google-sheets-structure.md   ← Estructura de la hoja y comandos MCP
    └── handoff-template.md          ← Plantilla de migración entre chats
```

---

## Cómo usar este proyecto

### 1. Crear el proyecto en Claude
- Ve a [claude.ai](https://claude.ai) → nuevo **Project**
- En **Custom Instructions**, pega el contenido de `system-prompt.md`

### 2. Subir los skills
- Sube los 3 archivos de `/skills` como archivos de conocimiento del proyecto

### 3. Google Sheets MCP ✅ (ya activo)
- Google Sheets MCP está conectado al proyecto
- El sistema registra cada transacción en tiempo real en la hoja estructurada
- Ver `skills/google-sheets-structure.md` para la estructura completa de pestañas

### 4. Google Calendar MCP 🔜 (próximamente)
- Permitirá crear recordatorios de pago directamente en el calendario
- Cuando esté activo, los vencimientos se agregarán automáticamente

### 5. Primera sesión
Claude te pedirá:
- Saldos actuales de cada cuenta
- Deudas existentes con montos y fechas
- Pagos recurrentes y sus vencimientos

---

## Técnicas de prompt engineering utilizadas

| Técnica | Aplicación |
|---|---|
| **Role prompting** | Claude adopta el rol de contador personal con contexto financiero colombiano |
| **Conditional behavior** | Comportamiento diferente con/sin Google Sheets MCP conectado |
| **Structured output** | Formato fijo para registros, resúmenes diarios, semanales y mensuales |
| **Escalating urgency** | Sistema de recordatorios con 3 niveles de presión según proximidad al vencimiento |
| **Memory management** | Handoff estructurado para migrar datos entre chats sin perder información |
| **Tool use instruction** | Integración explícita con Google Sheets MCP y Google Calendar MCP |
| **Grounding contextual** | Moneda COP, bancos colombianos (Bancolombia, Daviplata, Nu), cultura de pagos local |
| **Anti-hallucination rules** | Regla explícita de nunca asumir gastos no reportados ni redondear montos |

---

## Integraciones

| Herramienta | Función | Estado |
|---|---|---|
| Claude Projects | Motor principal de IA | ✅ Activo |
| Google Sheets MCP | Base de datos persistente de transacciones | ✅ Activo |
| Google Calendar MCP | Recordatorios de pago en calendario | 🔜 Próximamente |

---

## Contexto de diseño

Diseñado para un usuario en Colombia con:
- Ingresos variables e irregulares (Uber, clases, freelance)
- Múltiples cuentas: Bancolombia, Daviplata, Nu, efectivo
- Necesidad de control estricto sin apps adicionales
- Preferencia por interacción conversacional sobre formularios

El enfoque es **pragmático y directo**: sin consejos genéricos, sin redondeos, con presión real cuando hace falta.

---

## Stack

- **Claude Projects** (Anthropic) — Motor principal
- **Google Sheets MCP** — Persistencia de datos (opcional)
- **Google Calendar MCP** — Recordatorios (opcional)

---

## Licencia

MIT — Libre para adaptar a tu contexto.

---

*Proyecto desarrollado por [Faryd] | Ingeniero Electrónico & Fullstack Developer*
*Fusagasugá, Colombia 🇨🇴*
