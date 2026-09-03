# Ice Cream Management

A Zoho Creator DS application covering the full lifecycle of an ice cream
business: supplier and raw-material sourcing (with cold-chain tracking),
recipe-driven production with a Blueprint-managed quality workflow, lot-based
finished-goods inventory with expiry and FEFO shipment, and customer sales —
plus cold storage / temperature monitoring across the operation.

## Application Overview

The app tracks perishable ingredients and packaging from purchase through to
finished, expiry-dated ice cream stock. Production batches follow a six-stage
Blueprint (Planned → In Production → Quality Check → Approved/Rejected →
Packaged); starting production auto-consumes raw-material stock per the
product's recipe, and approving a batch creates a new expiry-dated stock lot
in Finished Goods Inventory. Sales orders ship against that inventory using
FEFO (first-expiry-first-out) allocation across lots. Cold storage units are
monitored via temperature logs that automatically flag a unit "Needs
Attention" when a reading drifts more than 3°C from its target. Three custom
profiles (Production Staff, Sales Staff, Shop Manager) scope access to their
relevant modules; two dashboards give operations-wide and sales-wide KPI
views.

## Forms

| Name | Purpose | Key Lookups |
|---|---|---|
| Suppliers | Vendor master | — |
| Customers | Buyer master | — |
| Cold_Storage_Units | Freezer / cold-room master | — |
| Temperature_Logs | Per-unit temperature readings | Cold_Storage_Units |
| Raw_Materials | Ingredient/packaging stock, with expiry | Suppliers, Cold_Storage_Units |
| Products | Flavor/SKU catalog + recipe (Recipe_Items subform) | Raw_Materials |
| Raw_Material_Purchases | Purchase orders (PO_Items subform) | Suppliers, Raw_Materials |
| Production_Batches | Blueprint-driven production run | Products, Cold_Storage_Units |
| Quality_Checks | QC records per batch (taste, texture, overrun %, melt time) | Production_Batches |
| Finished_Goods_Inventory | Lot-based stock, one row per approved batch | Products, Production_Batches, Cold_Storage_Units |
| Sales_Orders | Customer orders (Order_Items subform), FEFO shipment | Customers, Products |

## Reports

| Name | Type | Source Form |
|---|---|---|
| All_Suppliers / Active_Suppliers | list | Suppliers |
| All_Customers / Active_Customers | list | Customers |
| All_Cold_Storage_Units / Units_Needing_Attention | list | Cold_Storage_Units |
| All_Temperature_Logs / Out_Of_Range_Logs | list | Temperature_Logs |
| All_Raw_Materials / Low_Stock_Materials / Expiring_Raw_Materials | list | Raw_Materials |
| All_Products / Active_Products / Products_Board | list / list / kanban | Products |
| All_Purchase_Orders / Pending_Purchase_Orders | list | Raw_Material_Purchases |
| All_Production_Batches / Batch_Status_Board / Production_Calendar | list / kanban / calendar | Production_Batches |
| All_Quality_Checks / Failed_Checks | list | Quality_Checks |
| All_Finished_Goods / Expiring_Soon / Expired_Stock | list | Finished_Goods_Inventory |
| All_Sales_Orders / Pending_Sales_Orders / Delivery_Calendar | list / list / calendar | Sales_Orders |

## Pages

| Name | Purpose | Key Components |
|---|---|---|
| Operations_Dashboard | Production/QC/inventory/cold-storage KPIs | HTML snippet, ZCS-styled stat tiles, stage breakdown, quick links |
| Sales_Dashboard | Orders/revenue/customer KPIs | HTML snippet, ZCS-styled stat tiles, status/customer-type breakdown, quick links |

## Design Decisions

- **Lot-based Finished_Goods_Inventory, not one row per product**: each
  approved production batch inserts its own stock-lot record (`insert into
  Finished_Goods_Inventory`) carrying its own `Manufacture_Date` /
  `Expiry_Date`. This is the key departure from a simple aggregate-stock
  model, and it's what makes real expiry tracking and FEFO shipment possible
  for a perishable product — an aggregate row per product has nowhere to put
  a per-batch expiry date.
- **FEFO shipment via a Sales_Orders `on success` workflow**: shipping an
  order (`Status == "Shipped"`) fetches that product's in-stock lots `sort by
  Expiry_Date` and walks them oldest-first, draining each lot before moving to
  the next, marking a lot "Sold Out" once fully drawn down.
- **Auto-expiry via a form-date schedule, not a batch script**: each
  Finished_Goods_Inventory lot carries its own one-time schedule
  (`Expire_Finished_Goods_Lot`, `start = Expiry_Date at "00:00:00"`) that
  flips `Status` to "Expired" exactly when that lot's expiry date arrives —
  the idiomatic Deluge pattern for per-record date-triggered automation,
  rather than a nightly sweep.
- **Temperature_Logs drives Cold_Storage_Units.Status**: a log more than 3°C
  from its unit's target temperature marks the unit "Needs Attention"; a
  subsequent in-range reading resets it to "Operational" — mirrors the
  Equipment/Maintenance_Logs status-sync pattern used elsewhere in this
  workspace's similar apps, adapted for continuous temperature monitoring
  instead of discrete maintenance jobs.
- **No pivot chart/table report**: the bundled DS reference documents `list`,
  `spreadsheet`, `calendar`, `timeline`, `kanban`, `map`, and `custom` as the
  supported report types — `pivot chart`/`pivot table` appear only in a
  higher-level overview doc with no backing syntax. `Products_Board` (a
  kanban grouped by `Status`) was used instead to keep report-type variety
  without guessing unsupported syntax.
- **Custom profiles are additive, not exhaustive**: only Production_Staff,
  Sales_Staff, and Shop_Manager are defined; the default
  Administrator/Developer profiles retain full access to everything.
- **Dashboards use HTML snippets + hand-styled ZCS-token CSS** (referencing
  the fetched `zcs-global.css` utility sheet once per page) rather than
  native panels/charts, with aggregate (not per-user-scoped) queries since
  both are operational/admin views.

## Verification

Compiled clean: `zcreator diagnostics Components` → `0 error(s), 0 warning(s)`.
Packing/uploading to a live Zoho Creator account is available on request via
`zcreator pack` / `zcreator upload` but was not performed automatically.
