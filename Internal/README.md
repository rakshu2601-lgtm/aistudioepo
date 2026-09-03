## Application Overview
Internal Training Team Operations manages people, leave/WFH approvals, products, events, task execution, daily updates, discounts, invoices, and training analytics. Trainer, Lead, and Manager profiles provide progressively broader access, while URL-based resources avoid file uploads.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Team Members | Team directory and reporting | Reporting To → Team Members |
| Products | Product master | — |
| Leave Requests | Leave approval | Requester → Team Members |
| Work From Home Requests | WFH approval | Requester → Team Members |
| Events | Training/event lifecycle | Product, Trainers → masters |
| Pre Event Activities | Content, reviews, agenda, early stats | Event, team members |
| During Event Updates | Daily multi-day updates | Event, Trainer |
| Post Event Statistics | Outcomes and revenue | Event, Product |
| Source Wise Statistics | Webinar source breakdown | Post Event Statistics |
| Country Wise Statistics | Webinar country breakdown | Post Event Statistics |
| Task Assignments | Work allocation and deadlines | Event, Assigned Trainer |
| Daily Work Items | Daily update detail rows | Daily Update, Event, Task |
| Daily Work Updates | Consolidated daily reporting | Team Member, Work Items |
| Exchange Rates | Maintained USD conversion rates | — |
| Discount Requests | Discount approval and fulfilment | Product, Event, team members |
| Manual Invoice | Converted invoice requests | Product, Event, Exchange Rate |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All/Available Team Members | List | Team Members |
| All/Active Products | List | Products |
| Leave and WFH request views | List, Calendar | Request forms |
| Event views | List, Calendar, Kanban | Events |
| Pre/During Event views | List, Calendar, Kanban | Event activity forms |
| Post-event analytics | List summaries | Statistics forms |
| Task views | List, Kanban | Task Assignments |
| Daily update views | List, Calendar | Daily Work forms |
| Exchange-rate views | List | Exchange Rates |
| Discount views | List with action | Discount Requests |
| Invoice views | List with action | Manual Invoice |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Operations Dashboard | Operational and management overview | KPIs, charts, event cards, delayed tasks, approvals, quick links |

## Design Decisions
- Three profiles; no role hierarchy.
- WFH requests allow today/future dates only.
- Non-sick leave requires seven days' notice.
- Currency conversion uses the latest active internal USD-based rate.
- Discount approver is selected from Team Members per request.
- The supplied legacy DS informed only discount and invoice patterns.
- All documents and resources use URL fields.
