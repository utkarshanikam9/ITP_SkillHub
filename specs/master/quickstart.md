# Quickstart: Skill Matrix System Prototype (React + TypeScript)

## 1. Create the React + TypeScript app

```powershell
npm create vite@latest skill-matrix-prototype -- --template react-ts
cd skill-matrix-prototype
```

## 2. Install dependencies

```powershell
npm install zustand recharts react-router-dom
npm install -D vitest @testing-library/react @testing-library/jest-dom @testing-library/user-event jsdom
```

## 3. Create project directories

```text
src/
├── components/
├── pages/
├── services/
├── models/
├── mock-data/
└── state/
```

## 4. Add core domain models
- Create `src/models/Skill.ts`, `src/models/Employee.ts`, `src/models/Certification.ts`, and `src/models/ProficiencyLevel.ts` using the data model in `specs/master/data-model.md`.

## 5. Add mock JSON data
- Add realistic JSON datasets under `src/mock-data/`:
  - `skills.json`
  - `employees.json`
  - `certifications.json`
  - `analytics.json`

## 6. Build service layer (mock API simulation)
- Implement:
  - `src/services/skillService.ts`
  - `src/services/employeeService.ts`
  - `src/services/certificationService.ts`
  - `src/services/analyticsService.ts`
- Service requirements:
  - Return typed responses.
  - Simulate async latency (`setTimeout`/Promise delay).
  - Provide deterministic error modes for testing.
  - Keep JSON imports only inside services.

## 7. Configure state with Zustand
- Implement stores in `src/state/`:
  - `roleStore.ts` for role/permission context.
  - `filtersStore.ts` for search/report filters.
  - `appStore.ts` for shared async state and view flags.

## 8. Implement pages and modular components
- Pages:
  - Employee profile management
  - Manager validation queue
  - Admin taxonomy setup
  - Search and filtering
  - Leadership analytics dashboard
- Components:
  - Shared form controls and validation feedback
  - Loading/empty/error states for all data views
  - Reusable chart wrappers in `components/dashboard/`

## 9. Run the prototype

```powershell
npm run dev
```

## 10. Validate quality gates

```powershell
npm run test
npm run build
```

## 11. Migration to real APIs
- Keep UI and stores unchanged.
- Replace mock service implementations with HTTP implementations.
- Maintain response contracts from `specs/master/contracts/skill-matrix-api.yaml`.
