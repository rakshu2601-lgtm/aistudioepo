# Student Attendance & Training-Hours Tracking System

## Application Overview
A Zoho Creator application for managing student enrollment, daily attendance, and training-hours tracking across multiple program components. Instructors approve training sessions via a blueprint workflow, and a mobile-friendly GPS-enforced timer page lets students start and stop training sessions from the field.

## Forms

| Form Name | Purpose | Key Lookups |
|---|---|---|
| Programs | Training program catalog (CDL, etc.) with total required hours | — |
| Program_Components | Individual modules per program (Classroom, Yard, Road) with required hours | Programs |
| Training_Locations | Approved GPS training sites with configurable geofence radius | — |
| Students | Student profiles, enrollment, instructor assignment, completion status | Programs |
| Attendance | Daily attendance records with check-in/check-out and auto-calculated duration | Students |
| Training_Sessions | Individual training session records with start/end time, GPS, duration, credited hours | Students, Program_Components |
| Student_Component_Progress | Per-student per-component progress tracking with formula fields for remaining hours and % complete | Students, Program_Components |

## Reports

| Report Name | Type | Source Form |
|---|---|---|
| All_Programs / Active_Programs | List | Programs |
| All_Components / Components_By_Program | List | Program_Components |
| All_Locations / Active_Locations | List | Training_Locations |
| All_Students / Active_Students / Students_By_Program / Completed_Students | List | Students |
| All_Attendance / Attendance_By_Student / Today_Attendance | List | Attendance |
| Attendance_Calendar | Calendar | Attendance |
| All_Sessions / Active_Sessions / Pending_Approvals / Approved_Sessions / My_Sessions / Sessions_By_Student | List | Training_Sessions |
| Sessions_Kanban | Kanban | Training_Sessions |
| All_Progress / Progress_By_Student / Completed_Components / Incomplete_Components | List | Student_Component_Progress |
| Progress_Pivot | Pivot Table | Student_Component_Progress |

## Pages

| Page Name | Purpose | Key Components |
|---|---|---|
| Admin_Dashboard | Admin analytics overview | KPI cards, bar/donut charts, component progress bars, embedded Active Sessions and Pending Approvals reports, attendance trend line chart |
| Student_Progress | Per-student progress dashboard | Student header card, overall KPI strip, per-component progress bars, embedded recent sessions and attendance |

## Design Decisions

- **Blueprint for session approval**: Training sessions move through `In Progress → Pending Approval → Approved/Rejected` via a blueprint; hours are only credited to a student's progress when a session is `Approved`.
- **Credited hours cap**: The on-edit workflow caps `Credited_Hours` at the remaining hours for that component so completed components are never over-counted, while `Actual_Duration_Hours` retains the true session duration for audit purposes.
- **Auto-create progress records**: An on-add workflow on the Students form auto-creates one `Student_Component_Progress` record for each component in the enrolled program so tracking is always ready.
- **Forms in unused menu block**: All data-entry forms are in the `unused` menu block since all data access is through reports, keeping navigation clean.
