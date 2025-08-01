Here’s your **PRD in Markdown**, crafted following the structure of `create-prd.md` from your GitHub repo—clear, strategic, and ready for action.

---

# 🚀 Custom CRM for Client Management (Without Sales Pipeline)

## 1. 🧾 Elevator Pitch

We’re building a **bespoke CRM** focused on managing existing client accounts and empowering your KAM team. It consolidates all client data—contracts, billing, support tickets—and provides tools to monitor activity, automate alerts, and integrate seamlessly with your ecosystem. No sales pipeline, just robust account management.

---

## 2. 🎯 Target Users & Stakeholders

* **Primary Users**:

  * KAMs / **Farmers** tracking client work and relationships
  * Managers and Executives monitoring individual and team performance
* **Stakeholders**:

  * Product/Tech leads (implementation & data flow)
  * Finance team (billing / NetSuite integration)
  * Customer support (Zoho Desk integration)
  * Regional operations teams (template consistency)

---

## 3. 🧩 Functional Requirements

### A. Core Capabilities

* Unified **360° client view**: contracts, billing, tickets, tasks, past interactions
* Full **traceability** of client-related activity (who did what, when)
* **Account-based metrics**: PLV, last touch, usage, support history

### B. Activity Monitoring & Reporting

* Activity tracking per **Farmer** (KAM) and per team
* Views by individual and aggregate performance
* Dashboards and reports for Hunting vs. Farming needs—even though no pipeline stages

### C. Templates & Workflow Automation

* **Standardized templates and workflows** across regions
* Workflow automation: recurring tasks, handoffs, alerts
* Prebuilt templates for common processes (e.g. billing review, support check‑in)

### D. Automated Alerts & Reminders

* Notifications for:

  * Upcoming tasks
  * Contract renewal dates
  * Support inactivity or high ticket volume
* Enforced **transition criteria** within certain account workflows (e.g., after last invoice, mark “inactive”), even without a formal funnel

### E. Integration Requirements (Must-Haves)

* API / two-way sync with:

  * **Typeform** for lead capture (if needed for pre‑existing clients or forms)
  * **WeTrust (WeeTrust?)** for electronic signatures
  * **Google Workspace**: Gmail & Calendar integration
  * **Zoho Desk**: support ticket syncing and case tracking
  * **NetSuite**: financial data (billing, revenue, invoices)
  * **Duemint** (Chile collections tool; validate for other countries)
* **Open API layer** for custom integrations (e.g. Looker dashboards, internal systems)

### F. Data Quality & Governance

* Customizable data schemas per account type or region
* Mandatory fields enforcement at record creation/update
* Role-based access control: Executive, Manager, Admin
* Audit logs for changes

### G. Reporting & KPIs

* Prebuilt KPIs: revenue per account, churn risk, CSAT/NPS, support load
* Scheduled reports (daily/weekly/monthly), dashboards
* Custom KPI definitions per regional strategy

### H. Bonus / Future Features (Optional)

* **AI-assisted summaries** of ticket history or client interactions
* Smart upsell or renewal recommendations
* KAM health score over time
* SLA compliance metrics for support ticket handling
* WhatsApp or SMS integrations for outreach logs

---

## 4. 📋 User Stories (Examples)

| As a…        | I want to…                                         | So I can…                                   |
| ------------ | -------------------------------------------------- | ------------------------------------------- |
| KAM / Farmer | See full client history in one view                | Understand context before outreach          |
| Manager      | Track team activity and metrics at glance          | Evaluate performance and allocate workload  |
| Admin        | Define mandatory fields and templates per region   | Ensure data consistency across all accounts |
| Support Team | See tickets from Zoho Desk in CRM                  | Link client support activity to account     |
| Finance Team | Access billing/invoice information via integration | Reconcile revenue and client relationship   |

---

## 5. 📐 Success Metrics

* **Adoption & Usage**: 90% of KAMs logging activity daily
* **Data Completeness**: Mandatory fields 100% filled for new records
* **Alert Accuracy**: < 5% false/duplicate alerts per month
* **Integration Sync Health**: < 1% failed sync rate from Zoho Desk / NetSuite
* **Client Visibility**: All accounts have unified history accessible within 3 clicks
* **Support Impact**: Reduction in response time due to ticket integration (\~20% faster)

---

## 6. ⚠️ Dependencies & Constraints

* Zoho Desk API license access
* NetSuite integration endpoints availability
* Region-specific local tools (Duemint) require validation
* API access from Typeform, WeTrust, Google Workspace
* Compliance with data protection requirements by region

---

## 7. 📅 Timeline (High-Level)

1. Core CRM architecture & data model
2. Integrations with Zoho Desk, NetSuite, Google Workspace
3. Templates & workflow engine
4. Activity tracking + reporting dashboards
5. Role-based permissions, alerts, data validation
6. Pilot rollout with one country (Chile), then regional expansion
7. Bonus features deployment (AI assistant, smart recommendations)

---

## 8. 🎥 Additional Notes

* Don’t confuse this with a sales pipeline tool—it’s focused exclusively on **existing client account management**
* Make sure integrations are bidirectional where needed
* Emphasize **auditability and data accuracy** over bulk record creation
* Expect to evolve workflows based on feedback from your KAM team

---

Let me know if you want this exported as a `.md` file attached or synced to your GitHub repo directly. Ready to generate a task list or start implementation.
