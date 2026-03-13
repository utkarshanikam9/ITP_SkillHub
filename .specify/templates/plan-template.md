# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/plan-template.md` for the execution workflow.

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Language/Version**: [TypeScript (React) or NEEDS CLARIFICATION]  
**Primary Dependencies**: [React, state library (Context API or Zustand), chart library (Recharts or Chart.js)]  
**Storage**: [Prototype: local JSON mock datasets; Production path: API + database integration]  
**Testing**: [e.g., Vitest, React Testing Library, Playwright/Cypress or NEEDS CLARIFICATION]  
**Target Platform**: [Modern web browsers, responsive desktop/mobile]
**Project Type**: [Web application (frontend prototype)]  
**Performance Goals**: [e.g., analytics views render in <2s with mock data at target scale]  
**Constraints**: [Role-based UX parity, strict UI-model-service separation, typed contracts]  
**Scale/Scope**: [e.g., org-level skill matrix across Employee/Manager/Admin/Leadership roles]

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- [ ] Modular architecture defined (feature folders + reusable components)
- [ ] UI, domain models, and services are separated by file/module boundaries
- [ ] Mock data access only through API-simulated service layer
- [ ] State management approach selected (Context API or Zustand) and justified
- [ ] Analytics approach selected (Recharts or Chart.js) with reusable wrappers
- [ ] Role-based UX coverage defined for Employee, Manager, Admin, Leadership
- [ ] End-to-end journey documented for each role with decision points and outcomes
- [ ] Shared interaction patterns defined for forms, navigation, validation, dashboards
- [ ] Success, failure, and pending validation feedback states are explicitly designed
- [ ] Loading, empty, and error states are defined for every data-driven screen
- [ ] Dashboard readability standards defined (labels, legends, thresholds, summaries)
- [ ] Business outcome mapping defined (workforce visibility, staffing, skill development)
- [ ] Migration path to real APIs/databases documented

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
src/
├── app/
├── components/
│   ├── common/
│   └── charts/
├── features/
│   └── [feature-name]/
│       ├── components/
│       ├── hooks/
│       ├── models/
│       ├── services/
│       └── state/
├── models/
├── services/
├── state/
└── types/

public/
└── mocks/

tests/
├── unit/
├── integration/
└── e2e/
```

**Structure Decision**: [Document the selected structure and reference the real
directories captured above]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |
