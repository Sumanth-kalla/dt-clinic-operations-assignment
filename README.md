# DT Business Analyst Assignment

This repository contains my solution to the DT Role Test Drive Assignment.
The focus is on designing simple, practical systems for small clinics
to reduce operational chaos, inventory leakage, and doctor overload.


## Task 1: Clinic Inventory Statistical Audit

### 1. Problem Context
Small clinics rely on manual entry of medicine sales during busy OPD hours. Due to rush, fatigue, and multiple staff handling inventory, errors such as missed entries and wrong quantities are common. These small daily mistakes lead to stock mismatches and gradual revenue leakage. Performing full inventory reconciliation every day is not practical for doctors or clinic staff.

---

### 2. Where Inventory Errors Are Most Likely
Inventory errors most commonly occur at the following points:
- **Busy OPD hours** – staff prioritize patient flow over accurate entry.
- **Fast-moving medicines** – high sales volume increases chances of quantity errors.
- **Multiple staff handling the same medicine** – lack of clear ownership.
- **End-of-day stock updates** – fatigue leads to estimation instead of counting.

---

### 3. Daily Micro-Audit Design
Instead of full reconciliation, the clinic performs small daily statistical checks that take no more than 5–10 minutes.

**Daily Audit Steps:**
1. Randomly select 5 medicines each day.
2. For each medicine, calculate expected closing stock using:
3. Compare expected closing stock with actual physical stock.
4. Mark any mismatch as “Needs Review” instead of treating it as an error.
5. Record the staff involved in sale and entry for pattern tracking.

In addition, fast-moving medicines are checked daily as they pose higher risk of revenue leakage.

---

### 4. Sample Audit Table

| Medicine Name | Opening Stock | Purchased | Sold | Expected Closing | Actual Closing | Status |
|--------------|---------------|-----------|------|------------------|----------------|--------|
| Paracetamol  | 50            | 20        | 30   | 40               | 38             | Review |

This table helps quickly identify possible discrepancies without performing full inventory checks.

---

### 5. Error Handling and Discipline Improvement
The purpose of these checks is not punishment but awareness. When mismatches are flagged, staff are asked to explain the reason the next day. Over time, staff become more careful with entries because they know random checks happen daily. This creates accountability and improves SOP discipline without micromanagement or fear.

---

### 6. Constraints Considered
- No barcode systems or advanced software
- Manual entry environment
- Limited staff availability
- Daily audit time limited to 5–10 minutes
- Minimal involvement required from the doctor
















## Task 2: Patient Care & Communication System Design

### 1. Problem Context
In small clinics, patients frequently message doctors directly on WhatsApp for routine queries such as follow-ups, medicine clarification, and appointment reminders. This creates communication overload for doctors, mixes critical and non-critical messages, and increases cognitive burden. A simple system is needed to manage patient communication while keeping the doctor focused on care delivery.

---

### 2. Patient Message Classification
All patient messages are classified into three categories to reduce unnecessary doctor involvement.

- **Automated Messages**
  - Appointment reminders
  - Follow-up reminders
  - Medicine refill reminders  
  These messages do not require human decision-making.

- **Human-in-the-Loop Messages**
  - Clarification on dosage already prescribed
  - Appointment rescheduling
  - Report receipt confirmation  
  These are handled by clinic staff or nurse.

- **Doctor-Only Messages**
  - New or worsening symptoms
  - Adverse drug reactions
  - Post-procedure complications  
  Only these messages reach the doctor.

This classification ensures that the doctor’s attention is reserved only for clinical decision-making.

---

### 3. Google Sheets–Based Control System
A simple Google Sheet acts as the control system for patient communication.

**Sheet Structure (Example Columns):**
- Patient Name
- Patient ID
- Contact Number
- Last Visit Date
- Message Type (Automated / Human / Doctor)
- Message Content
- Status (Pending / Sent / Escalated)
- Owner (Admin / Nurse / Doctor)
- Remarks

Each patient interaction is logged and tracked using status updates instead of informal WhatsApp threads.

---

### 4. Workflow Design
1. Patient messages are received by clinic WhatsApp or phone.
2. Clinic staff logs the message into Google Sheets.
3. Message type is selected based on classification.
4. Automated or staff-handled messages are resolved without doctor involvement.
5. Only escalated doctor-only messages are forwarded to the doctor with clear context.

This creates visibility, accountability, and traceability.

---

### 5. Minimizing Doctor Time
- Doctor does not respond to routine or administrative messages.
- Doctor receives only filtered, high-priority clinical messages.
- Each doctor message comes with patient history and clear context.
- No direct WhatsApp interruptions throughout the day.

This protects doctor time while maintaining patient care quality.

---

### 6. Optional Automation (Conceptual)
This system can later be automated using:
- Google Apps Script to trigger reminders
- SMS or WhatsApp APIs for automated messages
- Conditional rules for auto-escalation based on keywords

Automation is optional and not required for initial implementation.

---

### 7. Constraints Considered
- No new software adoption
- Works with existing HMS exports
- Low training requirement for staff
- Minimal operational cost
- Suitable for small clinics
