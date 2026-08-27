## Application Overview
A staff-only restaurant dining operations solution for a single venue. It coordinates reservations, waitlist flow, table occupancy, guest service, feedback recovery, auditability, and generic POS staging without replacing the restaurant POS.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Restaurant Settings | Venue defaults and operating parameters | — |
| Dining Areas | Floor zones and service areas | — |
| Dining Tables | Capacity and live table state | Dining Area |
| Guests | Guest profile, consent, and preferences | — |
| Service Periods | Service windows and cover limits | — |
| Reservations | Booking and arrival lifecycle | Guest, Service Period, Table |
| Waitlist Entries | Walk-in queue and seating | Guest, Area, Reservation, Table |
| Dining Visits | Active and completed dining service | Guest, Reservation, Waitlist, Table |
| Guest Feedback | Ratings and recovery tracking | Guest, Visit |
| POS Sync Log | Vendor-neutral integration staging | Local entity reference |
| Audit Log | Operational change history | Entity reference |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| Settings / area / table views | List, Kanban | Settings, Areas, Tables |
| Guest directories | List | Guests |
| Reservation operations | List, Calendar, Kanban | Reservations |
| Waitlist operations | List, Kanban | Waitlist Entries |
| Dining room operations | List | Dining Visits |
| Feedback and follow-up | List, Kanban | Guest Feedback |
| POS staging health | List, Kanban | POS Sync Log |
| Audit and exceptions | List | Audit Log |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Host Operations | Front-desk command center | KPIs, arrivals, waitlist, alerts, quick actions |
| Live Floor Board | Area-filtered floor status | Occupancy cards, table state, next booking, POS context |
| FOH Manager Dashboard | Management oversight | KPIs, demand, exceptions, feedback, POS health |

## Design Decisions
- Profiles: Administrator, FOH Manager, Host, and Server; no role hierarchy.
- Generic POS staging boundary only; no vendor API or payment logic.
- Workflow-driven lifecycle controls synchronize reservations, waitlist, visits, tables, guest history, and audit events.
- Responsive web pages plus focused phone/tablet menus and report layouts.
- Legacy `Add_New_Lead` schema metadata is quarantined in device `unused` blocks and is not exposed operationally.
