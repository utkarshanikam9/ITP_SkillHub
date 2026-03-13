<!--
Sync Impact Report:
- Version change: 2.0.0 -> 2.1.0
- Modified principles:
    - V. Standardized Skill Analytics Visualization -> V. Decision-Ready Skill Analytics Visualization
    - VI. Role-Based User Experience Integrity (expanded)
    - VII. Prototype-to-Production Scalability (expanded)
    - Added VIII. Consistent UX Interaction Patterns
    - Added IX. Explicit System Feedback and Screen-State Governance
    - Added X. Business Outcome Traceability
- Added sections: Experience & Business Governance
- Removed sections: None
- Templates requiring updates:
    - .specify/templates/plan-template.md (✅ updated)
    - .specify/templates/spec-template.md (✅ updated)
    - .specify/templates/tasks-template.md (✅ updated)
    - .specify/templates/commands/*.md (✅ not present; no action required)
    - .github/agents/*.md (✅ checked; no outdated agent-specific naming found)
    - .github/prompts/*.md (✅ checked; no outdated agent-specific naming found)
- Follow-up TODOs:
    - TODO(RATIFICATION_DATE): Original ratification date was not available in repo history.
-->

# Skill Matrix System Constitution

## Normative Language
- **MUST**: non-negotiable requirement
- **SHOULD**: strongly recommended; exceptions require justification in the PR/complexity tracker

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

### V. Decision-Ready Skill Analytics Visualization
Skill analytics views MUST use Recharts or Chart.js through reusable chart adapters
or wrapper components. Visualizations MUST consume typed view models rather than raw
service payloads. Chart behavior, axis semantics, labels, legends, and threshold
indicators MUST be documented in specs for decision clarity.

Rationale: analytics dashboards are only valuable when users can interpret trends,
risks, and staffing implications without ambiguity.

### VI. Role-Based User Experience Integrity
Employee, Manager, Admin, and Leadership experiences MUST be explicitly modeled in
requirements, UI flows, and acceptance criteria. Role visibility, permissions, and
navigation differences MUST be testable and enforced in implementation. Each role
MUST have at least one documented end-to-end journey from entry point to business
outcome completion.

Rationale: the product value depends on clear role-specific journeys and safeguards.

### VII. Prototype-to-Production Scalability
All prototype interfaces, models, and services MUST be designed for migration to real
APIs and persistent storage without major UI rewrites. Service contracts, identifier
strategy, pagination/filtering semantics, and validation rules MUST anticipate
production needs.

Rationale: prototype work must accelerate, not block, production readiness.

### VIII. Consistent UX Interaction Patterns
Forms, navigation, validation behavior, and dashboard interactions MUST follow shared
interaction patterns and reusable UI conventions. Equivalent actions across modules
MUST produce equivalent interaction behavior unless a documented exception exists.

Rationale: interaction consistency lowers cognitive load and increases user trust.

### IX. Explicit System Feedback and Screen-State Governance
Every user action with side effects MUST expose clear system feedback for success,
failure, and pending validation states. All data-driven screens MUST define and
implement loading, empty, and error states with actionable guidance where relevant.

Rationale: transparent state communication prevents confusion and reduces workflow
failure in role-critical operations.

### X. Business Outcome Traceability
Features, user stories, and dashboards MUST map to at least one measurable business
outcome, including workforce visibility, project staffing effectiveness, or skill
development progress. Specs and plans MUST describe the linkage between UX behavior
and intended business decision support.

Rationale: BA alignment ensures delivery effort translates into organizational value.

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
    gates for architecture, state management, mock services, visualization choices,
    UX consistency, and screen-state handling.
- Every task plan MUST include tasks for models, services, role-based UI, state
    management wiring, analytics rendering, reusable interaction patterns,
    and loading/empty/error state handling.
- Linting, type-checking, and automated tests MUST pass before merge.

## Experience & Business Governance

- Every role (Employee, Manager, Admin, Leadership) MUST have a documented end-to-end
    journey with trigger, decision points, and completion outcome.
- Shared UX patterns for forms, navigation, validation, and dashboard controls MUST be
    defined once and referenced by all affected features.
- All data-driven screens MUST include explicit acceptance criteria for loading,
    empty, and error states.
- Dashboard specifications MUST include readability checks: label clarity, chart
    interpretability, and decision-focused summaries.
- Each feature specification MUST map to one or more business outcomes:
    workforce visibility, project staffing, or skill development.

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
- Reviews MUST verify role journey completeness and screen-state behavior coverage.
- Reviews MUST verify that dashboard and feature behavior preserve business-outcome
    traceability.

**Version**: 2.1.0 | **Ratified**: TODO(RATIFICATION_DATE) | **Last Amended**: 2026-03-14

<!-- Example: Version: 2.1.1 | Ratified: 2025-06-13 | Last Amended: 2025-07-16 -->
