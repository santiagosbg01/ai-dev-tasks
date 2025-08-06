## Relevant Files

- `models/Client.ts` - Defines the client schema, including billing, contracts, support data, and metadata.
- `models/User.ts` - Defines user roles and permissions for KAMs, Managers, Admins.
- `components/ClientDashboard.tsx` - Renders the unified 360° client view UI.
- `components/ActivityTimeline.tsx` - Displays chronological client interaction history.
- `components/AlertEngine.ts` - Logic for generating task reminders, renewals, and system alerts.
- `pages/api/integrations/zoho.ts` - Handles API integration with Zoho Desk.
- `pages/api/integrations/netsuite.ts` - Handles API integration with NetSuite billing system.
- `pages/api/integrations/google.ts` - Syncs calendar and email from Google Workspace.
- `components/AdminPanel.tsx` - UI for managing templates, workflows, roles, and regional settings.
- `components/ReportingDashboard.tsx` - KPIs, charts, and metrics for managers.
- `lib/alerts/generator.ts` - Logic to trigger alerts based on custom rules.
- `lib/workflows/templates.ts` - Standard workflows and templates for KAMs.
- `lib/utils/auth.ts` - Role-based access logic.
- `tests/Client.test.ts` - Unit tests for client model logic.
- `tests/ClientDashboard.test.tsx` - Tests for client UI and data visibility.
- `tests/AlertEngine.test.ts` - Unit tests for alert engine logic.
- `tests/ReportingDashboard.test.tsx` - Tests for reporting and KPI accuracy.

### Notes

- Unit tests should typically be placed alongside the code files they are testing (e.g., `ClientDashboard.tsx` and `ClientDashboard.test.tsx` in the same directory).
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.

## Tasks

- [ ] 1.0 Define CRM Data Models and Schema
  - [ ] 1.1 Define `Client` model including contract data, billing info, linked tickets, and metadata
  - [ ] 1.2 Define `User` model with role-based attributes (KAM, Manager, Admin)
  - [ ] 1.3 Define activity log schema with timestamp, user, and event type
  - [ ] 1.4 Set validation rules and required fields for client records

- [ ] 2.0 Build 360° Client View UI and Client Dashboard
  - [ ] 2.1 Create `ClientDashboard.tsx` to render contracts, billing, ticket status, and recent actions
  - [ ] 2.2 Add `ActivityTimeline.tsx` component with filters and chronological sorting
  - [ ] 2.3 Implement tabs or sections for documents, support history, and metrics
  - [ ] 2.4 Integrate UI with data model using SWR or GraphQL for real-time updates
  - [ ] 2.5 Add error states and loading states for dashboard components

- [ ] 3.0 Implement Integration Layer (Zoho Desk, NetSuite, Google Workspace, etc.)
  - [ ] 3.1 Set up API authentication and token management for all external services
  - [ ] 3.2 Create `/api/integrations/zoho.ts` to pull support ticket data
  - [ ] 3.3 Create `/api/integrations/netsuite.ts` to sync billing and contract data
  - [ ] 3.4 Create `/api/integrations/google.ts` to read Gmail threads and calendar events
  - [ ] 3.5 Implement sync scheduling (webhooks or polling every X minutes)
  - [ ] 3.6 Add logging for integration failures and success audits

- [ ] 4.0 Develop Activity Tracking and Alerts Engine
  - [ ] 4.1 Build `lib/alerts/generator.ts` to define and trigger event-driven alerts (contract renewal, ticket spike, no activity)
  - [ ] 4.2 Add UI notification system (toasts or inbox)
  - [ ] 4.3 Implement backend scheduler (e.g., cron job or task queue) for recurring checks
  - [ ] 4.4 Define rules for moving clients across status stages (e.g. “inactive”, “flagged”)
  - [ ] 4.5 Implement snooze, dismiss, or acknowledge actions for alerts

