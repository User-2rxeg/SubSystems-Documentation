# TIME MANAGEMENT SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** This module automates scheduling, attendance tracking, and policy enforcement within the HR Management System.

### 🎯 What Does This Module Do? (Simple Explanation)

Think of this system as an intelligent attendance assistant that:
- **Automatically tracks** when employees clock in and out across multiple channels (biometric, web, mobile, manual)
- **Manages schedules** by assigning standardized work shifts to employees individually, by department, or by position
- **Enforces rules** like preventing people from clocking in outside their shift windows and tracking policy violations automatically
- **Syncs data** with payroll, benefits, and leave systems so employees get paid correctly
- **Routes approvals** for overtime, corrections, and exceptions through defined workflows

Instead of HR managers manually tracking everyone's hours and calculating overtime by hand, this system does it automatically, consistently, and with a complete audit trail of every action.

---

## 📊 TIME MANAGEMENT FLOW

**The Time Management Module automates the administration of employee scheduling, attendance validation, and time-related exceptions. It ensures accurate time data capture, compliance with working policies, and seamless integration with payroll and leave systems. The process unfolds across several structured phases.**

### 🔍 What This Process Does (Simplified)

This is a 5-step cycle that:
1. Sets up work shifts (defines when people should work)
2. Records who actually showed up and when
3. Applies company rules (like penalties for being late)
4. Reviews and approves any exceptions (like overtime requests)
5. Sends the final data to payroll so people get paid

Each step builds on the previous one to create a complete, reliable system.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must track employee attendance"

**Why it matters:** Requirements are the starting point—they define what problem we're solving.

---

### 👤 USER STORIES (US)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As an HR Manager, I want to configure overtime rules, so that overtime is calculated fairly and consistently."

**Real-World Translation:** Janet, the HR Manager, needs to set up company overtime policy without asking IT for help every time. When she configures it once, the system automatically applies it to all employees.

