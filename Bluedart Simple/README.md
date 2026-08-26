## Application Overview
Bluedart Simple is an India-localized logistics and loyalty application covering customer onboarding, KYC, quotations, pickups, multi-leg hub journeys, delivery, tracking, rates, rewards, and audit history. It uses INR with Indian grouping, kg/km/cm, Indian contact and address conventions, day-first dates, and Asia/Kolkata time.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Hubs | Hub master and service locations | — |
| Employees | Internal users, managers, and agents | Hubs |
| KYC_Document_Rules | Configurable KYC requirements | — |
| Customers | Retail, Corporate, Wholesale onboarding | Loyalty_Programs |
| KYC_Document_Requests | Customer KYC collection and review | Customers, Employees |
| Transport_Rates | Effective INR rate bands | — |
| Loyalty_Programs | Earning, redemption, tier, expiry rules | — |
| Shipment_Requests | Quote-to-delivery shipment record | Customers, Hubs, Rates, Agents |
| Manifests | One physical journey leg | Hubs, Employees |
| Manifest_Items | Auditable shipment-to-leg link | Manifests, Shipments |
| Agent_Tasks | Pickup and delivery work | Shipments, Hubs, Employees |
| Shipment_Tracking_Events | Append-only tracking history | Shipments, Manifests, Tasks |
| Loyalty_Transactions | Authoritative signed points ledger | Customers, Shipments, Programmes |
| Loyalty_Redemptions | Cash and shipment-discount redemption | Customers, Shipments, Programmes |
| Audit_Log | Immutable operational audit | — |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| Hub/Employee master views | List, Map | Hubs, Employees |
| Customer/KYC views | List, Kanban, Map | Customers, KYC Requests |
| Rate/Programme matrices | List | Rates, Programmes |
| Shipment views | List, Kanban, Timeline | Shipments |
| Manifest journey views | List, Kanban | Manifests, Manifest Items |
| Agent work views | Kanban, List, Calendar | Agent Tasks |
| Tracking views | List, Timeline | Tracking Events |
| Loyalty views | List, Kanban | Transactions, Redemptions |
| Audit Trail | List | Audit Log |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Customer_Dashboard | Self-service overview | KPIs, shipments, KYC, loyalty |
| Hub_Dashboard | Hub operations | Workload, manifests, agents |
| Agent_Dashboard | Assigned field work | Tasks, manifests, status cards |
| Admin_Dashboard | Network oversight | KPIs, queues, agent summary |

## Design Decisions
- One Manifest equals one journey leg; Manifest_Items provides auditable many-to-many routing.
- Distance is manually confirmed; rate precedence is deterministic and configurable.
- Loyalty ledger entries are signed and authoritative; customer balances are caches.
- Tracking and audit histories are append-only.
- Five profiles enforce customer, agent, operations, hub-manager, and administrator access.
- Phone/tablet menus surface focused work while retaining complete component mappings.