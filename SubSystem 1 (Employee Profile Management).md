# EMPLOYEE PROFILE MANAGEMENT SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** This subsystem serves as the central repository for all employee-related information within the Human Resource Management System. It maintains accurate, secure, and up-to-date employee master data, acting as the foundation upon which other HR subsystems—such as Payroll, Performance, Time Management, and Organizational Structure—rely.

### 🎯 What Does This Subsystem Do? (Simple Explanation)

Think of this subsystem as the employee data hub. It handles:
- **Self-service profile access** - employees securely view their complete profiles including personal, employment, and performance data
- **Profile updates** - employees make immediate non-critical updates (phone, email, address, profile picture)
- **Correction requests** - employees formally request changes to HR-governed data (name, position, department, marital status)
- **Manager insights** - department managers see non-sensitive summaries of their team members
- **HR master data management** - HR administrators review and approve change requests, manage data integrity, and sync updates across systems
- **Data traceability** - all changes are logged with timestamps and user IDs for audit compliance
- **Privacy enforcement** - role-based access controls ensure sensitive data is protected

Instead of employees contacting HR for every profile question or update, this subsystem provides self-service access while maintaining strict data governance and multi-level approvals for critical changes.

---

## 📊 EMPLOYEE PROFILE FLOW

**This module manages how employee profile data is viewed, updated, requested for change, and governed through approvals. It moves from employee self-service access, through manager insight, to HR/System Admin control.**

### 🔍 What This Process Does (Simplified)

This is a 3-phase lifecycle that:
1. Employees securely access and update their own profiles, submit formal change requests
2. Department managers see team-member summaries with privacy restrictions
3. HR reviews, approves, and applies changes to master data with downstream system synchronization

Each phase builds on the previous to create employee empowerment with organizational oversight.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must securely store and display employee profile information"

**Why it matters:** Requirements define what functionality the system needs to provide.

---

### 👤 USER STORIES (US)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As an Employee, I want to view my full employee profile so that I can verify all my personal and employment information."

**Real-World Translation:** Sarah logs into the system and sees her complete profile with all personal details, employment information, department, pay grade, and performance history.

