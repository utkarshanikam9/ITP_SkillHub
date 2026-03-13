---

description: "Task list template for feature implementation"
---

# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Tests**: The examples below include test tasks. Tests are expected for critical and
role-based user journeys unless explicitly deferred in the specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **React + TypeScript app**: `src/`, `public/`, `tests/` at repository root
- **Feature modules**: `src/features/<feature>/components|models|services|state`
- **Shared modules**: `src/components/`, `src/models/`, `src/services/`, `src/state/`
- **Mock data**: `public/mocks/` or `src/services/mocks/`
- Paths shown below assume React + TypeScript prototype structure

<!-- 
  ============================================================================
  IMPORTANT: The tasks below are SAMPLE TASKS for illustration purposes only.
  
  The /speckit.tasks command MUST replace these with actual tasks based on:
  - User stories from spec.md (with their priorities P1, P2, P3...)
  - Feature requirements from plan.md
  - Entities from data-model.md
  - Endpoints from contracts/
  
  Tasks MUST be organized by user story so each story can be:
  - Implemented independently
  - Tested independently
  - Delivered as an MVP increment
  
  DO NOT keep these sample tasks in the generated tasks.md file.
  ============================================================================
-->

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [ ] T001 Create project structure per implementation plan
- [ ] T002 Initialize [language] project with [framework] dependencies
- [ ] T003 [P] Configure linting and formatting tools

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

Examples of foundational tasks (adjust based on your project):

- [ ] T004 Define typed core entities (Skill, Employee, Certification, ProficiencyLevel)
- [ ] T005 [P] Establish mock API service layer and async/error simulation patterns
- [ ] T006 [P] Implement role model/permission guards for Employee, Manager, Admin, Leadership
- [ ] T007 Select and wire state strategy (Context API or Zustand) with typed stores
- [ ] T008 Create reusable chart wrappers using Recharts or Chart.js
- [ ] T009 Configure linting, type-checking, and test commands

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - [Title] (Priority: P1) 🎯 MVP

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Tests for User Story 1 (OPTIONAL - only if tests requested) ⚠️

> **NOTE: Write these tests FIRST, ensure they FAIL before implementation**

- [ ] T010 [P] [US1] Unit test for service contract in tests/unit/[feature].service.test.ts
- [ ] T011 [P] [US1] Integration test for role-based journey in tests/integration/[feature].flow.test.tsx

### Implementation for User Story 1

- [ ] T012 [P] [US1] Create or extend typed models in src/models/[entity].ts
- [ ] T013 [P] [US1] Implement mock service in src/services/[feature]Service.ts
- [ ] T014 [US1] Implement state wiring in src/state/[feature]Store.ts or feature context
- [ ] T015 [US1] Implement feature UI in src/features/[feature]/components/[View].tsx
- [ ] T016 [US1] Add role-aware visibility/interaction rules
- [ ] T017 [US1] Add chart rendering with reusable wrapper (if analytics involved)

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - [Title] (Priority: P2)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Tests for User Story 2 (OPTIONAL - only if tests requested) ⚠️

- [ ] T018 [P] [US2] Unit test for mock service behavior in tests/unit/[feature].service.test.ts
- [ ] T019 [P] [US2] Integration test for role journey in tests/integration/[feature].flow.test.tsx

### Implementation for User Story 2

- [ ] T020 [P] [US2] Extend typed model(s) in src/models/[entity].ts
- [ ] T021 [US2] Implement feature service logic in src/services/[service].ts
- [ ] T022 [US2] Implement role-based UI in src/features/[feature]/components/[View].tsx
- [ ] T023 [US2] Integrate state and shared components without cross-story coupling

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - [Title] (Priority: P3)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Tests for User Story 3 (OPTIONAL - only if tests requested) ⚠️

- [ ] T024 [P] [US3] Unit test for chart adapter/view model in tests/unit/[feature].chart.test.ts
- [ ] T025 [P] [US3] Integration test for analytics flow in tests/integration/[feature].analytics.test.tsx

### Implementation for User Story 3

- [ ] T026 [P] [US3] Extend or create model(s) in src/models/[entity].ts
- [ ] T027 [US3] Implement or update service in src/services/[service].ts
- [ ] T028 [US3] Implement analytics UI in src/features/[feature]/components/[View].tsx

**Checkpoint**: All user stories should now be independently functional

---

[Add more user story phases as needed, following the same pattern]

---

## Phase N: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [ ] TXXX [P] Documentation updates in specs/ and feature notes
- [ ] TXXX Code cleanup and refactoring for component/service boundaries
- [ ] TXXX Validate API migration readiness for mock service contracts
- [ ] TXXX [P] Add/expand unit and integration tests for role-based UX
- [ ] TXXX Accessibility and responsive behavior validation
- [ ] TXXX Validate type-check, lint, and test suite execution

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - May integrate with US1 but should be independently testable
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - May integrate with US1/US2 but should be independently testable

### Within Each User Story

- Tests (if included) MUST be written and FAIL before implementation
- Models before services
- Services before endpoints
- Core implementation before integration
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- All tests for a user story marked [P] can run in parallel
- Models within a story marked [P] can run in parallel
- Different user stories can be worked on in parallel by different team members

---

## Parallel Example: User Story 1

```bash
# Launch all tests for User Story 1 together (if tests requested):
Task: "Unit test for service contract in tests/unit/[feature].service.test.ts"
Task: "Integration test for role-based journey in tests/integration/[feature].flow.test.tsx"

# Launch all models for User Story 1 together:
Task: "Create or extend typed model in src/models/[entity].ts"
Task: "Implement mock service in src/services/[feature]Service.ts"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Test User Story 1 independently
5. Deploy/demo if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Verify tests fail before implementing
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence
