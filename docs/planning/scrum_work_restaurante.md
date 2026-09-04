# Desglose del Trabajo del Restaurante

Proyecto: LA BRASA VIVA - Plataforma para restaurante tipo parrilla
Asignatura: DOSW
Entrega: Laboratorio 3 - Bloque B - Parte 5
Equipo: Carlos Sanchez, Cristian Moreno, Julian Morales
Concepto: Parrilla
Fecha: 03/09/2026

---

# Epica del Producto

## EPIC-01: Gestion integral del ciclo de pedidos y cocina para parrilla

- ID Jira: DOSW2026-1
- Tipo de issue: Epic
- Etiqueta: parrilla
- Descripcion general: Digitalizar el flujo principal del restaurante desde que el cliente o mesero configura y confirma una orden con especificaciones de parrilla hasta que la cocina prepara y despacha los platos.
- Por que existe: Elimina el uso de comandas de papel, reduce equivocaciones en los terminos de coccion solicitados verbalmente, sincroniza la disponibilidad de insumos en tiempo real y da visibilidad del estado de los pedidos.
- Que queda fuera: Facturacion electronica DIAN avanzada, pasarelas de pago, domicilios y reservas de mesas.
- Prioridad: Alta
- Justificacion de prioridad: Es el nucleo operativo del restaurante y la hipotesis que el MVP busca validar.

---

# Features

## FEAT-01: Armado y personalizacion de pedidos de parrilla

- ID Jira: DOSW2026-2
- Epica padre: EPIC-01
- Etiqueta: pedido
- Descripcion: Permite consultar la carta interactiva, seleccionar las opciones requeridas para los cortes de carne y verificar disponibilidad antes de enviar la orden.
- Prioridad: Alta
- Justificacion de prioridad: Es el punto de partida donde se originan todas las ordenes del restaurante.

## FEAT-02: Gestion y despacho en tablero de cocina

- ID Jira: DOSW2026-3
- Epica padre: EPIC-01
- Etiqueta: cocina
- Descripcion: Brinda al equipo de cocina un tablero para recibir comandas en tiempo real, controlar la capacidad de la parrilla y actualizar los estados de preparacion.
- Prioridad: Alta
- Justificacion de prioridad: Resuelve la falta de comunicacion y coordinacion entre el salon y los parrilleros.

---

# Historias de Usuario

## Historia de Usuario 1 (HU-01)

- Titulo: Seleccion de termino de coccion para cortes de parrilla
- ID Jira: DOSW2026-2
- Feature padre: FEAT-01
- Etiqueta: pedido
- Puntos de historia: 5
- Enlace video planning poker: Sesion grabada de Planning Poker del equipo (HU-01)

Formato de usuario:
Como comensal del restaurante, quiero seleccionar el termino de coccion al ordenar un corte a la parrilla, para recibir la carne en el punto exacto de mi preferencia sin errores de comunicacion.

Prioridad: Alta
Justificacion: Es la regla de negocio principal del restaurante (RN-P01). Sin el termino de coccion la cocina no puede procesar el corte.

Criterios de aceptacion:

Criterio 1:
Dado que el cliente esta en el detalle de un plato clasificado como corte de carne,
Cuando intenta agregarlo al pedido sin haber marcado un termino de coccion,
Entonces el sistema bloquea la accion y muestra un mensaje indicando que el termino es obligatorio.

Criterio 2:
Dado que el cliente selecciono un termino valido y una cantidad mayor a cero,
Cuando confirma la adicion del plato a su pedido,
Entonces el corte se agrega al pedido con su termino asignado, su precio queda congelado y el total de la cuenta se recalcula.

---

## Historia de Usuario 2 (HU-02)

- Titulo: Bloqueo de platos con ingredientes agotados
- ID Jira: DOSW2026-3
- Feature padre: FEAT-01
- Etiqueta: carta
- Puntos de historia: 3
- Enlace video planning poker: Sesion realizada en conjunto con HU-01

Formato de usuario:
Como comensal o mesero, quiero ver claramente en la carta los platos que no tienen ingredientes disponibles, para no ordenar platos que la cocina no puede preparar y evitar cancelaciones.

Prioridad: Media
Justificacion: Aplica la regla RN-02 y previene la insatisfaccion del cliente al impedir que se soliciten platos sin inventario.

Criterios de aceptacion:

Criterio 1:
Dado que un ingrediente clave fue marcado como agotado en el sistema,
Cuando el usuario entra a consultar la carta digital,
Entonces el plato se muestra deshabilitado, con texto visible de no disponible y no permite agregarlo.

Criterio 2:
Dado que un cliente intenta agregar un plato que se agoto mientras estaba en pantalla,
Cuando presiona el boton para agregarlo al pedido,
Entonces el sistema valida la disponibilidad en tiempo real, rechaza la adicion e informa que el plato ya no esta disponible.

---

## Historia de Usuario 3 (HU-03)

- Titulo: Recepcion de comandas en tablero de cocina
- ID Jira: DOSW2026-4
- Feature padre: FEAT-02
- Etiqueta: cocina
- Puntos de historia: 5
- Enlace video planning poker: Sesion realizada en conjunto con HU-01

