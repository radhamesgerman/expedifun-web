# ExpediFun — Roadmap & Vision

> Documento vivo. Captura lo que el dueño quiere construir. Revisar al inicio de cada sesión.

## Visión general
Plataforma de turismo (estilo Viator / Expedia) que conecta turistas con **touroperadores**.
ExpediFun cobra al cliente, separa su comisión + impuestos, y paga al operador automáticamente.
Trabaja con personas reales → **cualquier fallo es legalmente demandable** → la estructura debe ser robusta.

## Productos
1. **Experiences / Tours** (lo que hoy se llama "Packages") — atracciones y excursiones.
2. **Transfers** (NUEVO, alta prioridad) — traslados aeropuerto↔hotel, etc.
   El dueño indica que los transfers se venden MÁS que las atracciones porque los turistas
   necesitan moverse. Agregar ~3 touroperadores dedicados a transfers.

## Caso de uso clave — Transfer (manifiesto al operador)
Cliente compra un transfer (ej: aeropuerto→hotel, martes 5:00 PM).
El touroperador correspondiente recibe **automáticamente** un manifiesto (tipo Excel/CSV) con:
- Nombre del comprador
- Teléfono
- Correo electrónico
- País de origen
- Hora de recogida (pickup)
- Lugar de recogida
- Destino
- (probables adicionales: # pasajeros, # de vuelo, hotel, notas, idioma, equipaje)

## Pagos (automatización — requisito crítico)
En cada venta se debe separar automáticamente:
- Ganancia de ExpediFun (comisión)
- Impuestos
- Pago al touroperador → depositado/pagado de forma automática
**Solución estándar de la industria:** Stripe Connect (marketplace / split payments).
→ Requiere BACKEND + cuenta Stripe + KYC de cada operador. NO se resuelve solo con HTML.

## Pendientes de diseño (lo que SÍ puedo hacer en HTML ahora)
- [ ] Renombrar/clarificar nav: Destinations / Experiences / **Transfers** / About / Contact
- [ ] Arreglar: "Explore Trips" y "Packages" llevan al mismo lugar
- [ ] Sección **Transfers** con 3 operadores dedicados + formulario con campos del manifiesto
- [ ] Páginas de **detalle de tour** (itinerario, fotos, qué incluye, precio)
- [ ] **Sign in / cuenta** (diseño del flujo)
- [ ] Mock realista del **manifiesto del operador** (cómo se ve el "Excel" que recibe)
- [ ] Mock del **desglose de pago** (comisión / impuestos / pago operador)
- [ ] Reemplazar placeholders de galería con imágenes reales
- [ ] Quitar badge "Under construction" cuando esté listo

## Research pendiente (LUEGO, no ahora)
Investigar a fondo cómo operan los sistemas de: **Viator, Expedia, GetYourGuide, Civitatis**.
Foco: modelo de reservas, manifiestos a operadores, split de pagos, cancelaciones, marketplace.

## Infraestructura / decisiones del dueño
- GitHub: trabaja con **GitHub Desktop** (repos locales, ej. ArtDapter). Quiere también ExpediFun
  local para hacer cambios directos cómodamente. Por ahora trabaja conmigo (push remoto) + clona.
- **Higgsfield**: el dueño tiene cuenta; probar conexión más adelante para ver beneficios (imágenes/video).

## Distinción importante (front-end vs backend)
- **Lo que vive en el repo / lo que yo construyo:** el SITIO front-end (lo que el visitante ve y clica),
  flujos, páginas, prototipos clicables. Esto es el "blueprint" para un desarrollador.
- **Lo que NO es solo HTML (necesita desarrollador + servicios):** pagos reales y split automático
  (Stripe Connect), envío automático del manifiesto al operador, cuentas de usuario reales (auth),
  base de datos, e impuestos/legal. Requiere backend.