**Why it matters:** 
- Makes requirements human-centered (focuses on actual user needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Did Janet successfully set up overtime rules?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-TM-09: Early/Lateness per shift must follow HR rules (grace period, penalty thresholds, escalation)."

**Real-World Translation:** "The system must know: 5 minutes late = OK (grace period). 15 minutes late = -30 mins pay (penalty). 3rd time late = escalate to HR (escalation)."

**Why it matters:**
- Defines the exact logic developers must code
- Ensures consistency (everyone gets the same rules applied)
- Creates auditability (rules are documented, not hidden in code)
- Links to legal/compliance requirements

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works, from start to finish.

**Example:**
```
Employee clocks in 
  → System validates against shift
  → System creates attendance record
  → Manager reviews if missing
  → Payroll receives data
```

**Real-World Translation:** Sarah works 9-5. At 9:01 AM she clocks in (using fingerprint scanner). The system checks: "Is Sarah assigned a 9am shift today?" Yes. "Is 9:01 within her allowed window?" Yes. System creates a timestamped record. If Sarah forgot to clock out, the system alerts her manager. Eventually all of Sarah's data goes to payroll.

**Why it matters:**
- Shows the sequence of operations (order matters)
- Helps everyone understand the big picture
- Identifies where things can go wrong (what if Sarah forgets to clock out?)
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
| **US-8 (User Story)** | "As a Line Manager, I want to flag missed punches and send alerts so corrections are made promptly." |
| **BR-TM-14 (Business Rule)** | "Missed punches/late sign-ins must be handled via auto-flagging, notifications, or payroll blocking." |
| **FLOW (Process)** | (1) System detects missing clock-out, (2) System flags it, (3) System sends notification to manager and employee, (4) Manager manually adds the punch or employee corrects it |
| **IMPLEMENTATION** | Developer codes the logic: "If clock-in exists but no clock-out after 8 hours, flag + send email/SMS to both parties" |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what users actually need (not what developers think they need)
2. **Business Rules** ensure every company rule is enforced consistently
3. **Flows** ensure everything happens in the right order
4. **Together** they create a complete, testable, auditable system

---

# 📊 COMPREHENSIVE REQUIREMENTS MATRIX

## Overview of All Requirements by Phase

| Phase | Requirement Name | US ID | BR IDs |
|-------|------------------|-------|--------|
| **Phase 1** | Shift Configuration & Types | US-2 | BR-TM-03, BR-TM-04 |
| **Phase 1** | Shift Assignment Management | US-1 | BR-TM-02, BR-TM-05 |
| **Phase 1** | Custom Scheduling Rules | US-3 | BR-TM-04, BR-TM-10 |
| **Phase 1** | Shift Expiry Notifications | US-4 | BR-TM-02, BR-TM-05 |
| **Phase 2** | Employee Clock-In/Clock-Out | US-5 | BR-TM-06, BR-TM-12, BR-TM-13 |
| **Phase 2** | Manual Attendance Correction | US-6 | BR-TM-06, BR-TM-24 |
| **Phase 2** | Flexible Punch Handling | US-7 | BR-TM-07, BR-TM-11 |
| **Phase 2** | Missed Punch Management & Alerts | US-8 | BR-TM-14 |
| **Phase 3** | Overtime & Short Time Configuration | US-10 | BR-TM-08, BR-TM-16 |
| **Phase 3** | Lateness & Penalty Rules Setup | US-11 | BR-TM-09, BR-TM-10 |
| **Phase 3** | Repeated Lateness Handling | US-12 | BR-TM-09, BR-TM-16 |
| **Phase 3** | Attendance Correction Requests | US-13 | BR-TM-15 |
| **Phase 4** | Time Exception Approval Workflow | US-14 | BR-TM-01, BR-TM-15, BR-TM-18, BR-TM-20 |
| **Phase 4** | Holiday & Rest Day Configuration | US-17 | BR-TM-19 |
| **Phase 4** | Vacation Package Integration | US-16 | BR-TM-19 |
| **Phase 4** | Escalation Before Payroll Cut-Off | US-18 | BR-TM-20 |
| **Phase 5** | Payroll Synchronization | US-20 | BR-TM-22 |
| **Phase 5** | Reporting & Analytics Generation | US-19 | BR-TM-21, BR-TM-23 |
| **Cross-Module** | Data Integrity & Audit | N/A | BR-TM-24, BR-TM-25 |

---

# PHASE 1: SHIFT SETUP AND SCHEDULING

## 📋 Phase Description

**The process begins when the HR Manager or System Administrator defines standardized shift configurations such as normal, split, overnight, and rotational types. These templates establish the foundation for all scheduling and attendance operations. Once shift types are configured, the HR or System Administrator assigns them to employees individually or in bulk—by department or position—to ensure accurate coverage of all working hours. Subsequently, the HR Manager defines custom scheduling rules, including flexible hours, rotational work patterns, or compressed workweeks, allowing the organization to adapt to diverse work arrangements. The system then monitors shift expiry and triggers automated notifications to HR staff to renew or reassign shifts when required.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Imagine you're running a 24-hour store or factory. You need:
- Different shift types (morning, evening, overnight, split shifts)
- To assign these shifts to people in ways that make sense (some people work mornings, others nights, some rotate)
- Flexible options for different jobs
- Reminders when shift assignments are about to expire so you don't leave positions unfilled

This phase handles all of that planning and setup.

---

### STEP 1: Shift Configuration & Types

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager / System Admin |
| **What They Do** | Defines and configures standard shift types (Normal, Split, Overnight, Rotational) and naming templates that will be used across the organization. |
| **Why It Matters** | Creates consistency across the entire organization—everyone knows what "Split Shift" means, what hours it covers, etc. |
| **Supporting Requirements** | **US-2** (User Story 2): As an HR Manager/System Admin, I want to define and configure shift types (Normal, Split, Overnight, Rotational, etc.) and their corresponding names so that different work arrangements are supported consistently. |
| **What Gets Created** | Shift templates are created and stored for use in scheduling; foundational data for later attendance tracking. |
| **Related Business Rules** | **BR-TM-03**: The system must support multiple shift types (Normal, Split, Overnight, Mission, Rotational) with start and end dates. **BR-TM-04**: The system must support multiple shift names (Fixed Core Hours, Flex-Time, Rotational, Split, Custom Weekly Patterns, Overtime). |

---

### STEP 2: Shift Assignment Management

| Aspect | Details |
|--------|---------|
| **Actor** | HR Admin / System Admin |
| **What They Do** | Assigns configured shifts to employees (individually, by department, or position). Updates shift statuses (Approved, Cancelled, Expired). |
| **Why It Matters** | Instead of manually assigning each person's schedule, you can assign all department heads to morning shifts, or all warehouse workers to rotating shifts with one command. The system tracks if assignments are approved, cancelled, or expired. |
| **Supporting Requirements** | **US-1** (User Story 1): As a System Admin/HR Admin, I want to assign shifts to employees (individually, by department, or by position) and manage their statuses so that work schedules are properly maintained and updated. |
| **What Gets Created** | Employee schedules generated; valid shift assignments created for attendance validation. |
| **Related Business Rules** | **BR-TM-02**: Shifts must be assigned per employee for a defined term and hold statuses (Approved, Cancelled, Entered, Expired, Postponed, Rejected, Submitted). **BR-TM-03**: The system must support multiple shift types (Normal, Split, Overnight, Mission, Rotational) with start and end dates. **BR-TM-04**: The system must support multiple shift names (Fixed Core Hours, Flex-Time, Rotational, Split, Custom Weekly Patterns, Overtime). **BR-TM-05**: Shift schedules must be assignable by Department, Position, or Individual. |
| **Inputs Needed** | Employee Profile (who works where), Organizational Structure (department hierarchy) |
| **Outputs To** | Time Management system (uses these assignments to validate attendance later) |

---

### STEP 3: Define Custom Scheduling Rules

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Sets custom scheduling logic such as flexible hours, rotational work weeks, or compressed patterns (4-on/3-off). |
| **Why It Matters** | Modern workplaces need flexibility. Some employees work 9-5 fixed hours, others might work 7am-4pm one week and 3pm-midnight the next, or work 4 ten-hour days then get 3 days off. This step lets the system handle all these variations. |
| **Supporting Requirements** | **US-3** (User Story 3): As an HR Manager, I want to define flexible and custom scheduling rules (e.g., flex-in/flex-out hours, custom weekly patterns like 4 days on/3 off) so that the organization can accommodate diverse work styles. |
| **What Gets Created** | Scheduling flexibility applied; outputs feed into attendance validation logic. |
| **Related Business Rules** | **BR-TM-04**: The system must support multiple shift names (Fixed Core Hours, Flex-Time, Rotational, Split, Custom Weekly Patterns, Overtime). **BR-TM-10**: The system must restrict early/late clock-ins based on configured shifts and rules. |

---

### STEP 4: Shift Expiry Notification & Renewal

| Aspect | Details |
|--------|---------|
| **Actor** | System / HR Admin |
| **What They Do** | Sends notifications when a shift assignment nears expiry, prompting renewal or reassignment. |
| **Why It Matters** | If you forget that an employee's schedule expires next month, they could suddenly have no assigned shift. This automatic reminder prevents that—HR gets notified 30 days before expiry so they can renew or change it. |
| **Supporting Requirements** | **US-4** (User Story 4): As an HR Admin, I want to be notified when a shift assignment is nearing expiry so that schedules can be renewed or reassigned. |
| **What Gets Created** | Alerts generated for HR; expiring shifts either renewed or archived. |
| **Related Business Rules** | **BR-TM-02**: Shifts must be assigned per employee and can hold "Expired" status. **BR-TM-05**: Shift schedules must be maintained. |
| **Outputs To** | Notifications system (sends the alert) |

---

# PHASE 2: ATTENDANCE RECORDING AND VALIDATION

## 📋 Phase Description

**During daily operations, each Employee records attendance through clock-in and clock-out actions validated against their assigned shift and rest-day schedule. The system ensures that punches align with scheduled times and automatically generates attendance logs. In cases of missing or invalid punches, the Line Manager (Head of Department) performs manual corrections to maintain data integrity. The System Administrator also configures rules for flexible punch handling, defining whether multiple punches per day are allowed or whether only the first-in/last-out pattern applies. Missed punch alerts are automatically sent to both employees and managers to prompt timely corrections.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Now that shifts are defined and assigned, employees come to work. This phase:
- Records when they arrive (clock in) and leave (clock out)
- Makes sure their clocking times match their assigned shift
- Fixes any mistakes (missed punches, late entries)
- Handles employees who take breaks or multiple punch pairs per day
- Alerts people if they forgot to clock in or out

---

### STEP 5: Employee Clock-In / Clock-Out

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Clocks in/out using ID validating against assigned shifts and rest days. |
| **Why It Matters** | This is the core data collection point. Employees record when they arrived and left. The system validates: "Is this person assigned to work today? Is their clock-in time within their shift window?" This prevents fake punches or employees clocking in at wrong times. |
| **Supporting Requirements** | **US-5** (User Story 5): As an Employee, I want to clock in/out using ID so that my attendance is recorded accurately and timestamped. |
| **What Gets Created** | Attendance records created and timestamped; data logged for validation. |
| **Related Business Rules** | **BR-TM-06**: Time-in/out must be captured via Biometric, Web Login, Mobile App (GPS optional), or Manual Input (with audit trail). **BR-TM-12**: Clock-ins must be tagged with location, terminal ID, or device. **BR-TM-13**: Attendance devices must sync automatically once reconnected online. |
| **Capture Methods** | Multiple options: Fingerprint scanner, website login, mobile app, or manual entry by manager |
| **Inputs Needed** | External Excel Sheet (employee data, shift information) |
| **Outputs To** | Time Management system (creates records for all downstream processing) |

---

### STEP 6: Manual Attendance Correction

| Aspect | Details |
|--------|---------|
| **Actor** | Line Manager |
| **What They Do** | Reviews and corrects attendance in case of missing or invalid punches. |
| **Why It Matters** | Not every situation is perfect. Biometric system down? Employee forgot their badge? Worked from home but couldn't log in? Managers need the ability to manually add or fix attendance records. The system tracks every change so auditors can see what was changed and by whom. |
| **Supporting Requirements** | **US-6** (User Story 6): As a Line Manager, I want to record or correct attendance manually so that missing punches can be updated accurately. |
| **What Gets Created** | Corrected attendance record stored; audit log updated. |
| **Related Business Rules** | **BR-TM-06**: Time-in/out can be captured via Manual Input with audit trail. **BR-TM-24**: All edits/changes/cancellations must be timestamped and audit-tracked. |
| **Inputs Needed** | Organizational Structure (manager-employee relationships) |
| **Outputs To** | Time Management system (corrected records) |

---

### STEP 7: Flexible Punch Handling

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin / Employee |
| **What They Do** | Enables or restricts multiple punches per day (e.g., first-in/last-out vs. multiple). |
| **Why It Matters** | Some jobs need one clock-in/out pair per day. Others (field workers, people with breaks) need multiple. Example: An employee clocks in at 8am, clocks out for lunch at 12pm, clocks back in at 1pm, clocks out at 5pm. System needs to know how to handle these multiple punches. Does it add all time? Use first-in/last-out only? The admin configures this. |
| **Supporting Requirements** | **US-7** (User Story 7): As an Employee/System Admin, I want to support multiple clock-ins/outs per day or restrict to first-in/last-out, so that the system adapts to different work styles. |
| **What Gets Created** | Punch validation logic applied; affects attendance data calculations. |
| **Related Business Rules** | **BR-TM-11**: The system must allow multiple punches per day, or alternatively use first in/last out. **BR-TM-07**: Attendance data must follow HR rounding rules (nearest interval, ceiling/floor, alignment, first in/last out). |

---

### STEP 8: Missed Punch Management & Alerts

| Aspect | Details |
|--------|---------|
| **Actor** | Employee / Line Manager |
| **What They Do** | Flags missed punches and sends automated alerts to employees and managers for correction. |
| **Why It Matters** | If someone forgot to clock in or out, payroll might get incorrect data. The system automatically detects this: "Employee was supposed to work today but didn't clock in." It alerts both the employee ("Hey, did you forget to clock in?") and the manager ("Your employee never clocked in.") so it can be fixed immediately. |
| **Supporting Requirements** | **US-8** (User Story 8): As an Employee/Line Manager/Payroll Officer, I want the system to flag missed punches and send alerts so that corrections are made promptly. |
| **What Gets Created** | Notification records sent; pending corrections logged in system. |
| **Related Business Rules** | **BR-TM-14**: Missed punches/late sign-ins must be handled via auto-flagging, notifications, or payroll blocking. |
| **Outputs To** | Notifications system (sends alerts), Payroll system (may block processing) |

---

# PHASE 3: POLICY AND RULE ENFORCEMENT

## 📋 Phase Description

**The HR Manager configures policies for overtime, short time, and weekend work, including approval requirements and calculation logic. Lateness rules are also defined—specifying thresholds, grace periods, and penalties that the system applies automatically. Repeated lateness is monitored by the HR Administrator or Manager, allowing disciplinary actions or escalation when thresholds are exceeded. Employees may submit attendance correction requests when discrepancies occur, which follow a structured approval workflow to ensure transparency and traceability.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Now that we have attendance data, this phase applies the company's rules:
- How much overtime is allowed?
- What if someone is late? (5 min grace period? 15 min deduction?)
- Weekend rates different from weekday?
- What if someone is repeatedly late? (warning, discipline, etc.)
- Can employees request corrections to their punches?

---

### STEP 9: Overtime & Short Time Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Configures overtime, short-time, and weekend work rules, including approval requirements and calculation logic. |
| **Why It Matters** | Every company has different overtime rules. Some pay 1.5x for hours over 8, others pay 2x for overtime. Weekends might be double pay or regular. Night shift might get a bonus. The system needs to know these rules to calculate correctly. |
| **Supporting Requirements** | **US-10** (User Story 10): As an HR Manager, I want to configure overtime and short-time rules (including weekend, holiday, and pre-approval types) so that attendance and payroll comply with policies. |
| **What Gets Created** | Overtime policies defined; stored for payroll and approval workflow. |
| **Related Business Rules** | **BR-TM-08**: Overtime/Short Time must be calculated according to organizational policies (types, categories, implementation rules, calculation methods). **BR-TM-16**: Permission policies must define types of Over/Short time (Early In, Late Out, Out of Hours, Total). |
| **Inputs Needed** | None (policy establishment) |
| **Outputs To** | Time Management system (uses rules for calculations) |

---

### STEP 10: Lateness & Penalty Rules Setup

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Sets lateness thresholds, grace periods, and automatic penalty triggers. |
| **Why It Matters** | A 2-minute delay shouldn't hurt as much as a 30-minute delay. Companies set grace periods (5 mins late = OK, 6+ mins = penalty). They also set thresholds for escalation (1 late = warning, 3 lates = disciplinary action). The system automatically applies these consistently to everyone. |
| **Supporting Requirements** | **US-11** (User Story 11): As an HR Manager, I want to set grace periods, lateness thresholds, and automatic deductions so that penalties are applied fairly and consistently. |
| **What Gets Created** | Lateness configurations active; real-time penalty calculations enabled. |
| **Related Business Rules** | **BR-TM-09**: Early/Lateness per shift must follow HR rules (grace period, penalty thresholds, escalation). **BR-TM-10**: The system must restrict early/late clock-ins based on configured shifts and rules. |

---

### STEP 11: Repeated Lateness Handling

| Aspect | Details |
|--------|---------|
| **Actor** | HR Admin / Manager System |
| **What They Do** | Flags repeated lateness for disciplinary tracking and escalation. |
| **Why It Matters** | If someone is 5 minutes late once—OK. If it's a pattern (late 20 times in a month), that's a problem needing discipline. The system tracks this and raises flags automatically. HR can then take action (warnings, training, etc.). |
| **Supporting Requirements** | **US-12** (User Story 12): As an HR Admin/Manager, I want the system to flag repeated lateness for disciplinary tracking so that repeated offenders can be identified. |
| **What Gets Created** | Escalate after threshold reached. Disciplinary flags; performance reports updated. |
| **Related Business Rules** | **BR-TM-09**: Early/Lateness must follow HR rules with escalation. **BR-TM-16**: Permission policies must define types of Over/Short time (Early In, Late Out, Out of Hours, Total). |
| **Outputs To** | Performance Management system (disciplinary records) |

---

### STEP 12: Attendance Correction Requests

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Submits correction requests for missing or incorrect punches and tracks their approval status. |
| **Why It Matters** | An employee might notice their punch data is wrong and needs to request a fix. They can't just change it themselves—a manager must approve it. This keeps the system trustworthy (everything has approval trails). |
| **Supporting Requirements** | **US-13** (User Story 13): As an Employee, I want to submit correction requests for missing or incorrect punches and track their approval status so that I maintain accurate records. |
| **What Gets Created** | Correction request generated; pending approval workflow initiated. |
| **Related Business Rules** | **BR-TM-15**: Employees must be able to submit correction requests (reason + time) via ESS, routed to Line Manager for approval. |
| **Inputs Needed** | Time Management (current attendance records) |
| **Outputs To** | Time Management (corrected records upon approval) |

---

# PHASE 4: EXCEPTION HANDLING AND WORKFLOW APPROVALS

## 📋 Phase Description

**All time-related exceptions—such as corrections, permissions, or overtime requests—are reviewed by the Line Manager or HR Administrator. The workflow supports approvals, rejections, or automatic escalation if pending beyond defined deadlines. This phase ensures that only validated and approved time data proceeds to payroll processing. Additionally, the System Administrator or HR Admin defines holiday calendars and weekly rest days, which are integrated with attendance logic to avoid false lateness or penalty triggers. The HR Manager links employee vacation packages to attendance schedules to reflect leave automatically and maintain synchronized time-off records.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Before data goes to payroll, it needs approval. This phase:
- Reviews all exceptions and corrections
- Approves or rejects them
- Automatically escalates if they're not reviewed in time
- Sets up holiday/vacation calendars so people don't get penalized for legitimate time off
- Links vacation days to attendance so they're automatically accounted for

---

### STEP 13: Time Exception Approval Workflow

| Aspect | Details |
|--------|---------|
| **Actor** | Line Manager / HR Admin |
| **What They Do** | Reviews, approves, or rejects time-related requests (corrections, overtime, permissions). Escalates unreviewed ones automatically. |
| **Why It Matters** | Not everything gets auto-approved. Overtime, shift changes, correction requests—these need human review. A manager reviews and decides: "Does this make sense? Do I approve this change?" If no one reviews it in time, the system escalates it (bumps it up to HR leadership) so payroll doesn't get blocked. |
| **Supporting Requirements** | **US-14** (User Story 14): As a Line Manager/HR Admin, I want to review, approve, or reject attendance-related requests (corrections, overtime, permissions) and escalate unresolved ones automatically after deadlines. |
| **What Gets Created** | Approved or rejected requests finalized; audit trail maintained. |
| **Related Business Rules** | **BR-TM-01**: Roles for time management must be defined by the System Admin. Line Managers and HR approve or reject time management permissions. **BR-TM-15**: Employees must be able to submit correction requests via ESS, routed to Line Manager for approval. **BR-TM-18**: Over/Short time permissions can be Accepted or Rejected, impacting payroll and benefits. **BR-TM-20**: Unreviewed employee requests must auto-escalate after a defined time or before payroll cutoff. |
| **Inputs Needed** | Time Management (exception requests) |
| **Outputs To** | Time Management (validated approvals feed to payroll), Notifications (escalation alerts) |

---

### STEP 14: Holiday & Rest Day Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin / HR Admin |
| **What They Do** | Defines national holidays, organizational holidays, and weekly rest days to suppress penalties. |
| **Why It Matters** | If someone is scheduled for Sunday (normally a rest day) but doesn't clock in, they shouldn't get a "missed punch" penalty. If it's Christmas (a holiday) and they don't work, no penalty. The system needs to know what days are holidays/rest days so it doesn't incorrectly flag people. |
| **Supporting Requirements** | **US-17** (User Story 17): As a System Admin/HR Admin, I want to define national holidays, organizational holidays, and weekly rest days so that no shifts or attendance penalties are applied during those times. |
| **What Gets Created** | Holiday master list created; integrated into shift and attendance checks. |
| **Related Business Rules** | **BR-TM-19**: Vacation packages, national holidays, organizational holidays, and weekly rest days must be linked to shift schedules. |
| **Inputs Needed** | Leaves Module (may contain holiday definitions) |
| **Outputs To** | Time Management (uses definitions for penalty suppression) |

---

### STEP 15: Vacation Package Integration

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Links employee vacation entitlements to attendance schedules for automatic reflection of time off. |
| **Why It Matters** | If an employee has approved vacation from June 1-10, the system should automatically know: "This person isn't supposed to be working then. Don't flag them for missed punches." This prevents false penalties during legitimate time off and keeps leave/attendance synchronized. |
| **Supporting Requirements** | **US-16** (User Story 16): As an HR Manager, I want employee vacation packages linked to their schedules so that time off is automatically reflected in attendance and planning. |
| **What Gets Created** | Attendance and leave data unified; leave deductions auto-calculated. |
| **Related Business Rules** | **BR-TM-19**: Vacation packages must be linked to shift schedules. |
| **Inputs Needed** | Leaves Module (employee leave allocations and approvals) |
| **Outputs To** | Time Management (integrated leave/attendance records) |

---

### STEP 16: Escalation for Pending Requests Before Payroll Cut-Off

| Aspect | Details |
|--------|---------|
| **Actor** | System / HR Admin |
| **What They Do** | Automatically escalates any pending requests (corrections, permissions, approvals) before payroll finalization. |
| **Why It Matters** | Payroll can't run if there are still pending approvals. The system knows payroll closes on the 25th. On the 23rd, it automatically escalates any unapproved requests so they get handled before payroll runs. This prevents delays. |
| **Supporting Requirements** | **US-18** (User Story 18): As a System Admin/HR Admin, I want leave or time requests to escalate automatically if not reviewed before the monthly payroll cut-off date so that payroll processing is not delayed. |
| **What Gets Created** | Escalation alerts sent; ensures clean payroll closure. |
| **Related Business Rules** | **BR-TM-20**: Unreviewed employee requests must auto-escalate after a defined time or before payroll cutoff. |
| **Inputs Needed** | Payroll (cut-off date information), Time Management (pending requests) |
| **Outputs To** | Notifications (escalation alerts) |

---

# PHASE 5: INTEGRATION, REPORTING, AND PAYROLL CLOSURE

## 📋 Phase Description

**Once attendance and exceptions are validated, the System or HR Administrator synchronizes all relevant data—attendance, overtime, and penalties—with the payroll and leave management systems. This daily integration ensures that payroll runs use only accurate and approved data. The HR Officer or Payroll Officer generates detailed reports on overtime, exceptions, and penalties for review, auditing, and compliance. Before payroll closure, the system automatically escalates any pending time-related approvals to ensure that all records are finalized. This guarantees accurate and complete payroll processing, closing the time management cycle for the period.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

All the attendance data is now complete and approved. This phase:
- Sends all validated data to the payroll system so it can calculate paychecks
- Generates reports for review and auditing
- Makes final escalation checks before payroll closes
- Ensures the payroll system has clean, complete, approved data

---

### STEP 17: Payroll Synchronization

| Aspect | Details |
|--------|---------|
| **Actor** | System / HR Admin |
| **What They Do** | Syncs attendance, overtime, and penalty data with payroll and leave systems daily. |
| **Why It Matters** | Payroll needs accurate attendance data to calculate paychecks. If attendance data is wrong, paychecks are wrong. Daily sync ensures payroll always has the latest, most accurate data. If someone worked 10 hours (2 hours overtime) at 1.5x pay, payroll needs to know that. |
| **Supporting Requirements** | **US-20** (User Story 20): As an HR Manager, I want attendance and time management data synchronized with payroll and leave modules to maintain consistent records. |
| **What Gets Created** | Payroll system updated with validated time data. |
| **Related Business Rules** | **BR-TM-22**: All time management data must sync daily with payroll, benefits, and leave modules. |
| **Outputs To** | Payroll (uses synchronized data for calculations), Leaves (uses synchronized data for balance tracking) |

---

### STEP 18: Reporting & Analytics Generation

| Aspect | Details |
|--------|---------|
| **Actor** | HR Officer / Payroll Officer |
| **What They Do** | Generates overtime, exception, and penalty reports for review and auditing. |
| **Why It Matters** | Need to verify: "Did we pay overtime correctly? Did anyone get penalized unfairly? Are there patterns (like certain departments always working overtime)?" Reports let HR review and audit all the decisions the system made. |
| **Supporting Requirements** | **US-19** (User Story 19): As an HR or Payroll Officer, I want to view and export overtime and exception attendance reports so that payroll and compliance checks are accurate. |
| **What Gets Created** | Exportable reports and analytics dashboards generated. |
| **Related Business Rules** | **BR-TM-21**: HR and Line Managers must have access to attendance summaries, lateness logs, and overtime reports. **BR-TM-23**: Reports must be exportable in multiple formats (Excel, Access, Text). |
| **Inputs Needed** | Time Management (attendance, overtime, exception data) |
| **Outputs To** | Analytics / Payroll (reports feed into analysis and processing) |

---

### STEP 19: Final Escalation Before Payroll Closure

| Aspect | Details |
|--------|---------|
| **Actor** | System / HR Admin |
| **What They Do** | Automatically escalates any remaining pending time-related approvals to ensure all records are finalized. |
| **Why It Matters** | Final safety check. Before payroll actually closes and runs, the system does one last check: "Are there any approvals still pending? If yes, escalate them NOW so nothing gets missed." |
| **Supporting Requirements** | **US-18** (User Story 18): As a System Admin/HR Admin, I want leave or time requests to escalate automatically if not reviewed before the monthly payroll cut-off date so that payroll processing is not delayed. |
| **What Gets Created** | Escalation alerts sent; ensures clean payroll closure. |
| **Related Business Rules** | **BR-TM-20**: Unreviewed employee requests must auto-escalate before payroll cutoff. |

---

# 📋 COMPLETE BUSINESS RULES REFERENCE TABLE

This section contains ALL 25 Business Rules for the Time Management Subsystem with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-TM-01** | Roles for time management must be defined by the System Admin. Line Managers and HR approve or reject time management permissions. |
| **BR-TM-02** | Shifts must be assigned per employee for a defined term and hold statuses (Approved, Cancelled, Entered, Expired, Postponed, Rejected, Submitted). |
| **BR-TM-03** | The system must support multiple shift types (Normal, Split, Overnight, Mission, Rotational) with start and end dates. |
| **BR-TM-04** | The system must support multiple shift names (Fixed Core Hours, Flex-Time, Rotational, Split, Custom Weekly Patterns, Overtime). |
| **BR-TM-05** | Shift schedules must be assignable by Department, Position, or Individual. |
| **BR-TM-06** | Time-in/out must be captured via Biometric, Web Login, Mobile App (GPS optional), or Manual Input (with audit trail). |
| **BR-TM-07** | Attendance data must follow HR rounding rules (nearest interval, ceiling/floor, alignment, first in/last out). |
| **BR-TM-08** | Overtime/Short Time must be calculated according to organizational policies (types, categories, implementation rules, calculation methods). |
| **BR-TM-09** | Early/Lateness per shift must follow HR rules (grace period, penalty thresholds, escalation). |
| **BR-TM-10** | The system must restrict early/late clock-ins based on configured shifts and rules. |
| **BR-TM-11** | The system must allow multiple punches per day, or alternatively use first in/last out. |
| **BR-TM-12** | Clock-ins must be tagged with location, terminal ID, or device. |
| **BR-TM-13** | Attendance devices must sync automatically once reconnected online. |
| **BR-TM-14** | Missed punches/late sign-ins must be handled via auto-flagging, notifications, or payroll blocking. |
| **BR-TM-15** | Employees must be able to submit correction requests (reason + time) via ESS, routed to Line Manager for approval. |
| **BR-TM-16** | Permission policies must define types of Over/Short time (Early In, Late Out, Out of Hours, Total). |
| **BR-TM-17** | Permissions must be tied to valid dates (contract start, financial calendar, probation date). |
| **BR-TM-18** | Over/Short time permissions can be Accepted or Rejected, impacting payroll and benefits. |
| **BR-TM-19** | Vacation packages, national holidays, organizational holidays, and weekly rest days must be linked to shift schedules. |
| **BR-TM-20** | Unreviewed employee requests must auto-escalate after a defined time or before payroll cutoff. |
| **BR-TM-21** | HR and Line Managers must have access to attendance summaries, lateness logs, and overtime reports. |
| **BR-TM-22** | All time management data must sync daily with payroll, benefits, and leave modules. |
| **BR-TM-23** | Reports must be exportable in multiple formats (Excel, Access, Text). |
| **BR-TM-24** | All edits/changes/cancellations must be timestamped and audit-tracked. |
| **BR-TM-25** | The system must maintain continuous data backup with a retention policy. |

---

# 📊 ALL USER STORIES (US-1 through US-20)

### US-1: Shift Assignment Management
**What User Needs:** "As a System Admin/HR Admin, I want to assign shifts to employees (individually, by department, or by position) and manage their statuses so that work schedules are properly maintained and updated."

**Why It Matters:** Instead of assigning 1,000 employees individually (weeks of work), bulk assign by department in minutes.

**Related BRs:** BR-TM-02, BR-TM-05

**System Must Support:**
- Individual assignment (pick one person)
- Department bulk assign (all people in Sales get evening shift)
- Position bulk assign (all "Supervisors" get day shift)
- Status tracking: Approved, Cancelled, Entered, Expired, Postponed, Rejected, Submitted

---

### US-2: Shift Configuration and Types
**What User Needs:** "As an HR Manager/System Admin, I want to define and configure shift types (Normal, Split, Overnight, Rotational, etc.) and their corresponding names so that different work arrangements are supported consistently."

**Why It Matters:** Establishes organizational standards so everyone means the same thing by "Night Shift."

**Related BRs:** BR-TM-03, BR-TM-04

**System Must Support:**
- Create shift types: Normal, Split, Overnight, Mission, Rotational
- Create shift names: Fixed Core Hours, Flex-Time, Rotational, Split, Custom Weekly Patterns, Overtime
- Each with associated rules

---

### US-3: Custom Scheduling Rules
**What User Needs:** "As an HR Manager, I want to define flexible and custom scheduling rules (e.g., flex-in/flex-out hours, custom weekly patterns like 4 days on/3 off) so that the organization can accommodate diverse work styles."

**Why It Matters:** Modern workplaces need flexibility to compete for talent.

**Related BRs:** BR-TM-04, BR-TM-10

**System Must Support:**
- Flexible work hour windows (clock in 7-10am)
- Custom weekly patterns (4-on/3-off)
- Compressed workweeks

---

### US-4: Shift Expiry Notifications
**What User Needs:** "As an HR Admin, I want to be notified when a shift assignment is nearing expiry so that schedules can be renewed or reassigned."

**Why It Matters:** Prevents scheduling gaps from forgetting to renew shifts.

**Related BRs:** BR-TM-02, BR-TM-05

**System Must Support:**
- Auto-detect expiring shifts
- Send alerts to HR and managers
- Allow manual renewal or reassignment

---

### US-5: Employee Clock-In/Clock-Out
**What User Needs:** "As an Employee, I want to clock in/out using ID so that my attendance is recorded accurately and timestamped."

**Why It Matters:** Core data collection point for payroll.

**Related BRs:** BR-TM-06

**System Must Support:**
- Multiple channels (biometric, web, mobile)
- Validation against shift
- Prevent clock-in before shift or after shift ends
- Timestamp and device tagging

---

### US-6: Manual Attendance Correction
**What User Needs:** "As a Line Manager, I want to record or correct attendance manually so that missing punches can be updated accurately."

**Why It Matters:** Handles edge cases (system down, employee worked from home, etc.).

**Related BRs:** BR-TM-06, BR-TM-24

**System Must Support:**
- Manager can add/modify attendance
- All entries require reason
- Audit trail shows original vs. corrected
- Records flagged for payroll review

---

### US-7: Flexible Punch Handling
**What User Needs:** "As an Employee/System Admin, I want to support multiple clock-ins/outs per day or restrict to first-in/last-out, so that the system adapts to different work styles."

**Why It Matters:** Some roles need multiple punches (field workers), others don't (office workers).

**Related BRs:** BR-TM-11

**System Must Support:**
- Configuration: Multiple punches OR first-in/last-out
- Apply rounding rules to each punch pair
- Communicate rules to employees

---

### US-8: Missed Punch Management
**What User Needs:** "As an Employee/Line Manager/Payroll Officer, I want the system to flag missed punches and send alerts so that corrections are made promptly."

**Why It Matters:** Quick detection prevents payroll errors.

**Related BRs:** BR-TM-14

**System Must Support:**
- Auto-detect missing clock-in/out
- Flag in system
- Send notifications to employee and manager
- Prevent payroll processing until fixed

---

### US-9: Overtime & Short Time Configuration
**What User Needs:** "As an HR Manager, I want to configure overtime and short-time rules (including weekend, holiday, and pre-approval types) so that attendance and payroll comply with policies."

**Why It Matters:** Every company has different rules; system must be configurable.

**Related BRs:** BR-TM-08, BR-TM-16

**System Must Support:**
- Define overtime policy (thresholds, rates, caps)
- Define short-time policy
- Different rules for weekends/holidays
- Pre-approval requirements

---

### US-10: Lateness & Penalty Rules
**What User Needs:** "As an HR Manager, I want to set grace periods, lateness thresholds, and automatic deductions so that penalties are applied fairly and consistently."

**Why It Matters:** Fair, consistent rules prevent disputes.

**Related BRs:** BR-TM-09, BR-TM-10

**System Must Support:**
- Configure grace period (e.g., 5 min allowed)
- Penalty types (salary deduction, mark, discipline)
- Escalation thresholds (e.g., 3 lates = warning)
- Auto-apply penalties consistently

---

### US-11: Repeated Lateness Handling
**What User Needs:** "As an HR Admin/Manager, I want the system to flag repeated lateness for disciplinary tracking so that repeated offenders can be identified."

**Why It Matters:** Repeated offenses need escalated action.

**Related BRs:** BR-TM-09, BR-TM-16

**System Must Support:**
- Track lateness instances
- Auto-escalate at thresholds
- Generate reports of repeat offenders
- Link to performance management

---

### US-12: Attendance Correction Requests
**What User Needs:** "As an Employee, I want to submit correction requests for missing or incorrect punches and track their approval status so that I maintain accurate records."

**Why It Matters:** Gives employees a formal channel to fix errors they notice.

**Related BRs:** BR-TM-15

**System Must Support:**
- Employee self-service portal for requests
- Include date, time, reason
- Route to line manager
- Employee can view status and comments
- Request history audit trail

---

### US-13: Time Exception Approval Workflow
**What User Needs:** "As a Line Manager/HR Admin, I want to review, approve, or reject attendance-related requests (corrections, overtime, permissions) and escalate unresolved ones automatically after deadlines."

**Why It Matters:** Centralized approval creates consistency and audit trail.

**Related BRs:** BR-TM-01, BR-TM-15, BR-TM-20

**System Must Support:**
- Dashboard of pending approvals
- Review details and supporting info
- Approve, reject, or request info
- Auto-escalate if unreviewed after X days
- Log all decisions with timestamp/reason

---

### US-14: Holiday & Rest Day Configuration
**What User Needs:** "As a System Admin/HR Admin, I want to define national holidays, organizational holidays, and weekly rest days so that no shifts or attendance penalties are applied during those times."

**Why It Matters:** Prevents false penalties for legitimate time off.

**Related BRs:** BR-TM-19

**System Must Support:**
- Define national holidays
- Define organizational holidays
- Configure weekly rest days (typically weekends)
- Suppress penalties on these days
- Consider holidays in overtime calculations

---

### US-15: Vacation Package Integration
**What User Needs:** "As an HR Manager, I want employee vacation packages linked to their schedules so that time off is automatically reflected in attendance and planning."

**Why It Matters:** Prevents false penalties during approved leave.

**Related BRs:** BR-TM-19

**System Must Support:**
- Retrieve approved leave from leave system
- Auto-suppress attendance expectations during leave
- No missed punch flags during vacation
- Reflect leave in reports
- Auto-deduct from leave balance

---

### US-16: Escalation for Pending Requests Before Payroll Cut-Off
**What User Needs:** "As a System Admin/HR Admin, I want leave or time requests to escalate automatically if not reviewed before the monthly payroll cut-off date so that payroll processing is not delayed."

**Why It Matters:** Payroll can't run with pending approvals.

**Related BRs:** BR-TM-20

**System Must Support:**
- Know payroll cut-off dates
- Calculate escalation trigger dates
- Auto-escalate on trigger date
- Send urgent notifications
- Report all escalations

---

### US-17: Overtime & Exception Reports
**What User Needs:** "As an HR or Payroll Officer, I want to view and export overtime and exception attendance reports so that payroll and compliance checks are accurate."

**Why It Matters:** Enables verification and auditing.

**Related BRs:** BR-TM-21, BR-TM-23

**System Must Support:**
- Pre-built reports (overtime, lateness, exceptions)
- Filter by date, department, employee, type
- Include summary stats and details
- Export in Excel, Access, Text

---

### US-18: Cross-Module Data Synchronization
**What User Needs:** "As an HR Manager, I want attendance and time management data synchronized with payroll and leave modules to maintain consistent records."

**Why It Matters:** Single source of truth across systems.

**Related BRs:** BR-TM-22

**System Must Support:**
- Daily sync with payroll
- Daily sync with leave module
- Prevent processing until sync complete
- Log all exchanges and errors
- Handle conflicts and retries

---

### US-19: Permission Validation Rules
**What User Needs:** "As an HR Admin, I want to define limits for permission durations and ensure only approved permissions affect payroll."

**Why It Matters:** Controls which exceptions get paid.

**Related BRs:** BR-TM-16, BR-TM-18

**System Must Support:**
- Define permission duration limits
- Only approved permissions impact payroll
- Rejected permissions don't affect calculations
- Link to valid employment dates

---

### US-20: Attendance-to-Payroll Sync
**What User Needs:** "As an HR Admin, I want attendance records to sync daily with payroll and leave systems so that data remains consistent."

**Why It Matters:** Ensures payroll has accurate data.

**Related BRs:** BR-TM-22

**System Must Support:**
- Daily sync of all attendance data
- Timestamp all sync operations
- Alert on sync failures
- Maintain sync audit trail

---

---

**End of Time Management Subsystem Documentation**

✅ **All 5 Phases Documented Sequentially**
✅ **All 19 Workflow Steps in Order**
✅ **All 25 Business Rules Included**
✅ **All 20 User Stories with Full Context**
✅ **Professional Structure & Non-Technical Language**
✅ **Ready for Implementation & Audit**

