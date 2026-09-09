## Application Overview
The NPD application governs BPD and CPD product-development requests from plant selection through document review, configurable N-stage gates, final QA approval, and Mass Production. It preserves every rejection and resubmission attempt, applies fixed team assignments and SLA escalation, and provides role-aware operational analytics.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Process Settings | Fixed owners, SLA, escalation and release recipients | — |
| Plants | BPD/CPD plant master | — |
| Product Lines | Product lines by plant | Plants |
| Gate Routes | Versioned plant/product routing | Plants, Product Lines |
| Gate Route Steps | Ordered N1/N5/N10/N30/N50 gates | Gate Routes |
| Document Requirements | Initial and gate document checklist | Gate Routes, Gate Route Steps |
| NPD Requests | Main request and end-to-end lifecycle | Plants, Product Lines, Gate Routes |
| Request Documents | Versioned initial documents | NPD Requests, Document Requirements |
| Sample Validation Items | Structured validation checklist | NPD Requests |
| Stage Gate Instances | Per-request gate progression | NPD Requests, Gate Route Steps |
| Stage Gate Submissions | Immutable review attempts and decisions | Stage Gate Instances |
| Submission Documents | Sourcing evidence and QA reports | Stage Gate Submissions, Document Requirements |
| Process Audit Log | Immutable process history | Requests, gates, submissions |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| Process Settings Admin; All Plants; All Product Lines | List | Master forms |
| Gate Routes Admin; Gate Route Steps Admin; Document Requirements Admin | List | Routing forms |
| All/My NPD Requests; Approval Queue; Mass Production Queue | List | NPD Requests |
| NPD Pipeline | Kanban | NPD Requests |
| Request Documents; Sample Validation Sheet | List | Document/validation forms |
| Stage Gate Tracker | List | Stage Gate Instances |
| Stage Gate Board | Kanban | Stage Gate Instances |
| Stage Gate Submissions; My Review Queue | List | Stage Gate Submissions |
| Submission SLA Calendar | Calendar | Stage Gate Submissions |
| Submission Documents | List | Submission Documents |
| Process Audit Trail | List | Process Audit Log |
| Process Timeline | Timeline | Process Audit Log |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| NPD Dashboard | Pipeline, workload, SLA and route health | KPI cards, funnels, gate progress, queue, audit feed, quick links |

## Design Decisions
- Gate sequences and document requirements are configuration-driven.
- Fixed users are maintained centrally; transitions remain profile-restricted.
- Every rejection creates a new immutable attempt instead of overwriting history.
- Initial documents are versioned and Sample Validation is structured.
- Seven-working-day reminders/escalations support QA and approval gates.
- Final approval triggers Mass Production release notifications.