- [ ] 5.0 Build Admin Panel with Roles, Permissions, and Template Management
  - [ ] 5.1 Create `AdminPanel.tsx` to configure templates and field requirements per region
  - [ ] 5.2 Add interface to manage role-based access and permissions
  - [ ] 5.3 Connect template manager to `lib/workflows/templates.ts`
  - [ ] 5.4 Implement toggles for mandatory fields by stage, region, or client type
  - [ ] 5.5 Validate user permissions using `lib/utils/auth.ts`

- [ ] 6.0 Create Reporting Module with Dashboards and KPIs
  - [ ] 6.1 Design `ReportingDashboard.tsx` to show PLV, CSAT, churn risk, support load, and contract cycle
  - [ ] 6.2 Enable filtering by region, KAM, date range, and client tier
  - [ ] 6.3 Add drilldown links from KPIs into client-specific dashboards
  - [ ] 6.4 Generate scheduled exports or email reports (weekly/monthly)
  - [ ] 6.5 Add trend indicators (green/red arrows, deltas vs. previous period)
     
- [ ] 7.0 Implement KAM Account Assignment and Role-Based Client Access
  - [ ] 7.1 Extend `User` model to support assigned client relationships
  - [ ] 7.2 Add client assignment UI in Admin Panel (assign/unassign clients to KAMs)
  - [ ] 7.3 Update `ClientDashboard.tsx` to show account ownership and restrict editing
  - [ ] 7.4 Create view showing number of accounts each KAM manages
  - [ ] 7.5 Add role-based permission logic: editable if KAM is owner, read-only otherwise
  - [ ] 7.6 Add test coverage for permission enforcement (editing and viewing scenarios)

- [ ] 8.0 Implement Client Service & Subservice Assignment
  - [ ] 8.1 Extend `Client` model to store selected services and subservices
  - [ ] 8.2 Define the initial service taxonomy (Envios99, Tailor99, Freight99, Fulfill99 and all subservices)
  - [ ] 8.3 Add UI component in `ClientDashboard.tsx` to assign/unassign services and subservices
  - [ ] 8.4 Ensure selected services are displayed clearly on the client view
  - [ ] 8.5 Add filtering capability in the reporting or client list view by service/subservice
  - [ ] 8.6 Add validation rules to prevent conflicting or unsupported combinations
  - [ ] 8.7 Write unit tests to ensure service assignment logic and permissions work as expected

- [ ] 9.0 Integrate Google Calendar for Events and Tasks
  - [ ] 9.1 Set up Google OAuth for calendar access
  - [ ] 9.2 Create `/api/integrations/google/calendar.ts` to fetch events, write tasks
  - [ ] 9.3 Add calendar sync status and account info to user settings
  - [ ] 9.4 Handle token expiration, refresh tokens, and error logging
  - [ ] 9.5 Display upcoming meetings or deadlines from calendar in user dashboard
  - [ ] 9.6 Add unit and integration tests for Google Calendar integration logic

- [ ] 10.0 Build In-App Calendar View with Task Integration
  - [ ] 10.1 Create `CalendarView.tsx` to render calendar UI with daily/weekly/monthly view
  - [ ] 10.2 Link KAM-created tasks to calendar slots (e.g. follow-ups, contract renewal)
  - [ ] 10.3 Allow new tasks to be added directly from the calendar interface
  - [ ] 10.4 Visual indicators: differentiate between synced calendar events and CRM tasks
  - [ ] 10.5 Filter calendar by client, task type, or service
  - [ ] 10.6 Add role-based view: KAMs see their calendar, Managers can view team calendars
  - [ ] 10.7 Add unit tests for rendering, filtering, and sync integrity

Additions to Relevant Files Section
- `pages/api/integrations/google/calendar.ts` - Handles syncing events and tasks from Google Calendar.
- `components/CalendarView.tsx` - UI component for visual calendar interface.
- `models/Task.ts` - Extend if needed to include calendar binding.
- `lib/utils/calendar.ts` - Utilities for formatting events, mapping tasks to calendar slots.
- `tests/calendar.test.tsx` - Tests for UI, sync state, and filtering behavior.
- `tests/integrations/google-calendar.test.ts` - Tests for Google Calendar API interaction.

