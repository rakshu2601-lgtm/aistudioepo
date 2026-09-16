## Application Overview
MT Fleet Hub is a Phase 1 fleet-service coordination app covering authenticated intake, matching, sliced estimates, MTter responses, reassignment, and readiness for quotation. It provides controlled master data, operational automation, portal-specific access, audit history, and an internal exception dashboard.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Currency | Selectable currencies | — |
| FMC Client | Client and portal identity master | Currency |
| Capability | Controlled service capabilities | — |
| MTter | Provider, coverage, and portal master | Capability |
| Part | Approved parts catalog | Capability, Currency |
| Service Request | Draft/submitted service intake | FMC Client, Capability |
| Estimate | MTter assignment slices and responses | Service Request, MTter, Capability, Currency |
| Estimate Line | Parts and labor detail | Estimate, Part, Currency |
| Task | Reassignment and follow-up work | Service Request, Estimate |
| Activity | Append-only operational audit | Service Request, Estimate |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All Currencies | List | Currency |
| All / Active FMC Clients | List | FMC Client |
| All Capabilities | List | Capability |
| All MTters / Insurance Expiring | List | MTter |
| MTter Locations | Map | MTter |
| All / Active Parts | List | Part |
| All Service Requests / My Requests / Matching Queue | List | Service Request |
| Service Pipeline | Kanban | Service Request |
| All / Assigned / Pending / Declined Estimates | List | Estimate |
| Estimate Lines | List | Estimate Line |
| All Tasks / Open Reassignments | List | Task |
| Task Board | Kanban | Task |
| Activity Log / Recent Activity | List | Activity |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Fleet Dashboard | Internal operations command center | KPI cards, pipeline, exceptions, activity, shortcuts |

## Design Decisions
- Currency is master-driven; totals are not FX-normalized.
- Save Draft / Submit Request is an explicit intake choice.
- External geocoding is a documented connector placeholder with failure status.
- Portal ownership is enforced through permissions, report criteria, and validation.
- Estimate decline creates reassignment work; full approved coverage advances the request.
