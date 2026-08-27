## Application Overview

Task Hub is a simple personal to-do application for capturing, prioritising, scheduling, and completing everyday tasks. It provides list, Kanban, and calendar views plus a page-first dashboard with live task counts. The package uses India-friendly date and time settings.

## Forms

| Form Name | Purpose | Key Lookups |
|---|---|---|
| Tasks | Stores task details, status, priority, due date, and completion state | None |

## Reports

| Report Name | Type | Source Form |
|---|---|---|
| All Tasks | List | Tasks |
| Task Board | Kanban | Tasks |
| Task Calendar | Calendar | Tasks |

## Pages

| Page Name | Purpose | Key Components |
|---|---|---|
| Task Hub | Main personal productivity workspace | KPI cards, Add Task action, links to all reports |

## Design Decisions

- Uses built-in Creator profiles; no custom roles are needed for a personal app.
- Uses declarative mandatory fields and defaults instead of workflows.
- Keeps the Task Hub page as the primary menu entry; raw components remain reachable from it.
- Includes seven sample records in `Components/Tasks/Sample_Data.md` for manual CSV import.
- Configured for `Asia/Kolkata`, `DD-MMM-YYYY`, and 12-hour time.
