# Requirements

## Status

Version: 0.1
Status: Draft

Requirements are based on the current project hypothesis and have not
yet been fully validated against factory operations.

---

## 1. Functional Requirements

### 1.1 Customer Management

The system should potentially allow authorized users to:

- Create customers
- View customers
- Update customer information
- Search customers

Validation required:
- Required customer fields
- Whether customer deletion is necessary
- Existing customer records

---

### 1.2 Production Orders

The system should potentially allow authorized users to:

- Create production orders
- Associate an order with a customer
- Record product specifications
- Record required quantity
- Set expected delivery information
- Track order status
- View production progress

Validation required:
- Exact order fields
- Order lifecycle
- Order modification rules

---

### 1.3 Production Batches

The system should potentially allow:

- Creating batches for a production order
- Recording batch quantity
- Tracking batch progress
- Recording batch completion
- Recording rejection/rework where applicable

Validation required:
- Whether batches are used operationally
- Batch creation rules
- Quantity rules

---

### 1.4 Material Management

The system should potentially allow:

- Registering incoming material lots/reels
- Assigning internal identifiers
- Recording material information
- Recording received quantity/weight
- Tracking material status
- Tracking remaining quantity

Validation required:
- Actual receiving process
- Material identifiers
- Measurement process

---

### 1.5 Material Consumption

The system should potentially allow:

- Recording material consumed by production
- Linking consumption to a production batch
- Recording the operation where consumption occurred
- Tracking remaining material

Validation required:
- Measurement accuracy
- Units
- Partial consumption
- Correction rules

---

### 1.6 Production Operations

The system should potentially allow:

- Defining operations for a production job
- Starting an operation
- Pausing an operation
- Completing an operation
- Recording quantities
- Recording wastage/rejection
- Recording operator/machine information
- Recording timestamps

Validation required:
- Actual stage lifecycle
- Required information per stage

---

### 1.7 Quality Control

The system should potentially allow:

- Recording inspections
- Recording accepted quantity
- Recording rejected quantity
- Recording defects
- Recording rework requirements
- Recording inspection user and timestamp

Validation required:
- Existing QC process
- Inspection criteria
- Rework procedure

---

### 1.8 Dispatch

The system should potentially allow:

- Recording completed quantity
- Creating dispatch records
- Recording dispatch date
- Recording destination
- Supporting partial dispatch

Validation required:
- Actual dispatch documentation
- Partial shipment process

---

### 1.9 Dashboard

The system should potentially provide:

- Active production jobs
- Current production stage
- Completed stages
- Pending stages
- Production quantities
- Rejection/wastage
- Recent updates

The exact dashboard requirements will depend on what the owner and
manager actually need to see.

---

## 2. Non-Functional Requirements

Initial hypotheses:

### Usability

The system should require minimal interaction from production staff.

### Reliability

Important production records should not be silently lost.

### Security

Users should only be able to perform actions appropriate to their
roles.

### Auditability

Important changes should be traceable to a user and timestamp.

### Performance

Normal production workflows should respond quickly enough for
practical factory usage.

### Maintainability

The system should use understandable architecture and code.

### Cost

The initial system should avoid paid services wherever reasonably
possible.

---

## 3. Traceability Requirements

The system should potentially be able to answer questions such as:

- Which material lots contributed to a production batch?
- Which production batches consumed a particular material lot?
- What operations were performed on a batch?
- What quantities were produced?
- What was rejected or reworked?
- When did each important event occur?
- Who performed or recorded the event?

These are target capabilities, not yet finalized requirements.

---

## 4. Open Requirements Questions

- What exact information is required to create a production order?
- What defines a production batch?
- What constitutes operation completion?
- How are quantities measured?
- How is wastage calculated?
- How is rework recorded?
- How are cancelled jobs handled?
- How are changed orders handled?
- What happens when a machine goes offline?
- What happens when the network is unavailable?
- Who can modify historical records?
- What must appear on the owner dashboard?
- What must appear on the manager dashboard?