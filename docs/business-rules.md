# Business Rules

**Status:** Version 0.1 — Draft
**Purpose:** Define the operational and data-integrity rules that the system may need to enforce.

> Important: These are proposed rules based on the current domain model.
> They are not considered final until validated against actual factory operations.

---

## 1. Production Order Rules

### BR-001 — Production Order Identification
Every production order should have a unique identifier.

**Status:** Proposed

### BR-002 — Order Quantity
A production order should have a defined target quantity.

**Status:** Proposed

### BR-003 — Order Modification
Changes to important production-order information after production has started should be controlled and auditable.

**Status:** Proposed

---

## 2. Production Batch Rules

### BR-004 — Batch Identification
Every production batch should have a unique identifier.

**Status:** Proposed

### BR-005 — Order-to-Batch Relationship
A production order may potentially be divided into multiple production batches.

**Status:** Open — Requires factory validation

### BR-006 — Batch Quantity
A production batch should record its intended and actual production quantities where applicable.

**Status:** Proposed

---

## 3. Material Lot / Reel Rules

### BR-007 — Material Lot Identification
Every material lot or reel should have a unique identifier.

**Status:** Proposed

### BR-008 — Material Availability
Material consumption should not normally exceed the available recorded quantity of the material lot.

**Status:** Proposed

### BR-009 — One Lot, Multiple Jobs
A material lot should potentially be usable across multiple production jobs.

**Status:** Proposed

### BR-010 — Multiple Lots, One Job
A production batch should potentially be able to consume material from multiple material lots.

**Status:** Proposed

---

## 4. Material Consumption Rules

### BR-011 — Consumption Record
Material consumed during production should be recorded against the relevant production batch and/or operation.

**Status:** Proposed

### BR-012 — Consumption Quantity
Every material-consumption record should include a measurable quantity where applicable.

**Status:** Proposed

### BR-013 — Consumption Traceability
The system should be able to determine which material lot contributed to a production batch.

**Status:** Proposed

### BR-014 — Consumption Correction
Incorrect consumption records should not simply be silently overwritten.

Corrections should preserve an appropriate audit history.

**Status:** Proposed**

---

## 5. Production Operation Rules

### BR-015 — Operation Identification
Each production operation should be associated with a production batch.

**Status:** Proposed

### BR-016 — Operation Status
An operation should have a defined lifecycle/status.

Possible examples:

- Pending
- In Progress
- Completed
- Paused
- Cancelled
- Rework Required

**Status:** Proposed — Exact statuses require validation

### BR-017 — Operation Sequence
The system should not assume that every production order follows the same fixed sequence of operations.

Different products may require different operations.

**Status:** Open — Requires factory validation

### BR-018 — Operation Completion
An operation should record when it started and when it was completed, where applicable.

**Status:** Proposed

### BR-019 — Production Quantity
Where applicable, an operation should record quantities produced, rejected, wasted, or requiring rework.

**Status:** Proposed**

---

## 6. Rework Rules

### BR-020 — Rework
A production operation may require rework after a quality issue or production problem.

**Status:** Open — Requires factory validation

### BR-021 — Rework Traceability
If rework is implemented, the system should preserve the relationship between the original operation and the rework activity.

**Status:** Proposed**

---

## 7. Quality Control Rules

### BR-022 — Quality Check
A production batch may require quality checks at defined points in the production process.

**Status:** Proposed

### BR-023 — Quality Result
A quality check should record its result and relevant information.

**Status:** Proposed

### BR-024 — Failed Quality Check
A failed quality check should not automatically mark the entire production order as failed.

The appropriate next action may depend on the factory workflow.

**Status:** Proposed — Requires validation

---

## 8. Dispatch Rules

### BR-025 — Dispatch Identification
Every dispatch should have a unique identifier.

**Status:** Proposed

### BR-026 — Partial Dispatch
A production order may potentially be dispatched in multiple shipments.

**Status:** Open — Requires factory validation

### BR-027 — Dispatch Quantity
A dispatch should record the quantity being dispatched.

**Status:** Proposed

### BR-028 — Dispatch Reconciliation
The system should be able to compare ordered, produced, rejected/wasted, and dispatched quantities where those measurements are available.

**Status:** Proposed**

---

## 9. QR / Scanning Rules

### BR-029 — Unique QR Mapping
If QR codes are used, each QR code should resolve to a unique system entity.

**Status:** Proposed

### BR-030 — Invalid QR
Scanning an unknown or invalid QR code should not create an unintended production or consumption record.

**Status:** Proposed

### BR-031 — Duplicate Scan
Repeated scanning of the same QR code should not unintentionally create duplicate transactions.

The exact behaviour depends on the operation being performed.

**Status:** Proposed**

### BR-032 — Incorrect Scan
The system should provide an appropriate response when a user scans an entity that is not valid for the current operation.

**Status:** Proposed**

---

## 10. Audit Rules

### BR-033 — Important Changes
Important production, material, quality, and dispatch changes should be traceable.

**Status:** Proposed

### BR-034 — User Attribution
Where appropriate, important actions should record which user performed them.

**Status:** Proposed

### BR-035 — Completed Records
Completed production records should not be silently deleted or modified in a way that destroys historical traceability.

**Status:** Proposed**

---

## 11. Data Integrity Rules

### BR-036 — Referential Integrity
Records should not reference production orders, batches, materials, users, or other entities that do not exist.

**Status:** Proposed

### BR-037 — Historical Traceability
Deleting a record should not unnecessarily destroy historical production traceability.

**Status:** Proposed

### BR-038 — Quantity Reconciliation
The system should identify significant discrepancies between expected and actual quantities where sufficient data exists.

**Status:** Proposed**

---

# Open Business Rule Questions

The following questions require validation with the factory:

1. What exactly is considered an "order"?
2. What is the practical difference between an order, job, batch, and production run?
3. Can one order be produced in multiple batches?
4. Can one material reel be used for multiple orders?
5. Can one order consume multiple reels?
6. How is material consumption actually measured?
7. Is consumption recorded by weight, length, sheets, pieces, or another measurement?
8. How is wastage recorded?
9. How is rejected production recorded?
10. How is rework handled physically?
11. Can an operation be repeated?
12. Can production operations happen in different sequences?
13. Which operations require machine information?
14. Which operations require operator information?
15. At what points are quality checks performed?
16. What happens when QC fails?
17. Can an order be partially dispatched?
18. What happens when production is stopped midway?
19. What happens when a machine breaks down?
20. What happens if the network is unavailable?
21. Who is allowed to correct an incorrect production/material record?
22. Which actions require manager approval?
23. What should happen when the same QR code is scanned twice?
24. Which entities actually need QR codes?
25. What information must be visible to the owner in near real time?