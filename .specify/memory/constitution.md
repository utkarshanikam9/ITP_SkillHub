<!--
Sync Impact Report:
- Version change: 1.0.0 -> 2.0.0
- Modified principles:
    - I. Code Quality & Clean Architecture -> I. Modular & Maintainable Frontend Architecture
    - II. Comprehensive Testing Standards -> II. Separation of UI, Domain Models, and Services
    - III. User-Centric Design & Experience (UX) -> III. API-Simulated Mock Data Services
    - IV. Architectural Consistency & Standardization -> IV. Governed State Management
    - V. Performance & Scalability First -> V. Standardized Skill Analytics Visualization
    - Added VI. Role-Based User Experience Integrity
    - Added VII. Prototype-to-Production Scalability
- Added sections: Technology Standards, Delivery & Quality Gates
- Removed sections: Performance Standards, Quality Gates
- Templates requiring updates:
    - .specify/templates/plan-template.md (✅ updated)
    - .specify/templates/spec-template.md (✅ updated)
    - .specify/templates/tasks-template.md (✅ updated)
    - .specify/templates/commands/*.md (✅ not present; no action required)
    - .github/agents/*.md (✅ checked; no outdated agent-specific naming found)
- Follow-up TODOs:
    - TODO(RATIFICATION_DATE): Original ratification date was not available in repo history.
-->

# Skill Matrix System Constitution
<!-- Example: Spec Constitution, TaskFlow Constitution, etc. -->

## Core Principles

### I. Modular & Maintainable Frontend Architecture
All features MUST be implemented as small, composable modules with single-purpose
responsibilities. Components, hooks, utilities, and services MUST remain focused,
readable, and easy to refactor. Feature delivery that introduces avoidable coupling,
duplicated logic, or unclear ownership is non-compliant.

Rationale: maintainability and predictable iteration speed are mandatory for a
prototype expected to evolve into production architecture.

### II. Separation of UI, Domain Models, and Services
Presentation logic MUST stay in UI layers, domain/data definitions MUST stay in
typed model modules, and data retrieval/transformation MUST stay in service modules.
React components MUST NOT embed raw mock payloads, parsing rules, or business rules.

Rationale: strict layering allows independent testing and smooth replacement of mock
services with real APIs later.

### III. API-Simulated Mock Data Services
Prototype data access MUST be implemented through mock services that simulate API
behavior, including async response patterns, predictable error paths, and typed
contracts. Direct JSON imports inside feature components are prohibited except in
service implementation modules.

Rationale: realistic service boundaries de-risk backend integration and prevent
frontend architecture debt.

### IV. Governed State Management
Shared application state MUST use either React Context API or Zustand. The selected
store pattern for a feature MUST be documented in the plan and applied consistently.
State updates MUST be predictable and typed; ad hoc global mutable state is forbidden.

Rationale: explicit state governance reduces regression risk across role-based flows.

### V. Standardized Skill Analytics Visualization
Skill analytics views MUST use Recharts or Chart.js through reusable chart adapters
or wrapper components. Visualizations MUST consume typed view models rather than raw
service payloads. Chart behavior and axis semantics MUST be documented in specs.

Rationale: standard charting patterns keep analytics maintainable and consistent.

### VI. Role-Based User Experience Integrity
Employee, Manager, Admin, and Leadership experiences MUST be explicitly modeled in
requirements, UI flows, and acceptance criteria. Role visibility, permissions, and
navigation differences MUST be testable and enforced in implementation.

Rationale: the product value depends on clear role-specific journeys and safeguards.

### VII. Prototype-to-Production Scalability
All prototype interfaces, models, and services MUST be designed for migration to real
APIs and persistent storage without major UI rewrites. Service contracts, identifier
strategy, and pagination/filtering semantics MUST anticipate production needs.

Rationale: prototype work must accelerate, not block, production readiness.

## Technology Standards

- Frontend stack MUST be React + TypeScript.
- Domain entities MUST include, at minimum: Skill, Employee, Certification,
    and ProficiencyLevel.
- Mock datasets MUST be valid JSON and consumed through typed service boundaries.
- State sharing MUST use Context API or Zustand per feature decision.
- Analytics UI MUST use Recharts or Chart.js.

## Delivery & Quality Gates

- Every specification MUST include role-based user scenarios and independent tests.
- Every implementation plan MUST include a Constitution Check with explicit pass/fail
    gates for architecture, state management, mock services, and visualization choices.
- Every task plan MUST include tasks for models, services, role-based UI, state
    management wiring, and analytics rendering.
- Linting, type-checking, and automated tests MUST pass before merge.

## Governance

This Constitution supersedes local feature conventions and planning assumptions.
Amendments require: (1) documented rationale, (2) semantic version update,
(3) synchronization of affected templates, and (4) an updated Sync Impact Report.

Versioning policy:
- MAJOR: incompatible governance or principle redefinition/removal.
- MINOR: new principle/section or materially expanded mandates.
- PATCH: wording clarifications and non-semantic refinements.

Compliance review expectations:
- Pull requests MUST reference applicable constitutional principles.
- Reviewers MUST block changes that violate any MUST requirement.
- Deviations require explicit justification in the plan Complexity Tracking table.

**Version**: 2.0.0 | **Ratified**: TODO(RATIFICATION_DATE) | **Last Amended**: 2026-03-13

<!-- Example: Version: 2.1.1 | Ratified: 2025-06-13 | Last Amended: 2025-07-16 -->
