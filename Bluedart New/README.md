## Application Overview

Role-oriented logistics operations for onboarding, shipments, first/last mile, hubs, linehaul, exceptions, finance, and loyalty. Eight audience spaces provide focused queues and dashboards on web, tablet, and phone.

## Forms

| Form Name | Purpose | Key Lookups |
|---|---|---|
| Customers; Customer_KYC_Documents; KYC_Document_Types | Onboarding/KYC | Customer, document type |
| Shipment_Requests; Shipment_Tracking_Events; Shipment_Exceptions; NDR_Instructions; NDR_Response | Shipment lifecycle | Customer, hubs, shipment |
| Pickup_Run_Sheets; Pickup_Run_Sheet_Items | First mile | Hub, agent, shipment |
| Delivery_Run_Sheets; Delivery_Run_Sheet_Items | Last mile | Hub, agent, shipment |
| Logistics_Bags; Bag_Shipments; Manifests; Manifest_Bags | Hub/linehaul custody | Hubs, route, shipment |
| Hubs; Hub_Pincode_Mapping; Transport_Routes; Vehicles; Operations_Users | Network masters | Hubs, routes |
| Rate_Cards; Rate_Slabs | Pricing | Rate card |
| Invoices; Payment_Transactions; COD_Remittances; Account_Ledger | Finance | Customer, shipment, invoice |
| Loyalty_Tiers; Loyalty_Rules; Loyalty_Transactions | Loyalty | Customer, tier |
| App_Configuration; Audit_Log; Communication_Log | Controls/evidence | Business records |

## Reports

| Report Name | Type | Source Form |
|---|---|---|
| My_Profile; Verification_Pending; KYC_Review_Queue | List/actions | Customers/KYC |
| Unassigned_Orders; Pickup_Queue; Delivery_Queue; Shipment_Status_Board | List/Kanban | Shipments |
| My_Pickup_Runs; Today_Pickup_Planner; My_Pickup_Tasks; Failed_Pickups | List/actions | Pickup runs/items |
| My_Delivery_Runs; Last_Mile_Dispatcher; My_Delivery_Tasks; Failed_Deliveries | List/actions | Delivery runs/items |
| Open_Bags; In_Transit_Bags; Bag_Status_Board; Bag_Contents | List/Kanban | Bags |
| All_Manifests; Manifest_Status_Board; Expected_Master_Bags; Manifest_Reconciliation | List/Kanban | Manifests |
| Shipment_Timeline; Customer_Tracking_Events | Timeline | Tracking events |
| Shipment_Exception_Queue; Critical_Exceptions; Exception_Status_Board | List/Kanban | Exceptions |
| NDR_Instruction_Action_Queue; NDR_RTO_Pending | List/actions | NDR |
| Invoice_Statement; Overdue_Invoices; My_Invoices; Invoice_Due_Calendar | List/Calendar | Invoices |
| Payment_Transaction_Register; Failed_Payments; COD_Pending_Remittance | List/actions | Payments/COD |
| Ledger_Ageing; Credit_Utilization; Outstanding_Accounts | List | Ledger |
| Active_Hub_Map; Hub_Capacity; Active_Routes; Route_Capacity; Vehicle_Compliance | Map/List/Calendar | Network masters |
| Published_Rate_Cards; Expiring_Rate_Cards; Active_Slabs | List/Calendar | Pricing |
| My_Loyalty_History; Points_Expiring_Soon; Active_Tier_Benefits | List | Loyalty |

## Pages

| Page Name | Purpose | Key Components |
|---|---|---|
| Customer_Dashboard | Self-service | KYC, shipments, invoices, loyalty |
| KYC_Review | Review workspace | Customer/documents |
| Shipment_Tracking | Visibility | Milestones/timeline |
| Agent_Dashboard | Field day view | Pickup/delivery queues |
| Hub_Dashboard | Hub command | Capacity, bags, manifests |
| Admin_Dashboard | Oversight | KPIs/control tower |

## Design Decisions

- ModulePermissions control visibility in profile-oriented spaces.
- POC actions retain state, ownership, assignment, hub, and integrity checks while removing hard-coded profile-name gates.
- Customer access remains tied to login email/ownership.
- US-oriented formats and responsive navigation are used.
