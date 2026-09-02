## Application Overview

Content Management is a page-first review hub for product and session content, from draft through feedback, approval, and downstream handoff. It supports configurable masters, reviewer assignment, business-day SLAs, reminders, and audit history.

## Forms

| Form Name | Purpose | Key Lookups |
|---|---|---|
| Application Settings | Global SLA and automation settings | — |
| Products | Product catalog | Product Owner |
| Session Types | Session categories | — |
| Document Types | Content formats | — |
| Team Members | Resources, reviewers, capacity | User, Products |
| Holidays | SLA exclusions | — |
| Downstream Routes | Handoff destinations | — |
| SLA Policies | Scoped SLA rules | Product, Session Type, Document Type |
| Sessions | Product events and series | Product, Session Type, Owner |
| Content Documents | Submission and review lifecycle | Session, Product, Type, Users, SLA, Route |
| Review Feedback | Review-cycle comments | Document, Reviewer |
| Audit Log | Lifecycle history | Document |

## Reports

| Report Name | Type | Source Form |
|---|---|---|
| Configuration Settings | List | Application Settings |
| All Products | List | Products |
| All Session Types | List | Session Types |
| All Document Types | List | Document Types |
| All Team Members / Active Reviewers | List | Team Members |
| All Holidays / Holiday Calendar | List / Calendar | Holidays |
| All Downstream Routes | List | Downstream Routes |
| All SLA Policies | List | SLA Policies |
| All Sessions / Session Calendar | List / Calendar | Sessions |
| All Content Documents | List | Content Documents |
| Review Pipeline | Kanban | Content Documents |
| My Submissions / My Reviews | List | Content Documents |
| Overdue Reviews | List | Content Documents |
| Content Due Calendar | Calendar | Content Documents |
| All Feedback / Open Feedback | List | Review Feedback |
| Audit Trail | List | Audit Log |

## Pages

| Page Name | Purpose | Key Components |
|---|---|---|
| Content Hub Home | Shared dashboard | KPIs, lifecycle, pipeline, recent content |
| Submission Workspace | Resource workspace | Submissions, content, sessions, feedback |
| Review Workspace | Reviewer workspace | Queue, pipeline, overdue, calendar |
| Administration Center | Configuration workspace | Masters, policies, users, audit |

## Design Decisions

- Three profiles: administrator, resource, and reviewer; no role hierarchy.
- Seeds five products, five session types, and four document types; more can be added.
- Auto-assignment uses eligible reviewer workload and capacity.
- SLA ranking uses cycle, scope specificity, priority, effective date, and record ID.
- Deadlines use UTC weekdays and exclude active holidays.
- Blueprint covers draft, review, fixes, approval, and handoff.
- Pages lead navigation; web, tablet, and phone layouts are configured.