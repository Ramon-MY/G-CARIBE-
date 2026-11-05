# GUARDIÁN CARIBE — Wireframes y mockups

**Documento de diseño de interfaz**  
**Proyecto:** GUARDIÁN CARIBE  
**Autor:** Ramón Martínez  
**Repositorio:** [Ramon-MY/G-CARIBE-](https://github.com/Ramon-MY/G-CARIBE-)  
**Issue relacionado:** [#12 — Diseñar wireframes y mockups de GUARDIÁN CARIBE](https://github.com/Ramon-MY/G-CARIBE-/issues/12)  
**Rama de trabajo:** `mockups`  
**Versión del documento:** 1.0  
**Estado:** Propuesta inicial para revisión

---

## 1. Descripción del sistema

GUARDIÁN CARIBE es una propuesta de plataforma ligera de monitoreo de seguridad (SOC). Su propósito es centralizar eventos de seguridad, detectar comportamientos sospechosos, generar y administrar alertas, gestionar indicadores de compromiso (IoC), dar seguimiento a incidentes y conservar una bitácora de auditoría.

La interfaz se plantea para operadores y analistas de seguridad. Se priorizan la lectura rápida, la navegación consistente, el uso eficiente de recursos y la presentación clara de prioridades. Estos diseños son wireframes funcionales de referencia; no representan pantallas ya implementadas ni datos reales.

## 2. Objetivo del diseño

Definir la estructura y navegación de las pantallas principales antes de programar la interfaz. Los wireframes permiten validar qué información necesita cada rol, dónde se ubican las acciones y cómo se relacionan los módulos.

## 3. Usuarios previstos

| Perfil | Necesidad principal |
|---|---|
| Administrador | Gestionar usuarios, permisos y configuración. |
| Analista de seguridad | Revisar eventos, investigar alertas y administrar IoC. |
| Operador técnico | Supervisar el estado del servicio y apoyar la respuesta. |
| Supervisor | Consultar indicadores, incidentes y auditoría. |

Los permisos definitivos deberán aplicarse en el backend; ocultar un botón en la interfaz no sustituye la autorización del servidor.

## 4. Mapa de navegación

```text
INICIO DE SESIÓN
       |
       v
PANEL SOC / DASHBOARD
       |
       +---- Eventos
       |       +---- Detalle de evento
       |
       +---- Alertas
       |       +---- Detalle / investigación
       |       +---- Asignar / cambiar estado
       |
       +---- Incidentes
       |       +---- Crear / actualizar incidente
       |       +---- Evidencias y notas
       |
       +---- Inteligencia de amenazas (IoC)
       |
       +---- Auditoría
       |
       +---- Configuración
               +---- Usuarios y roles
               +---- Parámetros del sistema
```

## 5. Inventario de pantallas

1. Inicio de sesión.
2. Panel principal SOC (dashboard).
3. Explorador de eventos.
4. Bandeja de alertas.
5. Detalle e investigación de alerta.
6. Gestión de incidentes.
7. Inteligencia de amenazas e indicadores IoC.
8. Auditoría y actividad.
9. Configuración, usuarios y roles.

---

## 6. Wireframes de las pantallas

Los bloques representan la distribución, los controles y la jerarquía visual. Los textos entre corchetes son controles o datos de ejemplo, no información real.

### Pantalla 1 — Inicio de sesión

**Propósito:** permitir el acceso autenticado y mostrar mensajes seguros sin revelar detalles internos.

```text
+--------------------------------------------------------------+
|                     GUARDIÁN CARIBE                          |
|             Plataforma de monitoreo de seguridad            |
|                                                              |
|                 +------------------------+                   |
|                 |      INICIAR SESIÓN    |                   |
|                 |                        |                   |
|                 | Usuario / correo       |                   |
|                 | [____________________] |                   |
|                 |                        |                   |
|                 | Contraseña             |                   |
|                 | [____________________] |                   |
|                 |                        |                   |
|                 | [ ] Mostrar contraseña |                   |
|                 |                        |                   |
|                 | [      INGRESAR      ] |                   |
|                 |                        |                   |
|                 | [Mensaje de acceso]    |                   |
|                 +------------------------+                   |
|                                                              |
|             Acceso protegido · GUARDIÁN CARIBE               |
+--------------------------------------------------------------+
```

**Elementos y comportamiento:**
- Campo de usuario/correo y contraseña.
- Botón para mostrar u ocultar la contraseña.
- Mensaje genérico ante credenciales inválidas; no indicar si el usuario existe.
- Bloqueo o limitación de intentos según la política de autenticación.
- Comunicación cifrada HTTPS y protección de sesión.

### Pantalla 2 — Panel principal SOC

**Propósito:** ofrecer una visión rápida del estado de seguridad y facilitar el acceso a las tareas prioritarias.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE     [Buscar........................] [Ayuda] [Usuario v]       |
+----------------------+---------------------------------------------------------+
| MENÚ                 | PANEL SOC                         [Rango de fechas v]    |
|                      |                                                         |
| > Dashboard          | +---------------+ +---------------+ +----------------+ |
|   Eventos            | | Eventos       | | Alertas       | | Incidentes      | |
|   Alertas            | |      248      | |       12      | |        4        | |
|   Incidentes         | +---------------+ +---------------+ +----------------+ |
|   Inteligencia IoC   |                                                         |
|   Auditoría          | +--------------------------------+ +----------------+  |
|   Configuración      | | Eventos por período            | | Alertas por     |  |
|                      | | [Gráfico de tendencia]         | | severidad       |  |
|                      | |                                | | [Crítica: 2]    |  |
|                      | |                                | | [Alta: 5]       |  |
|                      | +--------------------------------+ | [Media: 5]      |  |
|                      |                                    +----------------+  |
|                      | +---------------------------------------------------+  |
|                      | | ALERTAS RECIENTES                                 |  |
|                      | | ID | Título | Severidad | Estado | Fecha          |  |
|                      | | 12 | Acceso | Alta      | Abierta| ...            |  |
|                      | | 11 | Tráfico| Media     | En rev.| ...            |  |
|                      | +---------------------------------------------------+  |
+----------------------+---------------------------------------------------------+
| Estado del servicio: [Indicador]     Última actualización: [fecha/hora]       |
+--------------------------------------------------------------------------------+
```

**Elementos y comportamiento:**
- Indicadores agregados de eventos, alertas e incidentes.
- Gráfico temporal y distribución por severidad.
- Tabla de alertas recientes con acceso al detalle.
- Filtro por período.
- Indicador de estado del servicio y hora de actualización.
- Los contadores deben proceder de datos consultados, no de valores ficticios en producción.

### Pantalla 3 — Explorador de eventos

**Propósito:** buscar, filtrar y consultar los eventos recibidos por la plataforma.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                                      EVENTOS                   |
+----------------------+---------------------------------------------------------+
| MENÚ                 | EVENTOS DE SEGURIDAD                                   |
|   Dashboard          | [Buscar por IP, usuario, origen o texto.............]  |
| > Eventos            | [Desde fecha] [Hasta fecha] [Tipo v] [Severidad v]   |
|   Alertas            | [Origen v] [Aplicar filtros] [Limpiar]               |
|   Incidentes         |                                                         |
|   Inteligencia IoC   | +---------------------------------------------------+  |
|   Auditoría          | | FECHA/HORA | ORIGEN | TIPO | SEVERIDAD | ACCIÓN |  |
|   Configuración      | |-----------|--------|------|-----------|--------|  |
|                      | | ...       | ...    | ...  | Alta      | [Ver]  |  |
|                      | | ...       | ...    | ...  | Media     | [Ver]  |  |
|                      | | ...       | ...    | ...  | Baja      | [Ver]  |  |
|                      | +---------------------------------------------------+  |
|                      | [Anterior]                         [Siguiente]         |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Búsqueda por IP, usuario, origen o contenido.
- Filtros combinables por fecha, tipo, severidad y origen.
- Tabla paginada y ordenable.
- Acción **Ver** para consultar el evento completo y su metadato.
- La información sensible debe ocultarse o enmascararse según el rol.

### Pantalla 4 — Bandeja de alertas

**Propósito:** priorizar detecciones y facilitar su asignación y seguimiento.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                                      ALERTAS                   |
+----------------------+---------------------------------------------------------+
| MENÚ                 | BANDEJA DE ALERTAS                                     |
|   Dashboard          | [Buscar alerta................] [Severidad v] [Estado v]|
|   Eventos            | [Responsable v] [Filtrar]                               |
| > Alertas            |                                                         |
|   Incidentes         | +---------------------------------------------------+  |
|   Inteligencia IoC   | | ID | DETECCIÓN       | SEV.    | ESTADO | ASIGNADO |  |
|   Auditoría          | |----|-----------------|---------|--------|----------|  |
|   Configuración      | | 24 | Fallos de login | CRÍTICA | Abierta| Sin asig.|  |
|                      | | 23 | IP relacionada  | Alta    | En rev.| Analista |  |
|                      | | 22 | Tráfico anómalo | Media   | Abierta| Analista |  |
|                      | +---------------------------------------------------+  |
|                      | [Seleccionar alerta] [Asignar] [Cambiar estado]       |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Filtros por severidad, estado y responsable.
- Severidad visible mediante texto e icono; no depender solo del color.
- Acciones para asignar responsable y cambiar estado.
- Acceso al detalle para revisar evidencia y eventos relacionados.
- Confirmación para acciones sensibles y registro en auditoría.

### Pantalla 5 — Detalle e investigación de alerta

**Propósito:** presentar el contexto de una detección y permitir su investigación trazable.

```text
+--------------------------------------------------------------------------------+
| ALERTAS  >  DETALLE DE ALERTA #24                                              |
+--------------------------------------------------------------------------------+
| Fallos repetidos de autenticación                 [CRÍTICA] [ABIERTA]           |
| Detectada: [fecha/hora]       Fuente: [sensor/origen]                         |
|                                                                                |
| RESUMEN                                  ASIGNACIÓN                            |
| Cuenta/IP: [dato enmascarado]            Responsable: [Seleccionar v]          |
| Intentos: [cantidad]                     Estado: [Abierta v]                   |
| Ventana: [intervalo]                     [Guardar cambios]                     |
|                                                                                |
| EVENTOS RELACIONADOS                                                           |
| +--------------------------------------------------------------------------+   |
| | Hora | IP/origen | Usuario | Resultado | Referencia                      |   |
| +--------------------------------------------------------------------------+   |
|                                                                                |
| INDICADORES / CONTEXTO                                                         |
| [IoC relacionados] [Eventos relacionados] [Incidente vinculado]               |
|                                                                                |
| NOTAS DE INVESTIGACIÓN                                                         |
| [Escribir nota...........................................................]    |
| [Guardar nota]      [Vincular a incidente]      [Registrar acción]             |
|                                                                                |
| HISTORIAL DE CAMBIOS                                                           |
| [Fecha/hora] [Usuario] [Acción] [Resultado]                                   |
+--------------------------------------------------------------------------------+
```

**Elementos y comportamiento:**
- Resumen de la detección, severidad, estado y fuente.
- Eventos que originaron la alerta.
- Asignación de responsable y actualización del estado.
- Notas, vínculo con incidente y acciones registradas.
- Historial de cambios inmutable o protegido contra alteraciones no autorizadas.

### Pantalla 6 — Gestión de incidentes

**Propósito:** organizar la investigación y el ciclo de vida de un incidente.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                                      INCIDENTES                |
+----------------------+---------------------------------------------------------+
| MENÚ                 | GESTIÓN DE INCIDENTES              [+ Nuevo incidente] |
|   Dashboard          | [Buscar.................] [Estado v] [Prioridad v]     |
|   Eventos            |                                                         |
|   Alertas            | +---------------------------------------------------+  |
| > Incidentes         | | ID | TÍTULO          | PRIORIDAD | ESTADO | DUEÑO |  |
|   Inteligencia IoC   | |----|-----------------|-----------|--------|-------|  |
|   Auditoría          | | 08 | Acceso indebido | Alta      | Abierto| ...   |  |
|   Configuración      | | 07 | Equipo afectado | Media     | En rev.| ...   |  |
|                      | +---------------------------------------------------+  |
|                      |                                                         |
|                      | DETALLE DEL INCIDENTE SELECCIONADO                     |
|                      | Descripción: [......................................]  |
|                      | Alertas vinculadas: [Ver alertas]                      |
|                      | Evidencias: [Agregar referencia]                      |
|                      | Notas: [...........................................]  |
|                      | Estado: [Abierto v] [Guardar]                          |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Listado con prioridad, estado y responsable.
- Creación y edición de incidentes.
- Asociación de una o varias alertas.
- Registro de notas y referencias a evidencias.
- Transiciones de estado controladas y auditadas.

### Pantalla 7 — Inteligencia de amenazas (IoC)

**Propósito:** administrar indicadores de compromiso y consultar su relación con eventos y alertas.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                              INTELIGENCIA DE AMENAZAS (IoC)    |
+----------------------+---------------------------------------------------------+
| MENÚ                 | INDICADORES DE COMPROMISO             [+ Agregar IoC]   |
|   Dashboard          | [Buscar indicador...........] [Tipo v] [Confianza v]   |
|   Eventos            |                                                         |
|   Alertas            | +---------------------------------------------------+  |
|   Incidentes         | | TIPO | VALOR (ENMASCARADO) | CONFIANZA | ESTADO |   |
| > Inteligencia IoC   | | IP   | 192.0.2.x           | Alta      | Activo |   |
|   Auditoría          | | HASH | ab12...ef90        | Media     | Activo |   |
|   Configuración      | +---------------------------------------------------+  |
|                      |                                                         |
|                      | DETALLE DEL INDICADOR                                   |
|                      | Tipo: [IP / dominio / hash / URL]                      |
|                      | Valor: [........................................]     |
|                      | Fuente: [........................] Confianza: [v]     |
|                      | Descripción: [....................................]   |
|                      | [Guardar] [Consultar coincidencias] [Desactivar]       |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Alta, consulta, actualización y desactivación de IoC.
- Tipo, valor, fuente, confianza, fecha y estado.
- Búsqueda de coincidencias con eventos y alertas.
- Validación del formato y normalización del indicador.
- Restricción de acceso a valores potencialmente sensibles.

### Pantalla 8 — Auditoría y actividad

**Propósito:** permitir supervisión y trazabilidad de las operaciones realizadas en el sistema.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                                      AUDITORÍA                 |
+----------------------+---------------------------------------------------------+
| MENÚ                 | REGISTRO DE ACTIVIDAD                                  |
|   Dashboard          | [Usuario v] [Acción v] [Desde] [Hasta] [Filtrar]      |
|   Eventos            |                                                         |
|   Alertas            | +---------------------------------------------------+  |
|   Incidentes         | | FECHA/HORA | USUARIO | ACCIÓN | RECURSO | RESULTADO|  |
|   Inteligencia IoC   | |------------|---------|--------|---------|----------|  |
| > Auditoría          | | ...        | ...     | Login  | Sesión  | Correcto |  |
|   Configuración      | | ...        | ...     | Cambio | Alerta  | Correcto |  |
|                      | +---------------------------------------------------+  |
|                      |                                                         |
|                      | [Ver detalle del registro] [Exportar según permisos]   |
|                      |                                                         |
|                      | Nota: los registros de auditoría no se editan desde     |
|                      | esta pantalla. Las consultas y exportaciones también   |
|                      | deben quedar registradas cuando corresponda.           |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Filtros por usuario, acción, recurso y período.
- Detalle del evento de auditoría con actor, fecha, resultado y contexto.
- Exportación restringida por permisos.
- No ofrecer edición ni eliminación ordinaria de registros.
- Evitar almacenar contraseñas, tokens o secretos en los registros.

### Pantalla 9 — Configuración, usuarios y roles

**Propósito:** administrar parámetros y accesos de acuerdo con el rol del usuario.

```text
+--------------------------------------------------------------------------------+
| GUARDIÁN CARIBE                                      CONFIGURACIÓN             |
+----------------------+---------------------------------------------------------+
| MENÚ                 | CONFIGURACIÓN DEL SISTEMA                              |
|   Dashboard          | [General] [Usuarios] [Roles y permisos] [Seguridad]   |
|   Eventos            |                                                         |
|   Alertas            | USUARIOS                              [+ Nuevo usuario] |
|   Incidentes         | +---------------------------------------------------+  |
|   Inteligencia IoC   | | NOMBRE | CUENTA | ROL | ESTADO | ACCIÓN             |  |
|   Auditoría          | |--------|--------|-----|--------|--------------------|  |
| > Configuración      | | ...    | ...    | ... | Activo | [Editar]           |  |
|                      | +---------------------------------------------------+  |
|                      |                                                         |
|                      | ROLES Y PERMISOS                                       |
|                      | [Administrador] [Analista] [Operador] [Supervisor]    |
|                      | Permisos: [Consultar] [Crear] [Modificar] [Aprobar]    |
|                      |                                                         |
|                      | [Guardar cambios]                                      |
+----------------------+---------------------------------------------------------+
```

**Elementos y comportamiento:**
- Pestañas para configuración general, usuarios, roles y seguridad.
- Alta, edición, activación y desactivación de usuarios.
- Permisos agrupados por módulo y acción.
- Confirmación y auditoría de cambios sensibles.
- Principio de mínimo privilegio; la API debe validar cada permiso.

---

## 7. Criterios visuales y de usabilidad

- **Diseño:** interfaz de escritorio adaptable a tabletas y móviles.
- **Navegación:** menú lateral persistente y encabezado con búsqueda y sesión.
- **Jerarquía:** títulos claros, indicadores resumidos y tablas para datos operativos.
- **Accesibilidad:** contraste suficiente, navegación por teclado, etiquetas visibles y textos alternativos.
- **Estados:** distinguir severidad y estado mediante texto, iconos y color, nunca solo por color.
- **Mensajes:** informar éxito, validación y errores con lenguaje claro; no mostrar trazas ni detalles internos.
- **Rendimiento:** filtros, paginación y carga por demanda para redes de baja capacidad.
- **Seguridad:** sesiones protegidas, autorización del lado del servidor, registro de auditoría y protección de datos sensibles.

## 8. Componentes reutilizables

| Componente | Uso |
|---|---|
| Barra superior | Identidad, búsqueda, ayuda y sesión. |
| Menú lateral | Navegación entre módulos. |
| Tarjeta KPI | Indicadores resumidos del dashboard. |
| Tabla paginada | Eventos, alertas, incidentes, IoC y auditoría. |
| Filtros | Búsqueda por fecha, estado, tipo, severidad y responsable. |
| Etiqueta de estado | Estado y severidad con texto e icono. |
| Modal de confirmación | Acciones sensibles o cambios importantes. |
| Panel de detalle | Contexto, relaciones e historial de un registro. |

## 9. Flujo principal de uso

1. El usuario inicia sesión.
2. El sistema valida credenciales y permisos.
3. El usuario llega al panel SOC y revisa indicadores.
4. Consulta eventos y alertas priorizadas.
5. Abre una alerta, analiza eventos e IoC relacionados y registra notas.
6. Si corresponde, crea o vincula un incidente y asigna un responsable.
7. Las acciones quedan registradas para auditoría.
8. El supervisor consulta el estado y la trazabilidad.

## 10. Alcance y consideraciones de implementación

Este documento define una propuesta de experiencia de usuario; no implementa frontend, backend, autenticación ni persistencia. Los datos de los wireframes son ilustrativos. Antes de desarrollar, se deben validar los flujos con los requerimientos funcionales, los roles y los criterios de aceptación.

La interfaz no debe ejecutar acciones de respuesta real sin controles de autorización, aprobación y auditoría definidos por el proyecto. Los mockups tampoco implican que los módulos descritos ya existan.

## 11. Relación con el control de cambios

- **Issue:** [#12 — Diseñar wireframes y mockups de GUARDIÁN CARIBE](https://github.com/Ramon-MY/G-CARIBE-/issues/12).
- **Rama:** `mockups`, creada desde `main`.
- **Archivo:** `mockups/README.md`.
- **Commit:** se registra en la rama `mockups`.
- **Pull Request:** se propone integrar `mockups` en `main`; el PR referencia y cierra el Issue cuando sea integrado.

## 12. Conclusión

Los wireframes establecen una base común para diseñar y revisar la interfaz de GUARDIÁN CARIBE. La propuesta cubre autenticación, supervisión, investigación, gestión de incidentes, inteligencia de amenazas, auditoría y administración. El siguiente paso del proyecto será validar estos diseños y convertirlos en componentes funcionales, manteniendo trazabilidad entre requerimientos, Issues, commits y Pull Requests.
