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


