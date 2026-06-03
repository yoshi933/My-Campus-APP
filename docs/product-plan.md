# Product Plan: Campus Learning App

## 1. Vision and Outcomes

Build a role-based campus app that helps learners stay on top of school life and helps educators manage class operations with less manual overhead.

### Target outcomes
- Reduce missed homework and forgotten items.
- Improve visibility into attendance and grade trends.
- Give a single daily hub for schedule, tasks, and school events.
- Support educators with lightweight class operations and communication.

## 2. Scope

### In scope (initial releases)
- Dashboard
- Homework management
- Timetable and timetable import
- Teacher panel
- Checklist
- Grades and attendance
- School calendar

### Out of scope (initial releases)
- Billing/payments
- Parent portal (separate product stream)
- Third-party LMS grade sync beyond CSV/manual import

## 3. User Roles and Access Model

## Student
- View personal dashboard, timetable, homework, checklist, grades/attendance, events.
- Submit homework and manage personal checklist state.

## Teacher
- Access teacher panel for class-level summary.
- Record attendance and grades for assigned classes.
- Review homework submissions and send announcements/templates.

## School Staff / Admin
- Manage school-wide calendar events and operational templates.
- Control user role assignments and approval workflows.

## 4. Core Modules and Functional Requirements

## 4.1 Dashboard
Purpose: Daily decision screen.

Must include:
- Next class and today schedule summary.
- Homework due soon and completion progress.
- Attendance/grade snapshot.
- Upcoming events and recent notifications.

## 4.2 Homework
Purpose: Assignment tracking and submission workflow.

Must include:
- Assignment list (card + list modes).
- Filters (subject/status/due date).
- Assignment detail with attachments/comments.
- States: not started, in progress, submitted, graded, overdue.

## 4.3 Timetable
Purpose: Weekly class schedule and lesson context.

Must include:
- Week grid with periods and subject cards.
- Lesson detail panel (room, teacher, notes, related homework).
- Week navigation and print/export action.

## 4.4 Timetable Import
Purpose: Add/update timetable from image/PDF.

Must include:
- Upload + validation for image/PDF.
- OCR extraction result preview.
- Manual correction before publish.
- Import job history and status.

## 4.5 Teacher Panel
Purpose: Operational hub for class management.

Must include:
- KPI cards (attendance, pending grading, unread messages).
- Student/class table with quick actions.
- Shortcut actions for attendance, grading, and communication templates.

## 4.6 Checklist
Purpose: Prevent forgotten materials and prep steps.

Must include:
- Reusable checklist templates.
- Daily personal checklist completion.
- Item-level completion history.

## 4.7 Grades and Attendance
Purpose: Performance visibility and quick updates.

Must include:
- Student: trends and subject summaries.
- Teacher: score/attendance entry forms.
- Calendar-style attendance visualization.

## 4.8 Calendar
Purpose: School events and preparation requirements.

Must include:
- Month/week views.
- Event detail (time, location, audience, required items).
- Event creation/editing for authorized roles.

## 5. Cross-Cutting Requirements

### Security and privacy
- Role-based authorization at route and action levels.
- Minimize student personal data visibility by default.
- Audit trail for attendance/grade edits.

### Accessibility
- Keyboard-first navigation for key tasks.
- Color + icon/text dual cues for statuses.

### Localization
- Date/time and language-ready content structure.

### Performance
- Fast initial dashboard load.
- Async processing for timetable OCR/import jobs.

## 6. Initial Data Domain (Planning Baseline)

Primary entities:
- User
- RoleAssignment
- ClassGroup
- Subject
- TimetableEntry
- Assignment
- Submission
- AttendanceRecord
- GradeRecord
- ChecklistTemplate
- ChecklistItem
- CalendarEvent
- Notification
- ImportJob

(See `docs/types/domain-model.stub.yaml` for a starter schema scaffold.)

## 7. Phased Implementation Plan

## Phase 0 — Foundation
- Project setup, environments, auth scaffolding, UI tokens/components.
- Shared layout (sidebar/header/content), navigation shell.

Exit criteria:
- Role-aware navigation working.
- Baseline design system available.

## Phase 1 — Student Core
- Dashboard, Homework, Timetable, Checklist, Calendar (student read/use flows).

Exit criteria:
- Student can complete a full daily loop: view schedule → track homework → confirm checklist → review events.

## Phase 2 — Academic Records
- Grades and attendance views plus teacher entry workflow.

Exit criteria:
- Teacher can record attendance/grades; student can view updates.

## Phase 3 — Teacher Operations
- Teacher panel KPIs, class table actions, messaging templates.

Exit criteria:
- Teacher can run daily class workflow from one screen.

## Phase 4 — Timetable Import
- OCR import pipeline with review/correction + publish.

Exit criteria:
- Timetable can be imported from file with correction before activation.

## Phase 5 — Optimization
- Analytics, AI-assisted prioritization, performance hardening, release readiness.

Exit criteria:
- Monitoring + feedback loop in place for iterative improvement.

## 8. Delivery and Handoff Artifacts

For each module, create and maintain:
- Module spec (`docs/templates/module-spec-template.md`)
- Acceptance criteria checklist (`docs/templates/implementation-checklist-template.md`)
- Domain model updates (`docs/types/domain-model.stub.yaml`)

## 9. Open Decisions

- Auth provider and identity lifecycle.
- Storage strategy for files/attachments.
- OCR provider selection and confidence thresholds.
- Notification channels and delivery guarantees.
- Data retention policies for attendance/grade history.