WIP - [ ] 11.0 Implementar Módulo de Reportes por Cliente
  - [ ] 11.1 Modificar estructura general de `ClientReporting.tsx` con tabs por tipo de reporte
  - [ ] 11.2 Agregar seccion de Reporte de Performance Operativo
    - [ ] 11.2.1 Crear endpoint para consultar performance por rango de fechas
    - [ ] 11.2.2 Mostrar: Número de guías creadas, días con recolección, % de delivery success, % de on-time delivery, % de attempted on-time delivery
    - [ ] 11.2.3 Agregar filtros por fecha y tipo de servicio
    - [ ] 11.2.4 Agregar upload feature para subir y resguardar un reporte para ese cliente como archivo descargable y compartible en email.
  - [ ] 11.3 Agregar Reporte de Facturación
    - [ ] 11.3.1 Integrar con NetSuite para obtener datos de facturación
    - [ ] 11.3.2 Mostrar totales por mes, desglose por servicio, y facturas emitidas
    - [ ] 11.3.3 Habilitar exportación en Excel o CSV
  - [ ] 11.4 Agregar seccion de Reporte de NPS
    - [ ] 11.4.1 Mostrar última medición de NPS con fecha y valor
    - [ ] 11.4.2 Listar comentarios cualitativos por cliente
    - [ ] 11.4.3 Mostrar gráfica histórica si hay más de una medición
  - [ ] 11.5 Agregar seccion de Reporte de Atención SAC
    - [ ] 11.5.1 Integrable con Zoho Desk para traer número de tickets, tiempos de respuesta y resolución en un rango de fechas determinado
    - [ ] 11.5.2 Calcular % de tickets resueltos favorable vs. no favorable
    - [ ] 11.5.3 Agregar breakdown por canal (WhatsApp, Email, etc.)

Archivos Relevantes a Agregar en tu Sección de Relevant Files
- `components/ClientReporting.tsx` - Componente principal con tabs para cada tipo de reporte
- `components/Reporting/OperationalReport.tsx` - Vista del reporte operativo
- `components/Reporting/BillingReport.tsx` - Vista del reporte de facturación
- `components/Reporting/NPSReport.tsx` - Vista del reporte de NPS
- `components/Reporting/SupportReport.tsx` - Vista del reporte de atención SAC
- `pages/api/reporting/operational.ts` - Endpoint para datos operativos
- `pages/api/reporting/billing.ts` - Endpoint para facturación desde NetSuite
- `pages/api/reporting/nps.ts` - Endpoint para métricas y comentarios de NPS
- `pages/api/reporting/support.ts` - Endpoint para KPIs de atención al cliente desde Zoho Desk
- `tests/ClientReporting.test.tsx` - Pruebas de integración de todos los reportes
- `tests/Reporting/OperationalReport.test.tsx` - Pruebas para métricas operativas
- `tests/Reporting/BillingReport.test.tsx` - Pruebas para visualización de facturación
- `tests/Reporting/NPSReport.test.tsx` - Pruebas para datos de NPS
- `tests/Reporting/SupportReport.test.tsx` - Pruebas para métricas SAC

TBD - [ ] 12.0 Implementar Funcionalidad de Envío de Correos desde la Plataforma
  - [ ] 12.1 Crear componente `EmailComposer.tsx` para redacción de correos
    - [ ] 12.1.1 Campo para asunto, destinatario (prellenado si es cliente asignado), y cuerpo
    - [ ] 12.1.2 Adjuntar archivos desde reportes generados
    - [ ] 12.1.3 Previsualización del correo antes de enviar
  - [ ] 12.2 Agregar opción para compartir un reporte desde el módulo de reporting
    - [ ] 12.2.1 Botón “Compartir por correo” en cada sección del reporte
    - [ ] 12.2.2 Insertar resumen del reporte o archivo adjunto generado (PDF/CSV)
  - [ ] 12.3 Crear flujo de notificación de actualización, reminder de cobro o pago
    - [ ] 12.3.1 Plantillas predefinidas para: recordatorio de pago, actualización operativa, seguimiento
    - [ ] 12.3.2 Permitir edición del contenido antes de enviar
    - [ ] 12.3.3 Registro del correo en el historial de actividad del cliente
  - [ ] 12.4 Restringir permisos: solo agentes o managers CAMP pueden enviar
  - [ ] 12.5 Crear logs de envío con estado (enviado, error, abierto)
  - [ ] 12.6 Agregar pruebas unitarias e integración para los flujos de correo

