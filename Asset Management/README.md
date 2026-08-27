## Application Overview
Asset Management is a web-based IT inventory application for maintaining asset stock, receipts, adjustments, assignments, returns, suppliers, employees, and a permanent movement audit. It flags assets when available stock falls below 10% of maximum stock and sends a configurable email once per downward threshold crossing.

## Forms
| Form Name | Purpose | Key Lookups |
|---|---|---|
| Asset Categories | Standard asset classifications | — |
| Vendors | Supplier directory | — |
| Employees | Employee directory | — |
| Alert Settings | Low-stock email recipients | — |
| Assets | Asset catalog and stock health | Category |
| Stock Transactions | Receipts, adjustments, retirements | Asset, Vendor |
| Asset Assignments | Issue and return quantities | Asset, Employee |
| Inventory Audit | Stock movement history | Asset |

## Reports
| Report Name | Type | Source Form |
|---|---|---|
| All Asset Categories | List | Asset Categories |
| All Vendors | List | Vendors |
| All Employees | List | Employees |
| Alert Configuration | List | Alert Settings |
| All Assets | List | Assets |
| Low Stock Assets | List | Assets |
| Assets with Stock | List | Assets |
| Asset Stock Summary | List | Assets |
| All Stock Transactions | List | Stock Transactions |
| Stock Receipts | List | Stock Transactions |
| Recent Stock Activity | List | Stock Transactions |
| All Asset Assignments | List | Asset Assignments |
| Currently Assigned Assets | List | Asset Assignments |
| Returned Assets | List | Asset Assignments |
| Inventory Audit Log | List | Inventory Audit |

## Pages
| Page Name | Purpose | Key Components |
|---|---|---|
| Asset Dashboard | Operational overview | KPIs, charts, low-stock table, recent activity |

## Design Decisions
- Low stock means `Current Stock / Maximum Stock × 100 < 10`.
- Email sends once per downward crossing and resets after recovery to 10% or higher.
- Processed/deducted/restored guards prevent duplicate stock posting.
- Returns restore stock; lost assets do not.
- Inventory Audit is workflow-written and read-only for users.
- Active profiles are IT Administrator and IT Staff.
- Legacy request/complaint components are hidden because deletion was not approved.
