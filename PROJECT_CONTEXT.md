# Chain-Of-Supply — Project Context

## 1. Project Overview

Chain-Of-Supply is a real-world Production Lifecycle & Material
Traceability System being developed around a printing/manufacturing
business.

The system is intended to track production from raw-material
receiving through manufacturing, quality control, and dispatch.

This project is also being used as a practical software engineering
learning project.

---

## 2. Primary Objectives

### Business Objective

Improve visibility and traceability across the production lifecycle.

Potential areas include:

- Raw-material tracking
- Material/reel traceability
- Customer orders
- Production/job orders
- Production stages
- Batch tracking
- Material consumption
- Quantity tracking
- Wastage/rejection
- Rework
- Quality control
- Dispatch
- Production status visibility
- Audit history

### Learning Objective

Use the project to learn and practice:

- Software engineering
- System design
- Domain modeling
- Database design
- Backend/API development
- Frontend development
- Authentication and authorization
- Git/GitHub
- Testing
- Security
- Deployment
- Monitoring
- Production engineering

---

## 3. Current Project Status

Current phase:

**Phase 0 — Factory Discovery & Domain Modeling**

The system is not yet fully specified.

The current project description contains initial ideas and hypotheses.
Important business rules must be validated against the actual factory
before they are treated as confirmed requirements.

---

## 4. Initial Workflow Hypothesis

A possible production lifecycle is:

Raw Material
→ Corrugation
→ Printing
→ Lamination
→ Cutting / Die-cutting
→ Pasting
→ Quality Control
→ Dispatch

This is only an initial hypothesis.

Actual factory workflows may:

- Skip stages
- Repeat stages
- Change stage order
- Split into batches
- Require rework
- Produce rejection/wastage
- Use multiple material lots
- Process one material lot across multiple jobs

These cases must be investigated before the workflow is finalized.

---

## 5. Initial Traceability Hypothesis

The initial idea is to assign a unique identifier and potentially a QR
code to raw-material reels.

Potential information may include:

- Reel ID
- Supplier / mill
- Material specifications
- Weight
- Arrival date
- Other relevant material information

The exact information captured and the relationship between reels,
production jobs, batches, and consumption are not yet finalized.

---

## 6. Users and Roles

Initial hypothesis:

- Owner
- Manager
- Production staff / operators

A manager may be able to operate most of the system, while operators
may require an extremely simple interface.

The final workflow will be determined after observing actual factory
operations.

---

## 7. Core Design Principle

The system should optimize for:

**Minimum friction → Reliability → Traceability → Scalability when necessary**

Avoid introducing complexity merely because a technology or
architecture makes it possible.

The system should fit the real factory rather than forcing the factory
to behave like the software.

---

## 8. Project Constraints

### Cost

The project should require no additional spending wherever reasonably
possible.

Prefer:

- Open-source tools
- Free software
- Free tiers
- Local development
- Existing hardware

Any paid dependency should be evaluated against a genuinely free
alternative first.

### Development

AI may be used for repetitive boilerplate and implementation
assistance.

However, important business logic, architecture, database design,
security decisions, and critical code must be understood by the
developer.

### Maintainability

The project should remain understandable to:

- The developer
- Future maintainers
- Another software engineer
- Another AI working on the repository

---

## 9. Documentation Principle

Important project knowledge should be stored in the repository.

This includes:

- Requirements
- Business rules
- Architecture
- Database design
- API contracts
- Decisions
- Testing strategy
- Setup instructions
- Environment variables
- Known issues
- TODOs
- Change history

Documentation should be concise enough to remain maintainable while
being detailed enough to reconstruct project context after a long gap.

---

## 10. Assumption Policy

An assumption must not silently become a business rule.

Use these classifications:

### Confirmed

Verified through factory observation, existing records, or confirmation
from relevant factory staff.

### Assumption

Currently believed to be true but not yet verified.

### Open Question

Information that is currently unknown.

### Decision

A deliberate project/design choice made after evaluating alternatives.

---

## 11. Engineering Principles

- Prefer simple solutions over unnecessary complexity.
- Preserve data integrity.
- Design for failure.
- Validate important assumptions.
- Keep business logic explicit.
- Avoid hidden dependencies.
- Do not commit secrets or API keys.
- Use meaningful Git commits.
- Test important workflows and failure cases.
- Treat local functionality and production readiness as different goals.

---

## 12. Current Known Risks

- Actual factory workflow has not yet been fully documented.
- Material traceability relationships are not yet confirmed.
- Production stage sequencing is not yet confirmed.
- Actual quantity and wastage measurement practices are unknown.
- User roles and permissions are not finalized.
- Network reliability and hardware constraints are unknown.
- The appropriate level of QR usage has not yet been determined.

---

## 13. Current Next Steps

1. Document the real factory workflow.
2. Identify core domain entities.
3. Identify relationships between entities.
4. Identify business rules.
5. Define initial requirements.
6. Create architecture v0.1.
7. Create database design v0.1.
8. Define a small MVP.
9. Implement incrementally.
10. Validate assumptions against the real factory.