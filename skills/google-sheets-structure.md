# 📊 Google Sheets MCP — Estructura y Guía de Uso

> Este skill define cómo usar Google Sheets como base de datos permanente del proyecto.
> Requiere Google Sheets MCP conectado al proyecto de Claude.

---

## Estructura de la hoja de cálculo

### Pestaña 1: Transacciones

| Columna | Tipo | Descripción |
|---|---|---|
| Fecha | Fecha (DD/MM/YYYY) | Fecha del movimiento |
| Descripción | Texto | Lo que el usuario reportó textualmente |
| Monto | Número (COP) | Monto exacto, siempre positivo |
| Tipo | Ingreso / Gasto / Movimiento interno | Tipo de transacción |
| Categoría | Texto | Ver skill `categories.md` |
| Subcategoría | Texto | Detalle adicional si aplica |
| Cuenta origen | Texto | Bancolombia / Daviplata / Nu / Efectivo / Otra |
| Cuenta destino | Texto | Solo si es movimiento interno entre cuentas |
| Notas | Texto | Contexto adicional relevante |

**Ejemplo de filas:**
```
15/04/2025 | Pago recibo luz ESSA | 85000 | Gasto | Vivienda | Servicios públicos | Bancolombia | | Vencía el 15
15/04/2025 | Carrera Uber zona norte | 32000 | Ingreso | Uber | | Daviplata | | 2 carreras juntas
15/04/2025 | Préstamo papá | 200000 | Ingreso | Apoyo familiar | | Efectivo | | Registrado como deuda también
```

---

### Pestaña 2: Cuentas

| Columna | Descripción |
|---|---|
| Nombre | Bancolombia, Daviplata, Nu, Efectivo, etc. |
| Tipo | Ahorro / Billetera digital / Tarjeta crédito / Efectivo |
| Saldo actual | Actualizar después de cada transacción |
| Última actualización | Fecha del último movimiento registrado |
| Notas | Número de cuenta, fecha de corte si aplica |

---

### Pestaña 3: Deudas

| Columna | Descripción |
|---|---|
| Acreedor | Nu, nombre de persona, banco |
| Tipo | Tarjeta crédito / Préstamo personal / Crédito formal |
| Prioridad | 🔴 Obligatoria / 🟡 Comprometida / 🟢 Flexible |
| Monto original | Cuánto se debía al inicio |
| Saldo pendiente | Cuánto falta por pagar (actualizar con cada pago) |
| Cuota mensual | Pago mínimo o acordado |
| Fecha de pago | Día del mes o fecha específica |
| Fecha de corte | Solo tarjetas de crédito |
| Estado | Al día / Próxima a vencer / Vencida |
| Notas | Tasa de interés, condiciones especiales |

---

### Pestaña 4: Pagos Recurrentes

| Columna | Descripción |
|---|---|
| Concepto | Luz, agua, internet, arriendo, etc. |
| Monto estimado | Valor promedio mensual |
| Día de vencimiento | Día del mes (ej. 15) |
| Frecuencia | Mensual / Bimestral / Anual |
| Cuenta habitual | Desde dónde se paga normalmente |
| Estado enero | Pagado ✅ / Pendiente ⏳ / N/A |
| Estado febrero | ... |
| *(columna por mes)* | |

---

### Pestaña 5: Resumen Mensual

| Columna | Descripción |
|---|---|
| Mes | Enero 2025, Febrero 2025... |
| Total ingresos | Suma de todos los ingresos del mes |
| Uber | Ingresos solo de Uber |
| Clases | Ingresos solo de clases |
| Otros ingresos | Resto |
| Total gastos | Suma de todos los gastos |
| Alimentación | Gasto en esta categoría |
| Transporte | Gasto en esta categoría |
| Servicios | Gasto en esta categoría |
| Deudas pagadas | Cuánto se abonó a deudas |
| Otros gastos | Resto |
| Balance | Ingresos - Gastos |
| Deuda total al cierre | Suma de todas las deudas ese mes |
| Notas | Contexto del mes |

---

## Comandos útiles con MCP

Cuando el usuario pida algo específico, usar estos patrones:

```
# Ver saldo de todas las cuentas
→ Leer pestaña "Cuentas", columna "Saldo actual"

# Registrar transacción
→ Agregar fila en pestaña "Transacciones"
→ Actualizar saldo en pestaña "Cuentas"
→ Si es pago de deuda: actualizar "Saldo pendiente" en pestaña "Deudas"

# Ver deudas
→ Leer pestaña "Deudas", ordenar por Prioridad y Fecha de pago

# Ver próximos pagos
→ Leer pestaña "Pagos Recurrentes", filtrar Estado = Pendiente del mes actual

# Resumen semanal
→ Leer pestaña "Transacciones", filtrar por fecha de la semana actual
→ Agrupar por Tipo y Categoría
```

---

## Si NO hay MCP conectado

Llevar el registro en el chat y recordarle al usuario al menos una vez por semana:

> "💡 Recuerda que conectar Google Sheets MCP te daría persistencia real de datos — ningún movimiento se perdería aunque cambies de chat. Puedes configurarlo en las opciones del proyecto."

---

*Skill complementario al proyecto Finanzas IA. Requiere Google Sheets MCP habilitado en el proyecto de Claude.*
