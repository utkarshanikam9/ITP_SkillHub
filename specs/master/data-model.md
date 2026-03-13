# Phase 1 Data Model: Skill Matrix System

## Entity: ProficiencyLevel
- Fields:
  - id: string
  - code: "L1" | "L2" | "L3" | "L4" | "L5"
  - label: string
  - description: string
  - rank: number (1-5)
  - isActive: boolean
- Validation rules:
  - `rank` MUST be unique within active levels.
  - `description` MUST be non-empty and business-readable.
- Relationships:
  - Referenced by `Skill.defaultProficiencyScale` and `EmployeeSkillEntry.declaredLevel`.

## Entity: Skill
- Fields:
  - id: string
  - name: string
  - description: string
  - categoryId: string
  - subcategoryId: string
  - isActive: boolean
  - defaultProficiencyScale: string[] (ProficiencyLevel ids)
  - createdAt: string (ISO timestamp)
  - updatedAt: string (ISO timestamp)
- Validation rules:
  - `name` MUST be unique within active skills.
  - `categoryId` and `subcategoryId` MUST reference existing taxonomy records.
- Relationships:
  - One `Skill` can appear in many `EmployeeSkillEntry` records.
  - One `Skill` can be associated with many `Certification` records.

## Entity: Certification
- Fields:
  - id: string
  - employeeId: string
  - skillId: string
  - title: string
  - issuer: string
  - issueDate: string (ISO date)
  - expiryDate: string | null (ISO date)
  - documentUrl: string
  - verificationStatus: "pending" | "verified" | "rejected"
- Validation rules:
  - `issueDate` MUST be <= current date.
  - `expiryDate` when present MUST be >= `issueDate`.
  - `documentUrl` MUST be present for uploaded evidence.
- Relationships:
  - Belongs to one `Employee` and one `Skill`.

## Entity: Employee
- Fields:
  - id: string
  - fullName: string
  - email: string
  - department: string
  - role: "Employee" | "Manager" | "Admin" | "Leadership"
  - managerId: string | null
  - profileUpdatedAt: string (ISO timestamp)
  - skillEntries: EmployeeSkillEntry[]
- Validation rules:
  - `email` MUST be unique.
  - `managerId` SHOULD be null for top-level leadership/admin.
- Relationships:
  - One `Employee` has many `EmployeeSkillEntry` and `Certification` records.

## Entity: EmployeeSkillEntry
- Fields:
  - id: string
  - employeeId: string
  - skillId: string
  - declaredLevel: string (ProficiencyLevel id)
  - yearsOfExperience: number
  - projectContext: string | null
  - status: "self-declared" | "verified" | "needs-evidence" | "rejected"
  - validatedBy: string | null
  - validatedAt: string | null
  - createdAt: string
  - updatedAt: string
- Validation rules:
  - `yearsOfExperience` MUST be >= 0.
  - `validatedBy` and `validatedAt` MUST be set when status is `verified` or `rejected`.
- Relationships:
  - Belongs to one `Employee` and one `Skill`.
  - Links to zero-many `Certification` evidence items.

## Entity: SkillChangeHistoryEntry
- Fields:
  - id: string
  - employeeSkillEntryId: string
  - changedBy: string
  - changeType: "created" | "updated" | "validated" | "rejected" | "evidence-added"
  - previousValue: object
  - newValue: object
  - changedAt: string
- Validation rules:
  - History entries MUST be immutable.
- Relationships:
  - Many history entries per `EmployeeSkillEntry`.

## Entity: CapabilityReport
- Fields:
  - id: string
  - reportType: "skill-gap" | "team-capability" | "distribution" | "project-match"
  - generatedBy: string
  - generatedAt: string
  - filters: object
  - summary: object
  - chartSeries: object[]
- Validation rules:
  - `reportType` MUST be one of supported values.
  - `summary` MUST include decision-readable metrics and labels.
- Relationships:
  - Aggregates data from `Employee`, `EmployeeSkillEntry`, and `Skill`.

## State Transitions

### EmployeeSkillEntry.status
- `self-declared` -> `verified` (manager approves).
- `self-declared` -> `needs-evidence` (manager requests supporting proof).
- `needs-evidence` -> `self-declared` (employee resubmits with evidence).
- `self-declared` -> `rejected` (manager rejects claim).
- `verified` -> `self-declared` (employee edits proficiency/experience; requires re-validation).

### Certification.verificationStatus
- `pending` -> `verified` (validation passed).
- `pending` -> `rejected` (validation failed).
- `verified` -> `pending` (auto-reset on expiration and renewal upload).
