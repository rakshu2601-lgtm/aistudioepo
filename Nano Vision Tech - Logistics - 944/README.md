## Application Overview
Nano Vision Tech Logistics manages the full sales-to-delivery lifecycle: leads, sourcing, supplier quotes, purchase orders, invoices, logistics, quality checks, delivery, returns, and audit history. Responsive operational pages provide aligned, live-data workspaces with contextual actions and safe empty states.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Add_Customer | Customer master | — |
| Add_Supplier | Supplier master | — |
| Add_Product | Product catalog | — |
| Add_Lead | Sales leads | Customer, Sales Agent |
| Create_Sales_Order | Customer requirements | Lead, Customer, Sales Agent |
| Add_Supplier_Quote | Supplier offers | Sales Order, Supplier |
| Create_Purchase_Order | Approved sourcing | Sales Order, Quote, Supplier, Customer |
| Add_Supplier_Invoice | Supplier billing | Purchase Order, Supplier |
| Create_Logistics_Booking | Shipment and receipt | Purchase Orders, Suppliers |
| Create_Return_Request | Delivered-item returns | Purchase Order, Customer, Sales Order |
| Add_History | Central audit trail | Business transactions, Employee |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All_Customers / All_Suppliers / All_Products | List | Master forms |
| All_Leads / All_Sales_Orders | List | Lead and sales order forms |
| All_Supplier_Quotes / All_Purchase_Orders | List | Sourcing forms |
| All_Supplier_Invoices | List | Add_Supplier_Invoice |
| All_Logistics_Bookings / All_Return_Requests | List | Logistics and return forms |
| All_Histories | List | Add_History |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Admin, Sales, Sourcing, Logistics, R&D Dashboards | Role-focused operations | Metrics, exception queues, live record sections |
| Supplier_Dashboard / Requests_For_Quote | Supplier workspace | Identity guard, RFQs, quotes, POs, invoices |
| Leads / Lead_Detail | Lead pipeline | Customer context, products, actions, history |
| Sales_Orders / Sales_Order_Detail | Order lifecycle | Sourcing, finance, logistics, returns |
| Supplier_Quotes / Quote_Comparison | Sourcing decisions | Coverage, variance, selection actions |
| Purchase_Orders / Purchase_Order_Detail | Fulfilment | Approval, products, invoices, delivery |
| Supplier_Invoices / Supplier_Invoice_Detail | Finance | Payment evidence and source verification |
| Logistics_Bookings / Logistics_Booking_Detail | Receiving | Milestones, quantities, QC |
| Return_Requests / Return_Request_Detail | Return resolution | Triage, evidence, financial context, timeline |
| Products / Product_Detail | Product master | Catalog, lifecycle, cross-module usage |
| History | Audit view | Order context and activity timeline |
| Confirmation_Page / Detail_View_Page | Helpers | Generic success state and allowlisted preview |

## Design Decisions
- Operational records are primary; KPIs are secondary and non-clickable.
- Responsive layouts use fixed-height scrolling and mobile-friendly cards.
- Optional lookups and supplier identity are guarded with controlled states.
- Detail/helper pages remain routable but hidden from primary device menus.
- Legacy setup administration remains largely unchanged.
