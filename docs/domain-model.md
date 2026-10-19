# Domain Model

## Status

Version: 0.1
Status: Draft

This document contains an initial domain model based on the current
project hypothesis.

It is not a finalized representation of the factory workflow.

---

## 1. Purpose

Define the important business entities involved in the production
lifecycle and material traceability system.

---

## 2. Initial Entities

### Customer

Represents a customer for whom production work is performed.

Current assumptions:
- A customer can have multiple production orders.
- Customer information should be reusable across orders.

Validation required:
- What customer information is actually maintained?
- Can one order have multiple customers?
- How are customers currently identified?

---

### Production Order

Represents a customer-related production requirement.

Potential information:
- Order identifier
- Customer
- Product specification
- Required quantity
- Order date
- Due date
- Status

Validation required:
- What exactly constitutes an order?
- Is a production order created from a customer purchase order?
- Can an order be modified after production starts?
- Can one customer order create multiple production jobs?

---

### Production Batch

Represents a portion of production associated with an order.

Initial hypothesis:
A production order may be completed in one or multiple batches.

Validation required:
- Are batches actually used operationally?
- Can batches be processed independently?
- Can batches be reworked or rejected independently?

---

### Production Operation

Represents a manufacturing operation performed on a production batch.

Possible operations:
- Corrugation
- Printing
- Lamination
- Cutting / Die-cutting
- Pasting
- Quality Control

Important:
The operation sequence is currently only a hypothesis.

---

### Material Lot / Reel

Represents an identifiable quantity of raw material.

Initial hypothesis:
Kraft paper may arrive as reels that can be individually identified.

Potential information:
- Reel identifier
- Supplier / mill
- Material specification
- Weight
- Arrival date

Validation required:
- Supplier-provided identifiers
- Internal identifiers
- Partial consumption
- Remaining quantity
- Multiple jobs consuming one reel
- Multiple reels contributing to one job

---

### Material Consumption

Represents the use of material by production.

This is currently treated as a separate concept rather than assuming
that one reel belongs permanently to one order.

Potential information:
- Material lot / reel
- Production batch
- Operation
- Quantity consumed
- Timestamp

Validation required:
- How consumption is measured
- Whether actual or estimated quantities are recorded
- How leftovers are handled
- How wastage is distinguished from usable remainder

---

### Quality Check

Represents a quality inspection performed during or after production.

Potential information:
- Production batch
- Inspection stage
- Result
- Accepted quantity
- Rejected quantity
- Notes
- Timestamp
- Inspector

Validation required:
- Existing QC process
- Inspection criteria
- Who performs QC
- How rejection is recorded
- How rework is handled

---

### Dispatch

Represents the shipment of completed production to a customer.

Potential information:
- Production order
- Quantity dispatched
- Dispatch date
- Destination
- Transport information

Validation required:
- Dispatch documentation
- Partial dispatch
- Multiple dispatches for one order
- Relationship between finished quantity and dispatched quantity

---

### User

Represents a person who interacts with the software.

Initial roles may include:
- Owner
- Manager
- Operator

Roles and permissions are not finalized.

---

### Machine

Potentially represents a machine used during production.

Validation required:
- Whether machine-level tracking provides enough value
- Which machines need to be tracked
- Whether machine downtime should be recorded

---

## 3. Initial Relationship Hypothesis

Possible relationships:

Customer
→ Production Order

Production Order
→ Production Batch

Production Batch
→ Production Operation

Material Lot / Reel
→ Material Consumption
→ Production Batch / Operation

Production Batch
→ Quality Check

Production Order
→ Dispatch

Machine
→ Production Operation

User
→ Production Operation / Quality Check / Audit Event

These relationships are preliminary and require validation.

---

## 4. Important Unknowns

- Exact definition of a customer order
- Difference between order, job, and production batch
- Whether production is batch-based
- Whether one material reel can serve multiple jobs
- Whether one job can consume multiple reels
- How material consumption is measured
- How wastage is measured
- How rework is represented
- Whether operations can repeat
- Whether operations can occur in different sequences
- How machine usage is recorded
- How QC is performed
- How partial dispatch works

---

## 5. Design Principles

- Do not encode unverified factory assumptions as permanent business
  rules.
- Prefer flexible relationships where the real workflow is uncertain.
- Preserve traceability between material, production, and finished output.
- Keep the initial model simple.
- Refine the model when factory evidence becomes available.
---

## 6. Model Challenges

### Challenge 1 — One Material Lot Across Multiple Jobs

The model should allow one material lot/reel to contribute material to
multiple production jobs.

Current model:
Material Lot → Material Consumption → Production Batch

Status: Supported conceptually.

---

### Challenge 2 — Multiple Material Lots for One Production Batch

The model should allow a production batch to consume material from
multiple lots/reels.

Status: Supported conceptually.

---

### Challenge 3 — Split Production

One production order may potentially be divided into multiple
production batches.

Status: Supported conceptually, but batch usage must be validated with
the factory.

---

### Challenge 4 — Rework

A production operation may potentially fail quality checks and require
rework.

Current model does not yet define a finalized representation for
rework.

Status: Open design question.

---

### Challenge 5 — Variable Operation Sequence

Different products may potentially require different production
operations or operation sequences.

A fixed global production sequence should therefore not be assumed.

Status: Open design question requiring factory validation.

---

### Challenge 6 — Partial Dispatch

A production order may potentially be dispatched in multiple shipments.

Status: Open design question requiring factory validation.