Formato de usuario:
Como parrillero de la cocina, quiero ver en el tablero digital los pedidos entrantes con su mesa y termino de coccion, para organizar los tiempos de la parrilla por orden de llegada.

Prioridad: Alta
Justificacion: Cumple con el requerimiento de rendimiento de reflejar ordenes en menos de 2 segundos (RNF-03) y elimina las comandas fisicas.

Criterios de aceptacion:

Criterio 1:
Dado que un mesero o cliente confirma un pedido desde el salon,
Cuando el pedido entra al sistema en estado RECIBIDO,
Entonces la tarjeta del pedido aparece en el tablero de cocina en menos de 2 segundos con mesa, hora, plato y termino de coccion.

Criterio 2:
Dado que hay varios pedidos pendientes en la columna RECIBIDO,
Cuando el parrillero revisa el tablero,
Entonces los pedidos se presentan ordenados de forma cronologica indicando el tiempo transcurrido desde su confirmacion.

---

## Historia de Usuario 4 (HU-04)

- Titulo: Control de capacidad de parrilla y cambio de estado
- ID Jira: DOSW2026-5
- Feature padre: FEAT-02
- Etiqueta: cocina
- Puntos de historia: 3
- Enlace video planning poker: Sesion realizada en conjunto con HU-01

Formato de usuario:
Como parrillero, quiero cambiar el estado de un pedido y controlar la capacidad maxima de la parrilla, para no superar los 8 cortes simultaneos y registrar el avance de la preparacion.

Prioridad: Media
Justificacion: Aplica la regla RN-P02 de capacidad maxima y asegura el registro de auditoria RNF-06 en cada cambio de estado.

Criterios de aceptacion:

Criterio 1:
Dado que la parrilla ya tiene 8 cortes en estado EN PREPARACION,
Cuando el parrillero intenta pasar otro corte a preparacion,
Entonces el sistema impide el cambio, deja el pedido en cola y muestra el tiempo estimado de espera.

Criterio 2:
Dado que un pedido avanza en la secuencia valida de estados,
Cuando el parrillero pulsa para cambiar su estado,
Entonces el sistema actualiza el estado, registra el usuario y la hora del cambio, y bloquea modificaciones del pedido desde el salon.

---

# Subtareas Tecnicas

## Subtareas de HU-01 (Seleccion de termino de coccion)

- SUB-01: Disenar modelo de datos y DTO para termino de coccion en items de pedido. Responsable: Carlos Sanchez. Tipo: Backend.
DOSW2026-6
- SUB-02: Construir selector visual de termino de coccion en pantalla de detalle. Responsable: Cristian Moreno. Tipo: Frontend.
DOSW2026-7
- SUB-03: Implementar validacion en API para rechazar cortes sin termino de coccion. Responsable: Julian Morales. Tipo: Backend.
DOSW2026-8

## Subtareas de HU-02 (Bloqueo de platos agotados)

- SUB-04: Desarrollar consulta y endpoint de carta con filtro de disponibilidad. Responsable: Carlos Sanchez. Tipo: Backend.
DOSW2026-9
- SUB-05: Construir indicador visual de plato agotado en la carta digital. Responsable: Cristian Moreno. Tipo: Frontend.
DOSW2026-10
- SUB-06: Crear prueba unitaria que valide el bloqueo al agregar platos sin inventario. Responsable: Julian Morales. Tipo: QA.
DOSW2026-11

## Subtareas de HU-03 (Recepcion de comandas en cocina)

- SUB-07: Configurar mecanismo de actualizacion en tiempo real para recepcion de pedidos. Responsable: Carlos Sanchez. Tipo: Backend.
DOSW2026-12
- SUB-08: Disenar interfaz de tarjetas de comanda ordenadas por hora de llegada. Responsable: Cristian Moreno. Tipo: Frontend.
DOSW2026-13
- SUB-09: Implementar prueba de carga para verificar respuesta menor a 2 segundos. Responsable: Julian Morales. Tipo: QA.
DOSW2026-14

## SUBTAREAS DE HU-04 (Control de capacidad y estados)

- SUB-10: Programar logica de transicion entre estados validos del pedido. Responsable: Carlos Sanchez. Tipo: Backend.
DOSW2026-15
- SUB-11: Desarrollar contador de cortes activos y bloqueo de maximo 8 cortes. Responsable: Cristian Moreno. Tipo: Backend.
DOSW2026-16
- SUB-12: Implementar registro de auditoria con usuario y fecha en cambios de estado. Responsable: Julian Morales. Tipo: Backend.
DOSW2026-17

---

# Resumen de Prioridades

- Prioridad Alta: HU-01 y HU-03. Justificacion: Son indispensables para la operacion basica del salon y la cocina. Sin ellas no se puede registrar el termino ni recibir comandas.
- Prioridad Media: HU-02 y HU-04. Justificacion: Regulan el inventario de platos agotados y la capacidad de la parrilla una vez el flujo principal esta activo.
- Prioridad Baja: No aplica para esta entrega, ya que todas las historias seleccionadas son parte esencial del MVP.
