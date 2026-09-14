## Application Overview
Prop-GPT is a property operations application for a single superadmin owner. It manages multi-unit properties and individual villas, tenants, leases, monthly rent, work orders, external API intake, status notifications, and operational tracking.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Properties | Property portfolio | — |
| Units | Units for multi-unit properties | Property |
| Tenants | Tenant contacts and unique phones | — |
| Leases | Occupancy and rental agreements | Tenant, Property, Unit |
| Rental Payments | Monthly obligations and receipts | Lease, Tenant, Property, Unit |
| Work Orders | Maintenance requests and lifecycle | Tenant, Property, Unit |
| Work Order Status History | Append-only status audit trail | Work Order |
| Work Order Tracker Filter | Tracking-page selector | Work Order |
| API Configuration | Encrypted API authentication key | — |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All Properties | List | Properties |
| Property Map | Map | Properties |
| All Units | List | Units |
| Unit Availability Board | Kanban | Units |
| All Tenants | List | Tenants |
| All Leases | List | Leases |
| Active Leases | List | Leases |
| All Rental Payments | List | Rental Payments |
| Outstanding Rent | List | Rental Payments |
| All Work Orders | List | Work Orders |
| Work Order Board | Kanban | Work Orders |
| All Status History | List | Work Order Status History |
| Work Order Status Timeline | Timeline | Work Order Status History |
| API Configurations | List | API Configuration |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Operations Dashboard | Portfolio and operations overview | KPIs, occupancy, rent, work-order status, activity |
| Work Order Tracking | Selected-order audit view | Selector, summary, chronological timeline |

## Design Decisions
- Property types are restricted to multi-unit property or individual villa.
- Units are separate records and only valid for multi-unit properties.
- Tenant phone is unique E.164 and is the external work-order identity.
- Active leases derive the property and optional unit for API work orders.
- Rent obligations are generated monthly; reminders run on the 27th at 09:00 America/New_York.
- Work-order status changes create history and email the tenant.
- API secrets are encrypted, private, configurable, and never exposed in reports.
- Web UI is optimized for the Property Superadmin profile.