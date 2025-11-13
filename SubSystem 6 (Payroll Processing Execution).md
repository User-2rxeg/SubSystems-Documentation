# PAYROLL PROCESSING & EXECUTION SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** This subsystem automates the monthly or periodic operation of payroll processing, where employee data is converted into finalized salary payments through a multi-phase approval workflow.

### 🎯 What Does This Subsystem Do? (Simple Explanation)

Think of this subsystem as the monthly payroll execution engine. Configuration defined the RULES; now Processing EXECUTES those rules:
- **Initiates payroll** - starts the monthly run for a specific period and employee group
- **Processes salaries** - pulls all employees, applies all configured rules (taxes, insurance, allowances, penalties)
- **Generates drafts** - creates draft payroll for review before any payment is made
- **Reviews for errors** - automatically flags missing bank details, negative salaries, or anomalies
- **Routes approvals** - sends payroll through approval gates (specialist → manager → finance)
- **Locks and finalizes** - once approved, payroll is locked to prevent unauthorized changes
- **Generates payslips** - creates detailed salary documents for each employee
- **Transfers payment** - sends finalized data to banking system for salary disbursement

Instead of manual payroll entry (error-prone and slow), this subsystem automates the entire process—from initiation through distribution—with built-in quality checks and multi-level approvals to ensure every payment is correct and traceable.

---

## 📊 PAYROLL PROCESSING FLOW

**This epic operationalizes the configured rules into actual salary calculations. It manages end-to-end payroll execution: from initiation, simulation, and validation to final approvals and disbursement. The workflow evolves through structured phases that add automation, approval layers, and exception handling to ensure every payment is correct, auditable, and timely.**

### 🔍 What This Process Does (Simplified)

This is an 8-step processing cycle that:
1. Reviews and approves signing bonuses, resignation, termination benefits first
2. Initiates payroll for a specific period
3. Generates draft payroll with all calculations
4. Reviews for errors and anomalies
5. Gets manager approval
6. Gets finance approval
7. Locks/freezes payroll
8. Generates and distributes payslips

Each step is automated, reviewed, and approved before proceeding.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must automatically calculate salaries based on configured rules"

**Why it matters:** Requirements are the starting point—they define what functionality we're building.

---

### 👤 USER STORIES (REQ-PY)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As a Payroll Manager, I want to approve payroll runs so validation is ensured before paying employees."

**Real-World Translation:** Maria, the Payroll Manager, needs to review and approve payroll before funds leave the bank. She wants to ensure everything is correct before it goes live.