Archivos Relevantes para Agregar
- `components/EmailComposer.tsx` - Componente principal de redacción y envío de correos
- `components/Reporting/[ReportComponent].tsx` - Integración de botón de “Compartir por correo”
- `lib/email/templates.ts` - Plantillas predefinidas de recordatorios y notificaciones
- `lib/email/sendEmail.ts` - Lógica para enviar correo usando Gmail API o SMTP
- `models/EmailLog.ts` - Modelo para almacenar logs de correos enviados
- `pages/api/email/send.ts` - Endpoint para enviar correo y registrar resultados
- `tests/EmailComposer.test.tsx` - Pruebas del UI de redacción de correos
- `tests/email/sendEmail.test.ts` - Pruebas de la lógica de envío y manejo de errores

TBD - [ ] 13.0 Activar Superpoder de Investigación Comercial por Cliente
  - [ ] 13.1 Agregar botón "Investigar" en la vista de cliente (`ClientDashboard.tsx`)
    - [ ] 13.1.1 Ejecuta escenario en Make.com vía webhook (pasando nombre, sitio, dominio, industria, etc.)
    - [ ] 13.1.2 Mostrar estado de ejecución (cargando, completado, error)
    - [ ] 13.1.3 Mostrar resultados procesados en nueva sección “Oportunidades Detectadas”
  - [ ] 13.2 Crear componente `ClientOpportunities.tsx`
    - [ ] 13.2.1 Mostrar insights regresados desde Make.com: volumen, actividad, servicios sugeridos, comparables
    - [ ] 13.2.2 Permitir que el KAM registre una oportunidad basada en estos insights
  - [ ] 13.3 Agregar lógica de ejecución automática
    - [ ] 13.3.1 Ejecutar escenario automáticamente al crear una nueva cuenta
    - [ ] 13.3.2 Agendar ejecución mensual por cliente (cron job o scheduled task)
    - [ ] 13.3.3 Guardar resultados previos y fecha del último análisis
  - [ ] 13.4 Añadir permiso para que solo roles de KAM y Manager puedan disparar botón
  - [ ] 13.5 Crear logs para cada ejecución (fecha, triggered by user/system, status)
  - [ ] 13.6 Pruebas de flujo completo (botón, backend, webhook, resultados, errores)

Archivos Relevantes para Agregar
- `components/ClientDashboard.tsx` - Agrega botón “Investigar” y conecta con la sección de oportunidades
- `components/ClientOpportunities.tsx` - Vista para mostrar resultados de la investigación
- `pages/api/research/trigger.ts` - Endpoint que llama al webhook de Make.com
- `lib/cron/monthlyResearch.ts` - Tarea mensual automática por cliente
- `models/ResearchLog.ts` - Modelo para registrar ejecuciones, status y resultados
- `tests/ClientDashboard.test.tsx` - Pruebas de botón e integración
- `tests/ClientOpportunities.test.tsx` - Pruebas del renderizado de insights
- `tests/research/trigger.test.ts` - Pruebas del endpoint y lógica Make.com

