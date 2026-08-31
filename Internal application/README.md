## Application Overview

This internal Training Operations Platform manages training events, people, leave/WFH, tasks, discounts, invoices, metrics, and audit history. Role-aware dashboards support operations, approvals, finance, and management. Invoices are ready for USD conversion; live rate integration is deferred.

## Forms

| Form Name | Purpose | Key Lookups |
|---|---|---|
| Team Members | Staff directory | Reporting Manager → Team Members |
| Leave & WFH Requests | Requests and approvals | Member, Manager → Team Members |
| Products | Product catalog | Owner → Team Members |
| Events | Unified event lifecycle | Product; trainers → Team Members |
| Event Performance | Webinar metrics | Event → Events |
| Tasks | Trainer/mentor work | Assignee, Assignor → Team Members |
| Discounts | Lead-approved discounts | Event; Product |
| Invoices | Billing and USD readiness | Event; Discount; Trainer |
| Audit Log | Critical-change history | Changed By → Team Members |

## Reports

| Report Name | Type | Source Form |
|---|---|---|
| Team/Product directories | List | Team Members, Products |
| Event summary/upcoming/incomplete/tickets | List | Events |
| Event Calendar | Calendar | Events |
| Event Lifecycle Board | Kanban | Events |
| Performance details/source/country | List | Event Performance |
| Leave requests/pending/mine | List | Leave Requests |
| Approved Leave & WFH | Calendar | Leave Requests |
| Task lists/attention/trainer/mentor | List | Tasks |
| Task Board | Kanban | Tasks |
| Discounts/pending/approved | List | Discounts |
| Invoices/outstanding/overdue/paid | List | Invoices |
| Audit History | List | Audit Log |

## Pages

| Page Name | Purpose | Key Components |
|---|---|---|
| Operations Dashboard | Event execution | KPIs, readiness, lifecycle |
| Metrics Dashboard | Performance | Attendance, revenue, charts |
| Trainer Dashboard | Personal workload | Assignments, overdue work |
| Leave Task Dashboard | Coordination | Approvals, schedule, task status |
| Finance Dashboard | Receivables | USD exposure, overdue invoices |
| Manager Dashboard | Oversight | Cross-module KPIs and alerts |

## Design Decisions

- One Events form supports all five event types with type-driven fields.
- Profile-based access is used without a role hierarchy.
- Leave is request-only; discount approval belongs to Lead.
- Webinar source/country metrics use structured child records.
- Blueprints manage event, task, leave, and discount lifecycles.
- Responsive snippets and device-specific navigation are used.
- Live currency-rate retrieval is deferred; invoice fields are conversion-ready.