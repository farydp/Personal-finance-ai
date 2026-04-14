# 📂 Categorías de Gastos e Ingresos — Colombia

> Referencia para clasificación automática de transacciones.
> Usar cuando el usuario reporte un movimiento sin especificar categoría.

---

## Categorías de Gastos

| Categoría | Subcategoría | Ejemplos típicos |
|---|---|---|
| 🍽️ Alimentación | Mercado | Compras de plaza, tienda, supermercado |
| 🍽️ Alimentación | Comidas fuera | Restaurante, almuerzo corriente, domicilio, cafetería |
| 🍽️ Alimentación | Snacks/antojos | Tienda, dulces, gaseosa, helado |
| 🚗 Transporte | Moto | Gasolina, aceite, mantenimiento, SOAT |
| 🚗 Transporte | Uber/InDriver | Cuando usa servicio como pasajero |
| 🚗 Transporte | Bus/TransMilenio | Pasajes, recarga tarjeta |
| 🏠 Vivienda | Arriendo | Pago mensual de arriendo |
| 🏠 Vivienda | Servicios públicos | Luz, agua, gas, internet, teléfono |
| 🏠 Vivienda | Hogar | Elementos de aseo, reparaciones, utensilios |
| 💳 Deudas | Tarjeta crédito | Pago cuota Nu, Bancolombia, etc. |
| 💳 Deudas | Préstamo personal | Pago a familiar o amigo |
| 💳 Deudas | Crédito formal | Banco, cooperativa, fintech |
| 📱 Tecnología | Celular | Plan, recargas, accesorios |
| 📱 Tecnología | Suscripciones | Netflix, Spotify, apps |
| 🏋️ Salud y bienestar | Gimnasio | Mensualidad gym |
| 🏋️ Salud y bienestar | Médico/farmacia | Consultas, medicamentos |
| 🏋️ Salud y bienestar | Suplementos | Proteína, vitaminas, pre-workout |
| 👔 Personal | Ropa y calzado | Prendas, ropa deportiva |
| 👔 Personal | Aseo personal | Corte de cabello, productos de higiene |
| 🎉 Ocio | Salidas | Rumbas, eventos, cine |
| 🎉 Ocio | Fútbol | Canchas, implementos |
| 📚 Educación | Cursos | Platzi, cursos online, libros |
| 🔧 Varios | Imprevistos | Gastos no planeados difíciles de categorizar |

---

## Categorías de Ingresos

| Categoría | Ejemplos típicos |
|---|---|
| 🚗 Uber / Plataformas | Ganancias diarias de Uber, InDriver, Rappi |
| 📖 Clases particulares | Clases de matemáticas, inglés, programación, etc. |
| 💻 Freelance / Servicios | Desarrollo web, soporte técnico, instalaciones CCTV |
| 👨‍👩‍👧 Apoyo familiar | Transferencias de papás, hermanos, familiares |
| 💰 Préstamo recibido | Plata prestada (registrar también como deuda) |
| 🎁 Regalo | Dinero recibido como regalo |
| 🔄 Devolución | Plata que le devolvieron de algo |
| 📦 Venta | Venta de objetos, cosas usadas |
| 🏦 Otros ingresos | Cualquier ingreso que no encaje arriba |

---

## Reglas de clasificación automática

### Por palabras clave en el mensaje del usuario

| Si menciona... | Categoría sugerida |
|---|---|
| "luz", "recibo luz", "ESSA", "EEB" | Vivienda → Servicios públicos |
| "agua", "acueducto" | Vivienda → Servicios públicos |
| "internet", "ETB", "Claro", "Movistar" | Vivienda → Servicios públicos |
| "gasolina", "tanquear", "moto" | Transporte → Moto |
| "almuerzo", "desayuno", "cena", "comida" | Alimentación → Comidas fuera |
| "mercado", "tienda", "supermercado", "Ara", "D1", "Justo&Bueno" | Alimentación → Mercado |
| "Nu", "cuota tarjeta", "tarjeta" | Deudas → Tarjeta crédito |
| "prestó", "préstamo", "me dio" (familia) | Ingreso: Apoyo familiar + crear deuda |
| "Uber", "carrera", "servicio" | Ingreso: Uber / Plataformas |
| "clase", "estudiante", "enseñé" | Ingreso: Clases particulares |
| "gym", "gimnasio" | Salud → Gimnasio |
| "Platzi", "curso", "certificado" | Educación → Cursos |

### Ambigüedades frecuentes

| Situación | Acción |
|---|---|
| Menciona comida pero no si fue en casa o fuera | Preguntar: "¿fue en restaurante o compraste en tienda?" |
| Monto sin cuenta especificada | Preguntar: "¿de qué cuenta salió?" |
| "Me pagaron X" sin fuente clara | Preguntar: "¿fue Uber, clases u otro?" |
| Transferencia entre sus propias cuentas | No es ingreso ni gasto — es movimiento interno. Registrar aparte |

---

*Skill complementario al proyecto Finanzas IA. Actualizar categorías según los hábitos específicos del usuario.*