TBD - [ ] 14.0 Implementar Módulo de Handoff de Cuenta entre Hunters y Farmers
  - [ ] 14.1 Crear `HandoffWizard.tsx` con flujo paso a paso de entrega de cuenta
    - [ ] 14.1.1 Paso 1: Seleccionar nuevo responsable (Farmer o KAM)
    - [ ] 14.1.2 Paso 2: Ingresar sección de notas internas y últimos touch points
    - [ ] 14.1.3 Paso 3: Ingresar lista de tareas pendientes con fechas
    - [ ] 14.1.4 Paso 4: Adjuntar documentos relevantes (videos, contratos, presentaciones)
    - [ ] 14.1.5 Paso 5: Proyectos a futuro y oportunidades de cross-sell / up-sell
  - [ ] 14.2 Enviar correo automático al cliente al finalizar el proceso
    - [ ] 14.2.1 Usar plantilla predefinida de “Presentación de nuevo responsable”
    - [ ] 14.2.2 Insertar nombre, correo y datos de contacto del nuevo dueño
    - [ ] 14.2.3 Incluir sección editable para un mensaje personalizado
  - [ ] 14.3 Cambiar asignación oficial de cuenta en el sistema
    - [ ] 14.3.1 Solo después de que el handoff esté completo y validado por ambas partes
  - [ ] 14.4 Habilitar tracking de handoffs completados y pendientes
    - [ ] 14.4.1 Vista de estado: En Proceso / Completado / Rechazado
    - [ ] 14.4.2 Registro histórico de todos los handoffs por cuenta
  - [ ] 14.5 Agregar validaciones:
    - [ ] 14.5.1 Todos los campos requeridos deben completarse antes de permitir el envío
    - [ ] 14.5.2 El nuevo responsable debe confirmar recepción del handoff
  - [ ] 14.6 Agregar pruebas para lógica, flujos y permisos

- `components/HandoffWizard.tsx` - UI paso a paso del proceso de handoff
- `components/ClientDashboard.tsx` - Agregar botón "Iniciar Handoff" si el usuario es dueño
- `pages/api/handoff/submit.ts` - API para crear y guardar handoff con validación
- `pages/api/handoff/confirm.ts` - API para confirmar y cerrar handoff por parte del nuevo responsable
- `models/Handoff.ts` - Modelo para almacenar estructura completa del handoff
- `lib/email/templates.ts` - Plantilla de presentación de nuevo responsable
- `lib/email/sendHandoffEmail.ts` - Lógica para envío de correo con resumen y presentación
- `tests/HandoffWizard.test.tsx` - Pruebas de UI del proceso
- `tests/handoff/submit.test.ts` - Pruebas de creación y validación del handoff
- `tests/handoff/confirm.test.ts` - Pruebas de confirmación y cambio de dueño

- ## 🧑‍💻 Módulo de Control de Usuarios: Último Login + Alertas

### 1. [ ] Captura del Login de Usuario
- [ ] Activar registro de timestamp al momento de login en el CRM.
- [ ] Guardar login más reciente por ID de usuario.
- [ ] Proteger contra sesiones fantasmas o inactividad (verificar con token activo).

### 2. [ ] Dashboard de Actividad por Usuario
- [ ] Crear vista para managers y admins con tabla de:
  - Nombre del KAM
  - País / Región
  - Último login (fecha/hora)
  - Estado de alerta (🟢 Activo / 🟡 4-7 días / 🔴 >7 días)
- [ ] Filtros por equipo, país o manager responsable.
- [ ] Orden por fecha de login (más antiguo arriba).

### 3. [ ] Alertas de Inactividad Automáticas
- [ ] Crear lógica que corra diariamente y detecte KAMs con >7 días sin login.
- [ ] Enviar alerta al manager responsable por WhatsApp o correo:
  - Mensaje sugerido: “🔴 Tu KAM Juan Pérez no ha entrado al CRM desde hace 8 días.”
- [ ] Agregar botón para que el manager dé seguimiento o marque como justificado.

### 4. [ ] Integración con Dashboard de Gamificación / Rendimiento
- [ ] Mostrar “Días desde último login” como métrica visible en el perfil del KAM.
- [ ] Penalizar en el leaderboard si >7 días sin actividad (opcional).
- [ ] Incluir dato en resumen semanal de managers.

### 5. [ ] Notas Técnicas
- [ ] Timestamp se actualiza solo con login activo, no sesiones automáticas.
- [ ] Guardar histórico (opcional)