**Why it matters:** 
- Makes requirements human-centered (focuses on actual user needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Can Maria successfully approve payroll?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-30: Payroll processing must support multi-step approval workflow: Payroll Specialist → Payroll Manager → Finance Department."

**Real-World Translation:** "Payroll requires three approval gates. Each person (specialist, manager, finance) must sign off. Payroll can't proceed without all three approvals."

**Why it matters:**
- Defines exact logic developers must code
- Ensures consistency (all payroll follows the same rules)
- Creates auditability (rules are documented and traceable)
- Links to legal/compliance requirements (labor laws, tax codes)

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works.

**Example:**
```
Payroll Specialist starts payroll
  → System fetches employees
  → System calculates all salaries
  → System generates draft
  → Specialist reviews draft
  → Publishes for Manager review
  → Manager reviews & approves
  → Finance reviews & approves
  → Payroll locked
  → Payslips generated
  → Payment sent to bank
```

**Real-World Translation:** The entire monthly payroll process, from start to finish, with each step clearly defined and sequential.

**Why it matters:**
- Shows sequence of operations (order matters)
- Helps everyone understand the big picture
- Identifies where things can fail (what if approval takes too long?)
- Makes testing easier (what should happen at each step?)

---

### 🔗 THE CONNECTIONS (How They Work Together)

```
USER STORY (What the user needs)
    ↓
BUSINESS RULES (The specific rules for implementing it)
    ↓
FLOW (The step-by-step process)
    ↓
SYSTEM (Code that makes it all work)
```

**Real Example:**

| Part | Details |
|------|---------|
| **REQ-PY-6 (User Story)** | "As a Payroll Specialist, I want to review system-generated payroll results in a preview dashboard so I can confirm accuracy before finalization." |
| **BR-30 (Business Rule)** | "Payroll processing must support multi-step approval workflow: Payroll Specialist → Payroll Manager → Finance Department" |
| **FLOW (Process)** | (1) Specialist reviews draft in dashboard, (2) Publishes for Manager review, (3) Manager reviews and approves, (4) Finance reviews and approves, (5) Payroll locked |
| **IMPLEMENTATION** | Developer codes: "Create preview dashboard. Store payroll in draft state. Require specialist → manager → finance approvals before finalization." |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what users actually need
2. **Business Rules** ensure every company rule is enforced consistently
3. **Flows** ensure everything happens in the right order with proper controls
4. **Together** they create a complete, compliant, auditable payroll processing system

---

---

# PHASE 0: PRE-RUN REVIEWS & APPROVALS

## 📋 Phase Description

**Before payroll initiation begins, Payroll Specialists review, edit, and approve or reject any pending signing bonuses, resignation benefits, and termination benefits to ensure input data integrity.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Before the monthly payroll runs, you need to make sure all special payments are ready:
- Are there any new hires with signing bonuses to process this month?
- Are there any resignations or terminations with severance to process this month?
- Have these special payments been approved?

This phase ensures everything is ready before the main payroll run begins.

---

### STEP 1: Signing Bonus Review & Approval

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Reviews and approves or rejects signing bonuses before payroll initiation. |
| **Why It Matters** | Signing bonuses must be approved before they can be included in payroll. Specialist reviews, approves, or rejects based on contract and rules. |
| **Supporting Requirements** | **REQ-PY-28**: As a Payroll Specialist, I want to review and approve processed signing bonuses. |
| **What Gets Created** | Approved signing bonuses ready to be included in payroll. |
| **Related Business Rules** | **BR-24**: Signing bonuses must be processed only for employees flagged as eligible in contracts. **BR-28**: System must ensure signing bonus disbursed only once unless explicitly authorized. |

---

### STEP 2: Signing Bonus Manual Edit

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Manually edits signing bonuses when needed. |
| **Why It Matters** | Sometimes a signing bonus amount needs adjustment before payroll runs. Specialist can manually edit with full audit trail. |
| **Supporting Requirements** | **REQ-PY-29**: As a Payroll Specialist, I want to manually edit signing bonuses when needed. |
| **What Gets Created** | Modified signing bonuses with edit audit trail. |
| **Related Business Rules** | **BR-25**: Any manual overrides must require authorization. |

---

### STEP 3: Resignation & Termination Benefits Review

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Reviews and approves or rejects termination and resignation benefits before payroll initiation. |
| **Why It Matters** | Termination payouts (severance, gratuity, accrued leave) must be approved before included in payroll. Complex calculations need review. |
| **Supporting Requirements** | **REQ-PY-31**: As a Payroll Specialist, I want to review and approve processed benefits upon resignation. |
| **What Gets Created** | Approved termination/resignation benefits ready for payroll inclusion. |
| **Related Business Rules** | **BR-26**: Termination benefits must not be processed until HR clearance complete. **BR-27**: Manual adjustments must require Payroll Specialist approval and logging. |

---

### STEP 4: Resignation & Termination Benefits Manual Edit

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Manually edits termination and resignation benefits when needed. |
| **Why It Matters** | Sometimes benefit calculations need adjustment. Specialist can edit with full audit trail. |
| **Supporting Requirements** | **REQ-PY-32**: As a Payroll Specialist, I want to manually edit benefits upon resignation when needed. |
| **What Gets Created** | Modified benefits with edit audit trail. |
| **Related Business Rules** | **BR-27**: Manual adjustments must require approval and logging. |

---

---

# PHASE 1: PAYROLL INITIATION

## 📋 Phase Description

**Payroll Specialists review the payroll period to approve or reject it to ensure it matches the current cycle. If rejected, they can manually edit the period and restart. If approved, Payroll Specialists directly start payroll initiation.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Setting up which employees and which time period:
- What period is this payroll for? (e.g., November 1-30, 2025)
- Is this the right month?
- Have any dates changed?
- Once approved, start automatic processing

---

### STEP 5: Review Payroll Period

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Reviews the payroll period (dates) to approve or reject, ensuring it matches current cycle. |
| **Why It Matters** | Must process payroll for the correct period. Wrong dates could delay or process wrong month's salaries. |
| **Supporting Requirements** | **REQ-PY-24**: As a Payroll Specialist, I want to review and approve processed payroll initiation. |
| **What Gets Created** | Approved payroll period confirmed. |
| **Related Business Rules** | BR-3: Payroll must be processed within defined cycles per local laws. |

---

### STEP 6: Edit Payroll Period (If Rejected)

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Manually edits the payroll period if rejected. |
| **Why It Matters** | If dates were wrong, specialist corrects and restarts approval. |
| **Supporting Requirements** | **REQ-PY-26**: As a Payroll Specialist, I want to manually edit payroll initiation when needed. |
| **What Gets Created** | Corrected payroll period for re-approval. |
| **Related Business Rules** | N/A |

---

### STEP 7: Start Automatic Processing

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Starts automatic payroll initiation after period is approved. |
| **Why It Matters** | Kicks off the entire payroll processing pipeline. Once approved, system automatically fetches employees and begins calculations. |
| **Supporting Requirements** | **REQ-PY-23**: As a Payroll Specialist, I want the system to automatically process payroll initiation. |
| **What Gets Created** | Payroll processing begins; moves to draft generation. |
| **Related Business Rules** | BR-63: Any payroll initiation must go through validation checks before processing. |

---

---

# PHASE 1.1: PAYROLL DRAFT GENERATION

## 📋 Phase Description

**The goal is to generate a draft version of the payroll run consisting of three sub-phases: (1) Fetching employees and checking HR events, (2) Salary calculations, (3) Draft generation with all details and breakdowns.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Automatically generating the draft payroll:
- Fetch all employees for this period
- Check for new hires, resignations, terminations
- Apply all salary rules (pay grade, allowances, taxes, insurance, penalties)
- Generate detailed payroll with all numbers
- This is a DRAFT, not final—will be reviewed for errors

---

## PHASE 1.1.A: FETCH EMPLOYEES & CHECK HR EVENTS

### STEP 8: Check HR Events

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | Fetches employees by department and checks for HR events (normal, new hire, resignation, termination). |
| **Why It Matters** | Different employee statuses need different calculations. New hires get signing bonuses; terminated employees get severance. System must know who's who. |
| **Supporting Requirements** | **REQ-PY-2**: As a Payroll Specialist, I want system to calculate prorated salaries for mid-month hires/terminations. |
| **What Gets Created** | List of all employees for this period, categorized by status (normal, new hire, resigned, terminated). |
| **Related Business Rules** | **BR-56**: Upon employee resignation, system must automatically calculate resignation entitlements. **BR-29**: Upon termination, system must calculate termination entitlements. |
| **Inputs Needed** | HR System (Employee status data) |

---

### STEP 9: Auto-Process Signing Bonus (For New Hires)

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | For newly hired employees, system automatically processes signing bonuses in their calculation. |
| **Why It Matters** | New hires that approved signing bonuses must receive them in first payroll. System automates this. |
| **Supporting Requirements** | **REQ-PY-27**: As a Payroll Specialist, I want system to automatically process signing bonuses. |
| **What Gets Created** | Signing bonuses included in new hire salary calculations. |
| **Related Business Rules** | **BR-24**: Signing bonuses only for eligible employees. **BR-28**: Disbursed only once. |
| **Inputs Needed** | Onboarding System (New hire flag, bonus amount) |

---

### STEP 10: Auto-Process Resignation/Termination Benefits

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | For resigned or terminated employees, system automatically processes termination and resignation benefits. |
| **Why It Matters** | Departing employees get severance, accrued leave, gratuity per law and contract. System automates complex calculation. |
| **Supporting Requirements** | **REQ-PY-30**: As a Payroll Specialist, I want system to automatically process benefits upon resignation per business rules & contracts. |
| **What Gets Created** | Termination/resignation benefits calculated and included. |
| **Related Business Rules** | **BR-29**: System must automatically calculate termination entitlements per contract and law. **BR-56**: System calculates resignation entitlements. |
| **Inputs Needed** | Offboarding System (Resignation/termination status, last day date) |

---

---

## PHASE 1.1.B: SALARY CALCULATIONS (GROSS TO NET)

### STEP 11: Deductions Calculations (Taxes & Insurance) = Net Salary

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | Calculates deductions (taxes, insurance) to get net salary using formula: Net Salary = Gross (from Pay Grade) − Taxes − Insurance. |
| **Why It Matters** | This is the core calculation. Gross salary minus all legal deductions equals net (what employee receives). |
| **Supporting Requirements** | **REQ-PY-3**: As a Payroll Specialist, I want system to auto-apply statutory rules (income tax, pension, insurance) so compliance is ensured. |
| **What Gets Created** | Net salary calculated for each employee. |
| **Related Business Rules** | **BR-35**: System must calculate net as: Gross Salary – Taxes – Social Insurance. **BR-11**: Deductions for unpaid leave calculated. **BR-34**: All deductions applied after gross, before net. |
| **Inputs Needed** | Pay Grade System (Gross salary), Configuration (Tax tables, insurance rates) |

---

### STEP 12: Salary Calculation (Final = Net − Penalties)

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | Calculates final paid salary: Final Salary = Net − Penalties (missing hours, unpaid days, other deductions). |
| **Why It Matters** | After deductions, penalties are applied. Missing work hours, unpaid leave, misconduct penalties reduce final pay. |
| **Supporting Requirements** | REQ-PY-3 (implied) |
| **What Gets Created** | Final salary amount for each employee. |
| **Related Business Rules** | **BR-33**: System applies deductions for misconduct penalties. **BR-60**: Penalties can't reduce below minimum wage. |
| **Inputs Needed** | Time Management (Missing hours, OT), Leaves (Unpaid leave status), HR penalties |

---

---

## PHASE 1.1.C: PAYROLL DRAFT GENERATION

### STEP 13: Generate Draft Payroll

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | Draft payroll generated with all details and full breakdowns. |
| **Why It Matters** | Complete record of all calculations before finalization. Shows every component for every employee. |
| **Supporting Requirements** | **REQ-PY-4**: As a Payroll Specialist, I want system to generate draft payroll automatically at cycle end. |
| **What Gets Created** | Draft payroll file with all employee records and calculations. |
| **Related Business Rules** | **BR-9**: Payroll structure shows base, allowances, deductions. **BR-36**: All calculation elements stored. **BR-31**: Payroll schema applied. |
| **Inputs Needed** | All previous calculations (salaries, deductions, penalties) |

---

---

# PHASE 2: PAYROLL DRAFT REVIEW

## 📋 Phase Description

**System automatically flags anomalies such as missing bank details or negative net pay for correction. Payroll run status becomes "Under Review".**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Quality control check:
- Missing bank account info? Flag it
- Negative salary (penalties too high)? Flag it
- Salary spike (100x normal)? Flag it
- Any other anomalies? Flag it

System reviews draft, flags issues, marks as "Under Review" until fixed.

---

### STEP 14: Flag Irregularities

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | System flags irregularities (sudden salary spikes, missing bank accounts, negative net pay) for correction. |
| **Why It Matters** | Catches errors before they're approved. Prevents paying wrong amounts or failing to transfer funds. |
| **Supporting Requirements** | **REQ-PY-5**: As a Payroll Specialist, I want system to flag irregularities so I can take required action. |
| **What Gets Created** | List of flagged anomalies requiring resolution. |
| **Related Business Rules** | BR-63: Validation checks needed before processing. BR-66: Contract status checked. |
| **Outputs To** | Payroll Manager (for review) |

---

---

# PHASE 3: REVIEW & APPROVAL WORKFLOW

## 📋 Phase Description

**Close payroll cycle through hierarchy of approvals. Payroll Specialists review draft in preview dashboard and publish for Payroll Manager and Finance Staff review and approval. Payroll Manager resolves exceptions. If approved, status changes to "Waiting Finance Staff Approval." Finance Staff review; if approved, Payroll Manager locks/freezes; if rejected, Payroll Specialists restart after adjustments. Payroll Manager can unfreeze with justification.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Multi-level approval process:
1. Specialist reviews draft in dashboard
2. Publishes for Manager review
3. Manager reviews and resolves errors
4. If OK, publishes for Finance review
5. Finance reviews; if OK, marks as "Paid"
6. Manager locks the payroll
7. If needed later, Manager can unlock with reason

Each level is a gate that prevents bad payrolls from proceeding.

---

### STEP 15: Payroll Specialist Reviews Draft

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Reviews system-generated payroll results in preview dashboard to confirm accuracy before finalization. |
| **Why It Matters** | First human review. Specialist checks if calculations look right before sending to manager. |
| **Supporting Requirements** | **REQ-PY-6**: As a Payroll Specialist, I want to review payroll results in preview dashboard. |
| **What Gets Created** | Specialist review documented; payroll ready for manager review or flagged issues noted. |
| **Related Business Rules** | N/A |

---

### STEP 16: Publish for Manager & Finance Review

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Publishes draft payroll for Payroll Manager and Finance Staff review and approval. |
| **Why It Matters** | Escalates payroll up approval chain. Manager and Finance get notification and access to review. |
| **Supporting Requirements** | **REQ-PY-12**: As a Payroll Specialist, I want to send payroll for approval to Manager and Finance before finalization. |
| **What Gets Created** | Payroll moved to manager/finance queue; they receive notification. |
| **Related Business Rules** | **BR-30**: Multi-step approval workflow: Specialist → Manager → Finance. |

---

### STEP 17: Payroll Manager Reviews & Resolves Exceptions

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Manager |
| **What They Do** | Reviews payroll draft and resolves any exceptions. |
| **Why It Matters** | Manager is responsible for quality. Reviews all flagged issues and decides if they're fixable or need specialist to restart. |
| **Supporting Requirements** | **REQ-PY-20**: As a Payroll Manager, I want to resolve escalated irregularities. |
| **What Gets Created** | Exceptions resolved or marked for specialist revision. |
| **Related Business Rules** | N/A |

---

### STEP 18: Payroll Manager Approves or Rejects

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Manager |
| **What They Do** | Approves payroll before distribution or rejects with reason. If approved, status changes to "Waiting Finance Staff Approval." If rejected, Payroll Specialists notified to restart after adjustments. |
| **Why It Matters** | Manager gate. If manager doesn't approve, payroll doesn't proceed. Ensures managerial oversight. |
| **Supporting Requirements** | **REQ-PY-22**: As a Payroll Manager, I want to approve payroll runs so validation ensured at managerial level. |
| **What Gets Created** | Manager approval/rejection logged. |
| **Related Business Rules** | BR-30: Multi-step approval workflow. |

---

### STEP 19: Finance Staff Reviews & Approves/Rejects

| Aspect | Details |
|--------|---------|
| **Actor** | Finance Staff |
| **What They Do** | Reviews payroll. If approved, payment status becomes "Paid" and Payroll Manager notified to lock payroll. If rejected, Finance specifies reason and Payroll Specialists notified to restart. |
| **Why It Matters** | Finance gate. Finance ensures funds are available, bank details correct, amounts reasonable before approval. Only Finance can approve payment. |
| **Supporting Requirements** | **REQ-PY-15**: As Finance Staff, I want to approve payroll disbursements so no incorrect payments made. |
| **What Gets Created** | Finance approval/rejection logged. Payment status set to "Paid" if approved. |
| **Related Business Rules** | **BR-18**: Payroll results need review by finance before payment file generation. **BR-30**: Multi-step approval. |

---

### STEP 20: Payroll Manager Locks/Freezes Payroll

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Manager |
| **What They Do** | Locks or freezes finalized payroll so no unauthorized retroactive changes made. |
| **Why It Matters** | Once finalized, payroll should be immutable to prevent fraud/errors. Locked payroll can't be changed without special justification. |
| **Supporting Requirements** | **REQ-PY-7**: As a Payroll Manager, I want to lock finalized payroll so no unauthorized retroactive changes made. |
| **What Gets Created** | Payroll locked; no further changes allowed without unfreeze. |
| **Related Business Rules** | N/A |

---

### STEP 21: Payroll Manager Unfreezes (If Needed)

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Manager |
| **What They Do** | Exceptionally unfreezes payroll by entering justification. |
| **Why It Matters** | Sometimes after locking, legitimate corrections are discovered. Manager can unlock with documented reason for audit trail. |
| **Supporting Requirements** | **REQ-PY-19**: As Payroll Manager, I want authority to unfreeze payrolls under exceptional circumstances with reason. |
| **What Gets Created** | Payroll unfrozen with justification logged. Can make corrections. |
| **Related Business Rules** | N/A |

---

---

# PHASE 5: EXECUTION & PAYSLIP GENERATION

## 📋 Phase Description

**Upon approval, Payroll Specialists allow system to automatically generate and distribute detailed payslips according to defined business rules.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Final step—create and send payslips:
- Generate detailed PDF payslips for each employee
- Show all salary components
- Show all deductions
- Send via email, portal, or print
- Employee receives notification
- Payment sent to bank

---

### STEP 22: Generate & Distribute Payslips

| Aspect | Details |
|--------|---------|
| **Actor** | System (automated) |
| **What They Do** | Automatically generates and distributes employee payslips (PDF, email, portal) after all approvals complete. |
| **Why It Matters** | Payslip is employee's proof of salary. Must show all components and deductions clearly. Multiple delivery methods for employee convenience. |
| **Supporting Requirements** | **REQ-PY-8**: As Payroll Specialist, I want system to auto-generate and distribute payslips so staff access details securely. |
| **What Gets Created** | Payslips generated and distributed to employees. |
| **Related Business Rules** | **BR-17**: Auto-generated payslip with clear breakdown of components. **BR-36**: All calculation elements stored. |
| **Outputs To** | Employees (via email, portal), Banking system (payment file) |

---

---


# 📋 COMPLETE PAYROLL USER STORIES REFERENCE (PROCESSING & EXECUTION)

### REQ-PY-1: Auto-Calculate Salaries
**What User Needs:** "As a Payroll Specialist, I want system to automatically calculate salaries, allowances, deductions based on configured rules so I don't need manual calculations."

**Why It Matters:** Manual calculations are error-prone and slow. System automates using configured rules, ensuring consistency and speed.

**Related BRs:** BR-1, BR-2, BR-9

**System Must Support:**
- Automatically fetch employee data
- Apply configured pay grades
- Calculate taxes automatically
- Calculate insurance automatically
- Apply allowances automatically
- Apply penalties automatically
- Calculate net salary automatically

---

### REQ-PY-2: Prorated Salary Calculation
**What User Needs:** "As a Payroll Specialist, I want system to calculate prorated salaries (mid-month hires, terminations) so payments are accurate for partial periods."

**Why It Matters:** Employees joining mid-month shouldn't get full month salary. Employees leaving mid-month get partial salary plus severance. System must calculate correctly.

**Related BRs:** BR-1, BR-29

**System Must Support:**
- Identify hire date and termination date
- Calculate pro-rated salary for partial months
- Apply signing bonus only for new hires
- Apply termination benefits only for departing employees

---

### REQ-PY-3: Auto-Apply Statutory Rules
**What User Needs:** "As a Payroll Specialist, I want system to auto-apply statutory rules (income tax, pension, insurance, labor deductions) so compliance is ensured without manual intervention."

**Why It Matters:** Tax and insurance laws are complex. Manual application risks non-compliance. System automates ensuring legal compliance.

**Related BRs:** BR-5, BR-6, BR-7, BR-8

**System Must Support:**
- Automatically apply income tax per configured brackets
- Automatically apply pension contributions
- Automatically apply health/social insurance
- Automatically apply labor law deductions
- Automatically apply payroll-specific rules

---

### REQ-PY-4: Generate Draft Automatically
**What User Needs:** "As a Payroll Specialist, I want system to generate draft payroll automatically at cycle end so I only need to review and approve."

**Why It Matters:** Generation is automatic and fast. Specialist only needs to review (not generate from scratch), saving huge amounts of time.

**Related BRs:** BR-31, BR-36

**System Must Support:**
- At configured time (e.g., month end), automatically start payroll
- Automatically fetch all employees
- Automatically calculate all salaries
- Automatically generate complete payroll draft
- Notify specialist that draft is ready

---

### REQ-PY-5: Flag Irregularities
**What User Needs:** "As a Payroll Specialist, I want system to flag irregularities (sudden salary spikes, missing bank accounts, negative net pay) so I can take required action."

**Why It Matters:** Anomalies indicate errors. System flags them so specialist doesn't miss issues.

**Related BRs:** BR-63

**System Must Support:**
- Detect sudden salary spikes (200% increase)
- Detect missing bank account details
- Detect negative net pay
- Detect other business rule violations
- Flag with clear description of issue

---

### REQ-PY-6: Review in Preview Dashboard
**What User Needs:** "As a Payroll Specialist, I want to review system-generated payroll results in preview dashboard so I can confirm accuracy before finalization."

**Why It Matters:** Dashboard provides easy review interface before payroll goes live. Specialist can see all data and spot errors.

**Related BRs:** N/A

**System Must Support:**
- Display all employees and their calculated salaries
- Show all salary components (gross, deductions, net)
- Allow filtering/searching
- Show flagged issues with clear descriptions
- Allow drill-down to see details

---

### REQ-PY-7: Lock/Freeze Payroll
**What User Needs:** "As a Payroll Manager, I want to lock or freeze finalized payroll so no unauthorized retroactive changes are made."

**Why It Matters:** Once finalized and sent to bank, payroll should be immutable. Lock prevents accidental/fraudulent changes.

**Related BRs:** N/A

**System Must Support:**
- Lock approved payroll
- Prevent changes to locked payroll
- Audit trail showing who locked and when
- Only manager can unlock

---

### REQ-PY-8: Auto-Generate & Distribute Payslips
**What User Needs:** "As a Payroll Specialist, I want system to auto-generate and distribute payslips (PDF, email, portal) so staff access details securely."

**Why It Matters:** Payslips are employee record of salary. System automatically generates and delivers securely.

**Related BRs:** BR-17, BR-36

**System Must Support:**
- Generate PDF payslips for each employee
- Show all salary components
- Show all deductions
- Email payslip to employee
- Post payslip to employee portal
- Send payment notification

---

### REQ-PY-12: Send for Approval
**What User Needs:** "As a Payroll Specialist, I want to send payroll for approval to Manager and Finance before finalization so payments not made without validation."

**Why It Matters:** Payroll requires multiple approvals. System must facilitate sending to approvers and tracking approvals.

**Related BRs:** BR-30, BR-18

**System Must Support:**
- Publish payroll for manager review
- Notify manager of pending payroll
- Publish payroll for finance review
- Notify finance of pending payroll
- Track approval status
- Escalate if approvals delayed

---

### REQ-PY-15: Finance Approve Disbursements
**What User Needs:** "As Finance Staff, I want to approve payroll disbursements before execution so no incorrect payments are made."

**Why It Matters:** Finance is gatekeeper for bank transfers. Finance must approve before payment processing.

**Related BRs:** BR-18

**System Must Support:**
- Finance can review all payroll details
- Finance can approve payroll
- Finance can reject with reason
- Finance notified when payroll awaits approval
- Approval logged with timestamp

---

### REQ-PY-19: Unfreeze Payroll
**What User Needs:** "As Payroll Manager, I want authority to unfreeze payrolls under exceptional circumstances with reason so legitimate corrections can be made even after locked."

**Why It Matters:** Rarely, after locking, corrections are needed. Manager can unlock with documented justification.

**Related BRs:** N/A

**System Must Support:**
- Manager can unfreeze locked payroll
- Requires reason/justification entry
- Audit trail shows unfreeze with reason
- Can make corrections after unfreeze
- Re-lock after corrections

---

### REQ-PY-20: Resolve Irregularities
**What User Needs:** "As Payroll Manager, I want to resolve escalated irregularities so payroll exceptions addressed at higher decision level."

**Why It Matters:** Some issues need manager decision. Manager reviews and resolves flagged issues.

**Related BRs:** N/A

**System Must Support:**
- View all flagged irregularities
- Understand issue details
- Decide on resolution (approve anyway, fix and restart, reject)
- Document decision
- Proceed based on decision

---

### REQ-PY-22: Approve Payroll
**What User Needs:** "As Payroll Manager, I want to approve payroll runs so validation ensured at managerial level prior to distribution."

**Why It Matters:** Manager is accountability gate. Manager review ensures payroll is correct before it's finalized and sent to bank.

**Related BRs:** BR-30

**System Must Support:**
- Review all payroll details
- Approve or reject payroll
- If reject, provide reason
- If approve, payroll moves to finance
- Approval logged

---

### REQ-PY-23: Auto-Process Initiation
**What User Needs:** "As a Payroll Specialist, I want system to automatically process payroll initiation."

**Why It Matters:** Initiation is automatic once specialist approves period. System starts fetching employees and calculating.

**Related BRs:** BR-63, BR-66

**System Must Support:**
- Automatically fetch all employees for period
- Check contract status (active, expired, suspended)
- Validate all prerequisites met
- Start salary calculations
- Generate draft

---

### REQ-PY-24: Review Initiation
**What User Needs:** "As a Payroll Specialist, I want to review and approve processed payroll initiation."

**Why It Matters:** Specialist confirms period is correct before system proceeds. Prevents wrong month processing.

**Related BRs:** BR-3

**System Must Support:**
- Display proposed payroll period
- Show which employees included
- Show validation results
- Approve or reject
- Restart if rejected

---

### REQ-PY-26: Edit Initiation
**What User Needs:** "As a Payroll Specialist, I want to manually edit payroll initiation when needed."

**Why It Matters:** If period is wrong, specialist corrects before restarting.

**Related BRs:** N/A

**System Must Support:**
- Allow changing payroll period dates
- Allow excluding/including employees if needed
- Allow manual adjustments
- Restart processing with changes

---

### REQ-PY-27: Auto-Process Signing Bonuses
**What User Needs:** "As a Payroll Specialist, I want system to automatically process signing bonuses."

**Why It Matters:** System automates bonus inclusion for new hires per configuration.

**Related BRs:** BR-24, BR-28, BR-56

**System Must Support:**
- Identify new hires with signing bonuses
- Automatically include bonuses in payroll
- Ensure only processed once
- Track bonus disbursement

---

### REQ-PY-28: Review Signing Bonuses
**What User Needs:** "As a Payroll Specialist, I want to review and approve processed signing bonuses."

**Why It Matters:** Before payroll runs, specialist reviews bonuses to ensure they're correct.

**Related BRs:** BR-24

**System Must Support:**
- View all signing bonuses to be processed
- See eligibility and amounts
- Approve or reject each
- Track approvals

---

### REQ-PY-29: Edit Signing Bonuses
**What User Needs:** "As a Payroll Specialist, I want to manually edit signing bonuses when needed."

**Why It Matters:** Sometimes bonus amount needs adjustment before payroll.

**Related BRs:** BR-25

**System Must Support:**
- Allow changing bonus amounts
- Audit trail for changes
- Justification requirement
- Re-approval after change

---

### REQ-PY-30: Auto-Process Resignation Benefits
**What User Needs:** "As a Payroll Specialist, I want system to automatically process benefits upon resignation per business rules & contracts."

**Why It Matters:** System automates complex termination calculations for departing employees.

**Related BRs:** BR-29, BR-56

**System Must Support:**
- Identify resigned employees
- Calculate resignation entitlements per contract
- Calculate end-of-service benefits per law
- Include in final payroll

---

### REQ-PY-31: Review Resignation Benefits
**What User Needs:** "As a Payroll Specialist, I want to review and approve processed benefits upon resignation."

**Why It Matters:** Before payroll, specialist reviews termination amounts to ensure correctness.

**Related BRs:** BR-26, BR-27

**System Must Support:**
- View all resignation benefits
- See calculation details
- Approve or reject
- Track approvals

---

### REQ-PY-32: Edit Resignation Benefits
**What User Needs:** "As a Payroll Specialist, I want to manually edit benefits upon resignation when needed."

**Why It Matters:** Sometimes calculated amounts need adjustment.

**Related BRs:** BR-27

**System Must Support:**
- Allow editing benefit amounts
- Audit trail for changes
- Justification requirement
- Re-approval after change

---

### REQ-PY-33: Auto-Process Termination Benefits
**What User Needs:** "As a Payroll Specialist, I want system to automatically process benefits upon termination per business rules & contracts."

**Why It Matters:** System automates termination calculations per law and contract.

**Related BRs:** BR-29, BR-56

**System Must Support:**
- Identify terminated employees
- Calculate termination entitlements per contract
- Calculate gratuity per law
- Include in final payroll

---

---

# 📋 COMPLETE PAYROLL BUSINESS RULES REFERENCE TABLE

This section contains ALL Payroll Business Rules with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-1** | The system must require an active employment contract with a defined role, type (full-time, part-time, hourly, commission-based, etc.), start/end dates and salary basis before payroll can be processed. Local labor law (Egyptian labor law 2025) need to be followed. |
| **BR-2** | The system must calculate base salary according to contract terms and role type. |
| **BR-3** | Payroll must be processed within defined cycles (monthly, etc) per contract or region following the local laws. |
| **BR-4** | The system must identify the minimum salary bracket(s) enforced through Local Labor Law. |
| **BR-5** | The system must identify the payroll income taxes' brackets enforced through Local Tax Law. |
| **BR-6** | The system must support multiple tax components (e.g. income tax, exemptions). |
| **BR-7** | The system must identify the social insurances' brackets enforced through Social Insurance and Pensions Law. |
| **BR-8** | The system must calculate employee and employer social insurance contributions according to the local Social Insurance and Pensions Law, with contribution percentages configurable. The same needs to be applied for the state-based Health Insurance system. |
| **BR-9** | Payroll Structure must support base pay, allowances, deductions, and other variable pay elements. |
| **BR-10** | The system allows for multiple pay scales configurable by grade, department, or location. |
| **BR-11** | The system must deduct pay for unpaid leave days based on daily/hourly salary calculations. |
| **BR-17** | An auto-generated Payslip should be available through the system with a clear breakdown of components. |
| **BR-18** | Payroll results needs to be reviewed by finance before payment file generation. |
| **BR-20** | All payroll records must Support local tax law customization (i.e. as per Egyptian labor law 2025 and other laws' requirements). |
| **BR-23** | The system must support issuing reports about standard payroll summary, tax reports, and pay slip history. |
| **BR-24** | Signing bonuses must be processed only for employees flagged as eligible in their contracts (linked through Employee Profile). |
| **BR-25** | Any manual overrides for signing bonuses must require authorization. |
| **BR-26** | Termination benefits must not be processed until HR clearance and final approvals are completed. |
| **BR-27** | Manual adjustments to termination payouts must require Payroll Specialist approval and full system logging. |
| **BR-28** | The system must ensure a signing bonus is disbursed only once unless explicitly authorized. |
| **BR-29** | Upon employee termination, the system must automatically calculate termination-related entitlements (e.g., severance pay, end-of-service gratuity, pending compensation) according to contract and local labor law. |
| **BR-30** | Payroll processing must support multi-step approval workflow: Payroll Specialist → Payroll Manager → Finance Department. |
| **BR-31** | The system needs to have a breakdown: Payroll schemas and Payroll areas. A. Payroll Area picks the employees and period. B. Payroll Schemas is the payroll logic (Net Salary = Gross (base pay + allowances) – Taxes – Social/Health Insurance – Other Deductions). |
| **BR-33** | The system must apply deductions for misconduct penalties (e.g., lateness, asset damage, disciplinary actions) as configured by HR policy, consistent with Egyptian law. |
| **BR-34** | The system must ensure all deductions (taxes, insurance, penalties, unpaid leave, recovery) are applied after gross salary calculation and before net salary. |
| **BR-35** | The system must calculate net salary as: Gross Salary – Taxes – Social Insurance. |
| **BR-36** | The system must store all calculation elements (salary base, allowances, taxes, deductions) for auditability and compliance. |
| **BR-38** | The system must allow defining allowances with multiple types as part of the employment contract and add them to payroll as part of gross salary, defined per role or contract. |
| **BR-39** | Allowance Structure must support and track different types (e.g. transportation, housing, meals, etc). |
| **BR-46** | Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. |
| **BR-56** | The system must support signing bonuses as a distinct payroll component, configurable by contract terms (e.g., one-time, etc.), and subject to approval workflows. Upon employee resignation, the system must automatically calculate resignation-related entitlements (e.g., accrued leave payout, service completion benefits, pending allowances) according to contract and local labor law, and end-of-service benefits (gratuity, accrued leave encashment, pending allowances) according to company policy and labor law. |
| **BR-59** | The system must generate gross-to-net breakdown reports for employees and management to validate calculations. |
| **BR-60** | Misconduct penalties must not reduce salary below statutory minimum wages. |
| **BR-63** | Any payroll initiation or modification (automatic or manual) must go through validation checks (e.g., contract active, no expired approvals, minimum wage compliance) before processing. |
| **BR-64** | The system needs to be linked to the organization's as well as the employees' accounts to facilitate processing payroll. |
| **BR-66** | Payroll must not be processed if an employee's contract is expired, inactive, or suspended. |

---

