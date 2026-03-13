# Phase 0 Research: Skill Matrix System

## Decision 1: State Management Strategy
- Decision: Use Zustand for shared application state.
- Rationale: Zustand provides typed, low-boilerplate stores for role context, filter state, and async mock-service integration. It reduces unnecessary re-renders compared to broad Context API providers and keeps migration to production straightforward.
- Alternatives considered: React Context API (rejected due to provider nesting and coarse-grained updates), Redux Toolkit (rejected as too heavy for prototype scope).

## Decision 2: Analytics Visualization Library
- Decision: Use Recharts with reusable wrapper components in `src/components/dashboard/`.
- Rationale: Recharts is React-native, TypeScript-friendly, and fast to iterate for dashboard widgets (skill distribution, gaps, and team capability charts). SVG semantics improve readability and maintainable customization.
- Alternatives considered: Chart.js via wrapper (rejected due to less React-idiomatic composition and lower accessibility ergonomics for this prototype).

## Decision 3: Mock API Simulation Pattern
- Decision: Implement async service modules that return typed response unions and inject deterministic delays/errors.
- Rationale: This enforces constitutional layering (UI -> state -> services -> mock data), exercises loading/empty/error UX states, and creates a clean adapter seam for real HTTP APIs later.
- Alternatives considered: Direct JSON imports in components (rejected by constitution), static synchronous helpers (rejected because no realistic async/error behavior).

## Decision 4: Testing Strategy
- Decision: Use Vitest + React Testing Library for unit/integration tests, with optional Playwright smoke tests for critical role-based journeys.
- Rationale: Vitest integrates naturally with Vite + TypeScript and supports rapid feedback for component/service/state behavior; RTL validates UX behavior and state transitions.
- Alternatives considered: Jest (rejected due to additional setup overhead in Vite-first prototype), no e2e checks (rejected because role workflows are a key risk area).

## Decision 5: Domain Modeling & Contracts
- Decision: Define domain models for `Skill`, `Employee`, `Certification`, and `ProficiencyLevel` in `src/models/`, with contract schemas documented in `specs/master/contracts/`.
- Rationale: Typed models preserve separation of concerns and allow service responses to be validated/mapped before rendering. Contracts improve migration readiness to backend APIs.
- Alternatives considered: Loose per-component types (rejected due to duplication and brittle evolution).

## Decision 6: Role-Based Journey Coverage
- Decision: Implement dedicated pages and route guards for Employee, Manager, Admin, and Leadership journeys with shared interaction primitives.
- Rationale: Explicit role journeys satisfy constitutional governance and make permissions, decision points, and business outcomes testable.
- Alternatives considered: Single blended dashboard UI (rejected due to unclear permissions and poor traceability of role outcomes).

## Decision 7: Performance & Scale Envelope
- Decision: Design for mock dataset scale of ~1,000 employees and ~5,000 skill profile entries with client-side filtering/index maps.
- Rationale: This supports prototype realism while keeping implementation simple and responsive under target SC-003 (<2s filtered search).
- Alternatives considered: Tiny toy datasets (rejected because they underrepresent analytics complexity), full server-side querying (deferred to production phase).
