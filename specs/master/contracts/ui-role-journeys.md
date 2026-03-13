# UI Contract: Role-Based Journeys and Interaction Patterns

## Shared Interaction Contract
- Form interactions:
  - Required fields show inline validation on blur and on submit.
  - Submit actions show pending state, then success or error feedback.
- Navigation:
  - Role-aware routes hide unauthorized pages.
  - Unauthorized access attempts route to role home with explanatory message.
- Data-driven screens:
  - MUST define loading, empty, and error state components.
  - Empty states include clear action hints (add skill, adjust filters, upload evidence).

## Employee Journey
- Entry point: Employee dashboard/profile page.
- Decision points:
  - Add/update/remove skill entries.
  - Upload certification evidence.
- Outcome:
  - Skill entries saved as `self-declared`.
  - History trail visible for each modified entry.

## Manager Journey
- Entry point: Validation queue page for direct reports.
- Decision points:
  - Verify proficiency.
  - Request more evidence.
  - Reject claim with rationale.
- Outcome:
  - Validation metadata persisted (`validatedBy`, `validatedAt`, status).
  - Employee notified via in-app status update.

## Admin Journey
- Entry point: Skill framework management page.
- Decision points:
  - Create/edit/deactivate categories, subcategories, skills, level definitions.
- Outcome:
  - Updated taxonomy available instantly in employee profile forms.

## Leadership Journey
- Entry point: Analytics dashboard page.
- Decision points:
  - Select report type and filters.
  - Compare team/org trend indicators.
- Outcome:
  - Decision-ready charts and summaries for staffing, workforce visibility, and development planning.

## Dashboard Readability Contract
- Charts MUST include axis labels, legend, and concise title.
- Threshold indicators MUST use clear text labels in addition to color.
- Summary cards MUST explain why a metric matters to business outcomes.
