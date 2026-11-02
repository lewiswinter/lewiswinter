# Operations CRM & Workflow Transformation

**One source of truth for customer data, with automation and commercial follow-up built around it**

I led the redesign of booking administration and developed an internal CRM that brought customer, booking and operational information into one place. Beyond removing repetitive admin, the bigger opportunity was **using that shared data to support growth**: sending timely communications, prompting follow-ups, identifying customers who had not rebooked and giving managers a clearer view of where sales attention was needed.

## Results

| Measure | Before | After |
| --- | --- | --- |
| Typical booking administration | Approximately 4–5 minutes | Around 1 minute |
| Time spent per booking | — | **Approximately 75–80% lower** |
| Annual capacity released | — | **Estimated 100–133 hours**, across roughly 2,000 bookings |
| Customer and booking information | Spread across separate tools | **One shared record and history** to support scheduling, communications and follow-up |
| Repeat-business activity | Relied heavily on manual tracking | **Reminders, booking-gap filters and customer follow-up workflows** |

*Capacity figures are estimates based on typical handling times and annual booking volume; the customer-growth benefits are operational capabilities, not a claimed measured sales uplift.*


## The problem

Booking details lived in multiple Google Sheets and a separate contacts application. Staff repeated entries, prepared emails manually and checked different places to see what had been completed. This was particularly difficult during seasonal peaks, when bookings, photographers and production deadlines all needed coordinating.

Off-the-shelf CRMs added complexity without fitting how the business operated. I wanted each nursery's history, bookings, communications and next actions linked together, rather than scattered across different systems. That would also make it possible to build repeatable sales and service workflows on top of reliable data.

## My role and the solution

I mapped the booking and follow-up processes, identified duplicated work, designed the new workflows and developed the application. I also worked through testing and iteration as the team began using it.

The platform brought together:

- **Client and booking records:** nursery details, booking history, notes, assigned actions and activity logs.
- **Operational coordination:** field scheduling, progress boards, overdue items and reminders.
- **Automated communications:** booking confirmations and pre-shoot emails driven by the booking record, with reminders and follow-up actions visible to staff.
- **Customer growth and retention:** booking-gap filters, reminders and rebooking visibility to help the team identify customers needing attention and pursue repeat business.
- **Commercial reporting:** booking targets, year-on-year comparisons, revenue dashboards, client quartiles, average order value and order rate.

Built using **Next.js, TypeScript and Supabase (PostgreSQL, authentication and row-level security)**. The application was developed for a multi-user operation with different staff permissions.

### What changed

| Previously | With the CRM |
| --- | --- |
| Booking details entered in several systems | One shared booking record and history |
| Updates and next steps checked manually | Clear statuses, ownership, reminders and outstanding actions |
| Separate information needed for scheduling | A shared field schedule linked to the booking workflow |
| Limited ability to compare performance | Structured reporting across clients, booking targets and revenue |
| Follow-ups depended on individual tracking | Reminders and filters to identify unbooked clients and outstanding customer actions |
| Emails prepared from disconnected information | Booking-linked confirmation and reminder workflows |

Centralising the data meant the business could develop new workflows without creating another standalone spreadsheet or relying on individual staff to remember every customer follow-up.

## Platform walkthrough

These screenshots contain fictional demonstration records and figures.

### Client record

The nursery record brings together booking history, notes, reminders and related activity.

![CRM client record showing booking details and operational activity](images/01-nursery-record.png)

### Field scheduling

The schedule gives office staff a shared view of assignments and booking activity.

![Field scheduling view in the operations CRM](images/02-field-schedule.png)

### Revenue reporting

Client and staff performance can be reviewed using average order value, order rate, targets and comparisons over time.

![Revenue dashboard with fictional commercial reporting data](images/03-revenue-dashboard.png)

### Scenario modelling

Managers can test assumptions about potential revenue improvements. **Modelled scenarios are not claimed as achieved results.**

![Revenue scenario modelling using fictional figures](images/04-revenue-scenario-modelling.png)

## Testing, security and release discipline

Because the application supports live operational records and communications, reliability and access control were part of development rather than added at the end.

**Functional and smoke testing.** The project used automated Vitest checks and a Playwright browser harness. Smoke checks covered login, the dashboard, client navigation and the booking flow. More involved end-to-end checks exercised booking creation, scheduling visibility and navigation consistency. Type checking, linting and regression tests supported release reviews.

**Security review and remediation.** I used Claude Code to support structured reviews of authentication, Supabase row-level security, API permissions, PostgreSQL function privileges and activity-log integrity. Reviews were followed by practical fixes and role-based tests, including attempts to perform actions or attribute changes outside the user's permissions.

**Database hardening.** One review phase addressed the configuration and execution privileges of **15 database functions**. A broader least-privilege review covered **40 tables**, with validation recorded in staging; deployment and production verification were tracked separately. Selected access-control changes were also checked against production roles.

**Traceability and privacy.** Role-based permissions, activity history and shared statuses make hand-offs more accountable. Production source code and business records remain private; the images here are fictional demonstrations.

## Operational and commercial value

**A stronger base for growth.** Bringing customer and booking data together gave the business a consistent view of each nursery relationship. The team could identify booking gaps, see which customers needed recontacting and act on those opportunities rather than waiting for enquiries to arrive.

**More consistent customer contact.** Booking-linked confirmations, pre-shoot communications and internal reminders made it easier to reach more customers at the right time, follow up outstanding opportunities and keep repeat-business activity moving during busy periods.

**Capacity to scale.** Reducing repetitive booking work freed up administrative capacity. Centralised records also made it easier for multiple staff to coordinate bookings, scheduling and follow-ups without building new disconnected processes each time the business grew.

**Better commercial decisions.** Revenue and performance reporting brought booking, order and client information closer together, helping managers identify where to focus attention and investigate ways to improve sales.

I led the work from process mapping and redesign through development, testing and operational adoption. **The CRM was not just an admin time-saving tool; it became a way to manage customer relationships and growth more systematically.**

*These are supported workflow and commercial capabilities; no specific additional sales volume is attributed to the CRM without a measured comparison.*

---

[← Back to portfolio](../README.md) · [Recruitment agent](ai-recruitment-operations-agent.md) · [Image automation and AI vision](image-editing-automation-ai-vision.md)