**Why it matters:** 
- Makes requirements human-centered (focuses on actual user needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Can Sarah successfully view her profile?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-20a: Only authorized roles can modify profile data."

**Real-World Translation:** "The system must prevent unauthorized users from changing employee data. Only HR administrators and the employee themselves (for non-critical fields) can make changes."

**Why it matters:**
- Defines exact logic developers must code
- Ensures consistency (all profile changes follow same rules)
- Creates auditability (who changed what, when)
- Links to legal/compliance requirements

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works.

**Example:**
```
Employee logs into portal
  → Views complete profile
  → Updates phone number
  → Request formal name change
  → HR reviews request
  → HR approves change
  → Profile updated across all systems
```

**Real-World Translation:** The complete process an employee goes through to access and manage their profile information.

**Why it matters:**
- Shows sequence of operations (order matters)
- Helps everyone understand the big picture
- Identifies where things can fail
- Makes testing easier

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
| **US-E2-04 (User Story)** | "As an Employee, I want to view my full employee profile." |
| **BR-2a-r (Business Rule)** | "System must record specific personal and job data with secure access." |
| **FLOW (Process)** | (1) Employee logs in, (2) Authenticated, (3) Profile displayed with all components |
| **IMPLEMENTATION** | Developer codes: "Load profile data. Apply role-based access controls. Display components securely." |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what users actually need
2. **Business Rules** ensure every organizational rule is enforced consistently
3. **Flows** ensure everything happens in the right order with proper controls
4. **Together** they create a complete, secure, auditable employee profile system

---

---

# PHASE 1: EMPLOYEE SELF-SERVICE ACCESS & UPDATES

## 📋 Phase Description

**Employees securely view their profiles, make immediate non-critical updates (e.g., phone, email, photo), and submit formal correction requests for governed fields.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Employee self-service access and updates:
- View complete profile with all personal and employment data
- See performance appraisal history
- Update contact information immediately
- Upload profile picture
- Submit formal requests for critical data changes
- Receive notifications about profile updates

All actions are logged for traceability and compliance.

---

### STEP 1: View Personal Profile (Self-Service)

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Securely access and view their complete employee profile including personal details, employment information, position, department, pay grade, and appraisal history. |
| **Why It Matters** | Employees can verify their information is accurate and understand their employment status. |
| **Supporting Requirements** | **US-E2-04**: As an employee, I want to view my full employee profile. |
| **What Gets Created** | Displayed employee profile with all components (Name, ID, Status, Pay Grade, Department, Position, Appraisals, etc.). |
| **Related Business Rules** | **BR 2a-r**: System must record specific personal and job data. **BR-14**: Authentication and secure access controls required. **NFR-14**: All users authenticate via secure login and role-based access control. |
| **Inputs Needed** | Performance Module (Appraisal history), Organizational Structure (Position and Department data) |
| **System Integration** | Data retrieval from Performance module for appraisal history, Organizational Structure for position/department context |

---

### STEP 2: Update Self-Service Data (Immediate Update)

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Directly modify and save non-critical profile data points such as profile picture, phone number, email address, and home address. |
| **Why It Matters** | Employees can keep their contact information current without HR intervention, improving communication and emergency contact accuracy. |
| **Supporting Requirements** | **US-E2-12**: As an employee, I want to add a short biography and upload a profile picture. **US-E2-05**: As an employee, I want to update my contact information (e.g., phone number, address). |
| **What Gets Created** | Updated Employee Profile Master Data with new contact information and profile picture. |
| **Related Business Rules** | **BR-2n**: Phone number requirement. **BR-2o**: Email address requirement. **BR-2g**: Address requirement. **BR-22**: All actions traced per BR 22 (timestamped and user-logged). |
| **Outputs & Data Flow** | Update Employee Profile Master Data. Trigger Notification N-037 (Profile updated) to employee and HR. All actions traced with timestamp and user ID. |

---

### STEP 3: Submit Request for Correction/Change

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Submit formal requests to modify critical, HR-governed data such as Name, National ID, Position, Department, or Marital Status. |
| **Why It Matters** | Provides formal channel for data corrections that require HR approval and validation, ensuring data integrity and audit compliance. |
| **Supporting Requirements** | **US-E6-02**: As an employee, I want to request corrections of data (e.g., job title or department). **US-E2-06**: As an employee, I want to submit requests to change legal name or marital status. |
| **What Gets Created** | Pending Change Request record with employee's requested changes and supporting information. |
| **Related Business Rules** | **BR-20a**: Only authorized roles can create and/or modify profile data. **BR-36**: All changes must be made via workflow approval. |
| **Outputs & Data Flow** | Creation of Pending Change Request record. Notification N-040 (Profile change request submitted) sent to HR/Manager. Request routed to HR approval queue. |

---

---

# PHASE 2: DEPARTMENT MANAGER INSIGHT

## 📋 Phase Description

**Department Managers see non-sensitive team summaries based on reporting lines with privacy restrictions applied.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Manager team visibility:
- View list of direct report team members
- See basic information (name, position, department, date of hire, status)
- Sensitive data hidden (salary, personal details, etc.)
- Information filtered by reporting line hierarchy
- Used for team management and oversight

---

### STEP 4: View Team Brief (Manager Insight)

| Aspect | Details |
|--------|---------|
| **Actor** | Department Manager |
| **What They Do** | Securely access team list displaying non-sensitive, summarized profile data filtered by direct reporting line hierarchy. |
| **Why It Matters** | Managers can see their team structure and basic information for scheduling, planning, and management purposes without accessing sensitive employee data. |
| **Supporting Requirements** | **US-E4-01**: As a manager, I want to view my team members' profiles (excluding sensitive info). **US-E4-02**: As a manager, I want to see a summary of my team's job titles, and departments. **US-E6-03**: As an HR Admin, I want to be able to search for employees data. |
| **What Gets Created** | Displayed summarized team list (Name, Position, Department, Date of Hire, Status). |
| **Related Business Rules** | **BR-41b**: Direct Managers see their team only. **BR-18b**: Privacy restrictions applied for Department Managers on sensitive data. **BR-3d, 3e**: Department/Supervisor links required. **BR-10c**: Pay Grade/Band definition. |
| **Inputs Needed** | Organizational Structure Module (Provides reporting line hierarchy to determine team members) |
| **System Integration** | Data retrieval from Organizational Structure for team hierarchy and position assignments |

---

---

# PHASE 3: HR/ADMIN PROCESSING & MASTER DATA MANAGEMENT

## 📋 Phase Description

**HR reviews and approves change requests through workflow, applies edits to master data, and system-syncs downstream modules (Payroll, Time Management, Org Structure) as required.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

HR master data management:
- Review pending change requests from employees
- Validate data and compliance
- Approve or reject requests with audit trail
- Apply approved changes to employee master record
- Deactivate profiles upon termination/resignation
- Assign roles and access permissions
- Sync changes across all downstream systems
- Maintain historical records

---

### STEP 5: Review and Process Change Request

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager / System Administrator |
| **What They Do** | Review pending change requests, validate compliance with policies and data requirements, and either approve (apply changes to master record) or reject. |
| **Why It Matters** | Ensures all employee profile changes are validated for accuracy and compliance before being applied to the master record and distributed to downstream systems. |
| **Supporting Requirements** | **US-E2-03**: As an HR admin, I want to review and approve employee-submitted profile changes before applying them. **US-E7-04**: As a system admin, I want to configure workflow rules. |
| **What Gets Created** | If Approved: Updated Employee Profile Master Data. If Rejected: Status updated to "Rejected" with reason documented. |
| **Related Business Rules** | **BR-36**: All changes must be made via workflow approval. **BR-22**: Traces any editing, changes, and cancellations in a timestamped and trailed manner. **BR-20a**: Only authorized roles can create/modify data. |
| **Outputs & Data Flow** | If Approved: Update Employee Profile Master Data. If change affects hierarchy (Position/Department), trigger update/request in Organizational Structure Module. Sync changes to Payroll and Time Management modules. If Rejected: Status updated to "Rejected". Notification N-037 (Profile updated/rejected) sent to employee. All changes logged with timestamp and user ID. |
| **System Integration** | Updates to downstream systems: Payroll Module (if Pay Grade/Contract Type changes), Time Management Module (if Status changes), Organizational Structure Module (if Position/Department changes) |

---

### STEP 6: Deactivate Profile & Assign Permissions

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager / System Administrator |
| **What They Do** | Deactivate employee profiles upon termination or resignation, and assign roles and access permissions to each employee. |
| **Why It Matters** | Ensures that terminated employees cannot access the system, protects data security, and maintains proper access controls. Permissions assignment ensures employees have appropriate system access for their roles. |
| **Supporting Requirements** | **US-EP-05**: As an HR admin, I want to deactivate an employee's profile upon termination or resignation. **US-E7-05**: As an HR admin, I want to assign roles and access permissions to each employee. |
| **What Gets Created** | Updated employee status (Active, Suspended, Retired, Terminated). Updated role and permission assignments. |
| **Related Business Rules** | **BR-3j**: Employee status definition for system access control. **BR-20a**: Only authorized roles can create/modify data. **BR-22**: All changes logged and traced. |
| **Inputs Needed** | Onboarding Module (Initial profile creation), Leaves Module/Offboarding Module (Status change triggers) |
| **Outputs & Data Flow** | Status field updated in Employee Profile Master Data. Access permissions updated in system. Changes synced to Payroll Module (payment blocking), Time Management Module (access restrictions), Analytics Module (compliance reporting). All changes logged with timestamp and user ID. |
| **System Integration** | Sync to Payroll & Benefits Module (payment processing and blocking), Time Management Module (time tracking access), Analytics Module (compliance reports) |

---

---

# 📋 COMPLETE EMPLOYEE PROFILE USER STORIES REFERENCE

### US-E2-04: View Personal Profile
**What User Needs:** "As an Employee, I want to view my full employee profile."

**Why It Matters:** Employees need to verify their personal, employment, and performance information is accurate.

**Related BRs:** BR-2a-r, BR-14, NFR-14

**System Must Support:**
- Secure login with role-based access control
- Display of all profile components (personal, employment, performance data)
- Real-time data retrieval from Performance and Organizational Structure modules
- Secure display of sensitive information

---

### US-E2-05: Update Contact Information
**What User Needs:** "As an Employee, I want to update my contact information (e.g., phone number, address)."

**Why It Matters:** Employees can keep HR informed of current contact details for emergency communication.

**Related BRs:** BR-2g, BR-2n, BR-2o, BR-22

**System Must Support:**
- Direct update of phone, email, address fields
- Immediate saving to profile
- Notification to HR of changes
- Audit trail with timestamp and user ID

---

### US-E2-12: Add Biography and Upload Profile Picture
**What User Needs:** "As an Employee, I want to add a short biography and upload a profile picture."

**Why It Matters:** Employees can personalize their profile and share professional information.

**Related BRs:** BR-22, BR-14

**System Must Support:**
- Profile picture upload functionality
- Biography text field
- Image format and size validation
- Audit trail of changes

---

### US-E6-02: Request Data Corrections
**What User Needs:** "As an Employee, I want to request corrections of data (e.g., job title or department)."

**Why It Matters:** Provides formal channel for employees to request changes to critical data requiring HR approval.

**Related BRs:** BR-20a, BR-36, BR-22

**System Must Support:**
- Formal change request submission
- Document reason for change
- Route to HR approval workflow
- Track request status
- Notify employee of decision

---

### US-E2-06: Submit Legal Name or Marital Status Change
**What User Needs:** "As an Employee, I want to submit requests to change legal name or marital status."

**Why It Matters:** Enables employees to update critical personal information through proper HR channels.

**Related BRs:** BR-20a, BR-36, BR-22

**System Must Support:**
- Submission of name change request
- Submission of marital status change request
- Document submission with supporting information
- HR validation and approval
- Update to all affected systems upon approval

---

### US-E4-01: View Team Profiles (Manager)
**What User Needs:** "As a Manager, I want to view my team members' profiles (excluding sensitive info)."

**Why It Matters:** Managers need to see team information for scheduling and management purposes.

**Related BRs:** BR-41b, BR-18b, BR-3d, BR-3e

**System Must Support:**
- Filter team members by reporting line
- Display non-sensitive data only
- Show position and department information
- Role-based access restrictions

---

### US-E4-02: View Team Summary
**What User Needs:** "As a Manager, I want to see a summary of my team's job titles, and departments."

**Why It Matters:** Managers can quickly see team composition and structure.

**Related BRs:** BR-41b, BR-18b, BR-3d, BR-3e, BR-10c

**System Must Support:**
- Summary view of team job titles
- Department assignment display
- Team structure visualization
- Filtering by department or position

---

### US-E6-03: Search Employee Data (HR Admin)
**What User Needs:** "As an HR Admin, I want to be able to search for employees data."

**Why It Matters:** HR needs to quickly find and access employee information for administrative tasks.

**Related BRs:** BR-20a, BR-14

**System Must Support:**
- Search by employee ID
- Search by name
- Search by department
- Advanced filters
- Role-based access restrictions

---

### US-EP-04: Edit Employee Profile (HR Admin)
**What User Needs:** "As an HR Admin, I want to edit any part of an employee's profile."

**Why It Matters:** HR needs to maintain master data accuracy and update information as needed.

**Related BRs:** BR-20a, BR-36, BR-22

**System Must Support:**
- Edit all profile fields
- Save changes to master record
- Audit trail of all edits
- Timestamp and user ID tracking
- Sync to downstream systems

---

### US-E2-03: Review and Approve Profile Changes
**What User Needs:** "As an HR Admin, I want to review and approve employee-submitted profile changes before applying them."

**Why It Matters:** Ensures employee-requested changes are validated before being applied to master data.

**Related BRs:** BR-36, BR-22, BR-20a

**System Must Support:**
- View pending change requests
- Review change details
- Approve or reject requests
- Document decision with reason
- Apply approved changes to master record
- Notify employee of decision

---

### US-EP-05: Deactivate Employee Profile
**What User Needs:** "As an HR Admin, I want to deactivate an employee's profile upon termination or resignation."

**Why It Matters:** Prevents terminated employees from accessing the system and maintains security.

**Related BRs:** BR-3j, BR-20a, BR-22

**System Must Support:**
- Update employee status to Terminated/Resigned
- Disable system access
- Maintain historical record
- Sync status to all systems
- Audit trail of deactivation

---

### US-E7-05: Assign Roles and Permissions
**What User Needs:** "As an HR Admin, I want to assign roles and access permissions to each employee."

**Why It Matters:** Ensures employees have appropriate system access for their roles.

**Related BRs:** BR-20a, BR-22, BR-3j

**System Must Support:**
- Role assignment functionality
- Permission assignment by role
- Update of access levels
- Audit trail of permission changes
- Enforcement of role-based access control

---

---

# 📋 COMPLETE EMPLOYEE PROFILE BUSINESS RULES REFERENCE TABLE

This section contains ALL Employee Profile Business Rules with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-2a-r** | System must record specific personal and job data including address, phone, email, education details, employment information, and other required fields. |
| **BR-3d** | Department/Supervisor links required to establish reporting relationships. |
| **BR-3e** | Supervisor assignment required for hierarchical organization. |
| **BR-3h** | Education Details storage requirement for employee development tracking. |
| **BR-3j** | Employee status definition for system access control (Active, Suspended, Retired, Terminated). |
| **BR-10c** | Pay Grade/Band definition required for compensation. |
| **BR-14** | Authentication and secure access controls required for system access. |
| **BR-16** | Appraisal records must be saved on employee profile. |
| **BR-18b** | Privacy restrictions must be applied for Line Managers on sensitive data. |
| **BR-20a** | Only authorized roles can create and/or modify profile data. |
| **BR-22** | All editing, changes, and cancellations must be traced in a timestamped and user-logged manner. |
| **BR-36** | All changes must be made via workflow approval. |
| **BR-41b** | Direct Managers see their team only (role-based access restriction). |
| **NFR-14** | All users shall authenticate via secure login and role-based access control. |

---

**Document Complete. All sections properly formatted and cross-referenced with user stories and business rules.**

