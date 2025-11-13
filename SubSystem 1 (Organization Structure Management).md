# ORGANIZATION STRUCTURE MANAGEMENT SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** This subsystem defines and maintains how the company is organized. It enables System Administrators to create departments and positions, update them when changes happen, and deactivate positions that are no longer needed while keeping their history. It allows managers to request changes to reporting lines or positions, and enables role-based organizational visibility for all employees.

### 🎯 What Does This Subsystem Do? (Simple Explanation)

Think of this subsystem as the organizational blueprint. It handles:
- **Structure definition** - System Admins create and define departments, positions, and reporting relationships
- **Structure maintenance** - System Admins update positions, departments, pay grades, and hierarchies
- **Change requests** - Managers can request modifications to reporting lines or team assignments
- **Approvals** - Change requests go through workflow validation to prevent structural issues
- **Deactivation** - Obsolete positions are deactivated while preserving historical records
- **Synchronization** - Changes automatically update dependent systems (Payroll, Recruitment, Employee Profiles)
- **Organizational visibility** - Employees and managers see the org chart based on role-based access
- **Historical tracking** - All structural changes are versioned and audited for compliance

Instead of manual coordination between departments when organizational changes occur, this subsystem manages the entire structure while automatically syncing updates to all dependent systems.

---

## 📊 ORGANIZATION STRUCTURE FLOW

**The Organizational Structure Management (OSM) Module governs how departments, positions, and hierarchical structures are created, updated, and maintained across the HR system. This ensures that the organizational framework remains accurate and aligned with operational and administrative needs.**

### 🔍 What This Process Does (Simplified)

This is a 3-phase lifecycle that:
1. System Admin defines and creates new departments and positions in the organizational hierarchy
2. System Admin maintains and updates existing structures as needs change
3. System Admin deactivates obsolete positions while preserving historical records, with all changes automatically syncing to dependent systems

Each phase builds on the previous to maintain an accurate, auditable organizational structure.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must maintain the organizational hierarchy with accurate reporting relationships."

**Why it matters:** Requirements define what functionality the system needs to provide for organizational management.

---

### 👤 USER STORIES (REQ)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As a System Admin, I want to define and create departments and positions so that the organization can grow and change."

**Real-World Translation:** John, the System Administrator, creates a new department for the expanding sales team and defines positions within it, complete with pay grades and reporting lines.

**Why it matters:** 
- Makes requirements human-centered (focuses on actual user needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Can John successfully create a department?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-12: Positions cannot be deleted if historical employee assignments exist; they can only be delimited."

**Real-World Translation:** "When a position is no longer needed but has had employees assigned to it, the system can't delete it. Instead, it marks the position as 'delimited' (closed as of a date) but keeps the historical record."

**Why it matters:**
- Defines exact logic developers must code
- Ensures consistency (all structural changes follow same rules)
- Creates auditability (what changed, when, why)
- Links to legal/compliance requirements

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works.

**Example:**
```
Admin creates new position
  → System generates position ID
  → Admin assigns pay grade
  → Admin sets reporting manager
  → Position marked as vacant
  → Payroll module updated
  → Recruitment notified
  → History logged
```

**Real-World Translation:** The complete process for adding a new position to the organization.

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
| **REQ-OSM-01 (User Story)** | "As a System Admin, I want to define and create departments and positions." |
| **BR-10 (Business Rule)** | "Position must have Position ID, Pay Grade, Department ID." |
| **FLOW (Process)** | (1) Admin enters position details, (2) System validates, (3) Position created, (4) Marked as vacant, (5) Payroll updated |
| **IMPLEMENTATION** | Developer codes: "Validate position data. Generate unique ID. Sync to Payroll and Recruitment modules." |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what administrators actually need
2. **Business Rules** ensure structural integrity and compliance
3. **Flows** ensure all dependent systems stay synchronized
4. **Together** they create a complete, auditable organizational structure system

---

---

# PHASE 1: STRUCTURE DEFINITION

## 📋 Phase Description

**The process begins when the System Administrator defines and creates new organizational entities such as departments or positions. These additions accommodate new roles within the company hierarchy. Each position is linked to a department and assigned its relevant attributes including identification codes, reporting lines, and pay grades.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Defining organizational structure:
- Create new departments
- Create new positions within departments
- Assign position IDs and attributes
- Set reporting relationships
- Define pay grades
- Mark positions as vacant for recruitment
- Auto-notify dependent systems

---

### STEP 1: Define and Create Department or Position

| Aspect | Details |
|--------|---------|
| **Actor** | System Administrator |
| **What They Do** | Define and create organizational entities (departments, positions) to structurally accommodate new roles within the hierarchy. |
| **Why It Matters** | Creates the foundation for organizational growth and allows the system to support new business needs. |
| **Supporting Requirements** | **REQ-OSM-01**: As a System Admin, I want to define and create departments and positions. |
| **What Gets Created** | Vacant position created in Organizational Structure (OS). Position automatically flagged as vacant for recruitment. |
| **Related Business Rules** | **BR-5**: Unique ID for entities. **BR-10**: Position must have Position ID, Pay Grade, Department ID. **BR-30**: Creation requires Cost Center and Reporting Manager. |
| **Outputs & Data Flow** | Position record created with all attributes. Payroll/Benefits module updated with Cost Center and Wage Type. Recruitment module notified of vacancy. All changes logged with timestamp and user ID. |
| **Inputs Needed** | Payroll/Benefits (Pay Grade definitions), Employee Profile (for linking positions to employees later) |
| **System Integration** | Updates to Payroll Module (Cost Center/Wage Type linkage), Recruitment Module (vacancy notification) |

---

---

# PHASE 2: STRUCTURAL MAINTENANCE

## 📋 Phase Description

**When modifications are needed, the System Administrator performs direct updates or maintenance of existing departments and positions. This may include renaming, reassigning, or updating attributes such as reporting structures or pay grades. Structural changes are applied immediately across the system.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Updating organizational structure:
- Update position attributes (title, pay grade, reporting line)
- Update department information
- Modify reporting relationships
- Update cost center assignments
- All changes immediately sync to dependent systems
- Changes are logged for audit trail

---

### STEP 2: Edit/Update Position

| Aspect | Details |
|--------|---------|
| **Actor** | System Administrator |
| **What They Do** | Perform direct updates or maintenance of existing departments and positions. Can update titles, pay grades, reporting lines, and other position attributes. |
| **Why It Matters** | Allows the organization to adapt as business needs change without recreating entire structures. |
| **Supporting Requirements** | **REQ-OSM-02**: As a System Admin, I want to update existing departments and positions. |
| **What Gets Created** | Updated position record with modified attributes. Historical version maintained. |
| **Related Business Rules** | **BR-22**: All changes must be traced with timestamp and user ID. **BR-10**: Position must maintain Position ID, Pay Grade, Department ID throughout. |
| **Outputs & Data Flow** | System Synchronization: Approved structural changes are immediately applied to hierarchy in Organizational Structure (OS). Payroll Module updated if Pay Grade changes. Employee Profile Module updated if reporting line changes. All changes logged with audit trail. |
| **System Integration** | Updates to Payroll Module (if compensation changes), Employee Profile Module (if reporting changes), Time Management (if department changes) |

---

---

# PHASE 3: DEACTIVATION AND SYNCHRONIZATION

## 📋 Phase Description

**When a position or department becomes obsolete, the System Administrator deactivates it from the active structure. Positions with historical employee records are not deleted but are delimited—meaning they are closed as of a certain date—to preserve organizational history.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Deactivating positions safely:
- Deactivate obsolete positions from active structure
- Preserve historical records (don't delete)
- Mark as delimited with effective date
- Auto-notify dependent systems
- Prevent re-use of critical historical references

---

### STEP 3: Deactivate Position

| Aspect | Details |
|--------|---------|
| **Actor** | System Administrator |
| **What They Do** | Deactivate or remove obsolete positions from the active organizational structure. Positions with historical employee assignments are delimited rather than deleted to preserve organizational history. |
| **Why It Matters** | Keeps the active organization chart current while maintaining historical records for audit and reporting purposes. |
| **Supporting Requirements** | **REQ-OSM-05**: As a System Admin, I want to deactivate or remove obsolete roles or positions, so that the organizational structure stays clean and up-to-date. |
| **What Gets Created** | Position marked as Frozen/Inactive with delimiting date. Historical record preserved. |
| **Related Business Rules** | **BR-12**: Positions cannot be deleted if historical employee assignments exist; they can only be delimited. **BR-16**: Position status includes Frozen/Inactive. **BR-37**: Historical records must be preserved using delimiting. |
| **Outputs & Data Flow** | System Synchronization: Approved structural changes immediately applied to hierarchy in OS. Recruitment Module notified (Vacant/Frozen positions flagged for posting status). Offboarding Module updated (Position delimited upon exit). All changes logged with audit trail. |
| **System Integration** | Updates to Recruitment Module (posting status), Offboarding Module (position removal status), Historical Archives (maintain historical records) |

---

---

# STEP 4: Manager Request Structural Change

| Aspect | Details |
|--------|---------|
| **Actor** | Department Manager |
| **What They Do** | Submit requests for changes to reporting lines or team assignments so that team structures reflect actual work relationships. |
| **Why It Matters** | Allows managers to formally request structural changes while maintaining control and audit trail. |
| **Supporting Requirements** | **REQ-OSM-03**: As a Manager, I want to submit requests for changes to reporting lines or team assignments. |
| **What Gets Created** | Pending structural change request record. |
| **Related Business Rules** | **BR-36**: All changes must be made via workflow approval. **BR-22**: All requests logged with timestamp. |
| **Outputs & Data Flow** | Request saved to pending approval queue. Notification N sent to System Admin for approval. |
| **System Integration** | Organizational Structure (OS): Change request saved in pending approval queue. Notifications: Alert sent to System Admin. |

---

### STEP 5: Review and Approve Manager Requests

| Aspect | Details |
|--------|---------|
| **Actor** | System Administrator |
| **What They Do** | Review and approve manager requests for structural changes. Validate that changes don't create circular reporting lines, duplicate positions, or mismatched department assignments. |
| **Why It Matters** | Ensures modifications to hierarchy are controlled and consistent, preventing structural integrity issues. |
| **Supporting Requirements** | **REQ-OSM-04**: As a System Admin, I want to review and approve manager requests for changes, so that modifications to the hierarchy are controlled and consistent. |
| **What Gets Created** | Approved structural change applied to organization structure. If rejected, request marked as rejected with reason. |
| **Related Business Rules** | **BR-36**: All changes must be made via workflow approval. **BR-22**: All decisions logged with audit trail. **REQ-OSM-09**: Validation rules prevent circular reporting lines, duplicate positions, mismatched department assignments. |
| **Outputs & Data Flow** | If Approved: Structural changes applied to OS. Dependent modules (Employee Profile, Payroll) notified and updated. If Rejected: Status marked "Rejected" with reason documented. Manager notified of decision. All changes logged with timestamp and audit trail. |
| **System Integration** | Updates to Employee Profile, Payroll, Recruitment based on approval |

---

### STEP 6: Hierarchy Change Notification

| Aspect | Details |
|--------|---------|
| **Actor** | System (Automated) |
| **What They Do** | Automatically notify managers and relevant stakeholders when a structural change occurs or is approved according to hierarchy. |
| **Why It Matters** | Keeps all affected parties informed of organizational changes and maintains transparency. |
| **Supporting Requirements** | **REQ-OSM-11**: As a System Admin, I want the system to notify managers and relevant stakeholders when a structural change occurs or is approved according to hierarchy. |
| **What Gets Created** | Notifications sent to affected managers and stakeholders. |
| **Related Business Rules** | **BR-22**: Changes must retain version history and audit logs with timestamp and user ID. |
| **Outputs & Data Flow** | Notifications sent to impacted managers based on hierarchical position. Version history maintained. Audit logs created. |

---

### STEP 7: Structure Access & Visibility

| Aspect | Details |
|--------|---------|
| **Actor** | Employee / Manager / System |
| **What They Do** | Display organizational hierarchy based on role-based access. Employees view their own position and structure. Managers view their team. |
| **Why It Matters** | Provides visibility to organizational structure while maintaining appropriate access controls based on roles. |
| **Supporting Requirements** | **REQ-SANV-01**: As an Employee, I want to view the organizational hierarchy. **REQ-SANV-02**: As a Manager, I want to view my team's structure and reporting lines. |
| **What Gets Created** | Displayed organizational chart based on role and access permissions. |
| **Related Business Rules** | **BR-24**: Organizational structure must be viewable as a graphical chart. **BR-41**: Access must be role-based, where Direct Managers see their team only and Employees see their own structure. |
| **Outputs & Data Flow** | Graphical org chart displayed to authorized users. Employee Profile Module provides person data. Role-based filters applied for access control. |
| **Inputs Needed** | Employee Profile (EP) (Provides the individual's data to display alongside position) |

---

---

# 📋 COMPLETE ORGANIZATION STRUCTURE USER STORIES REFERENCE

### REQ-OSM-01: Define and Create Departments and Positions
**What User Needs:** "As a System Admin, I want to define and create departments and positions."

**Why It Matters:** Enables organizational growth and structure definition.

**Related BRs:** BR-5, BR-10, BR-30

**System Must Support:**
- Department creation with name and attributes
- Position creation with all required attributes
- Assignment of Position ID, Pay Grade, Department ID
- Assignment of reporting manager
- Cost Center assignment
- Position flagged as vacant for recruitment

---

### REQ-OSM-02: Update Existing Departments and Positions
**What User Needs:** "As a System Admin, I want to update existing departments and positions."

**Why It Matters:** Allows organizational adaptation without recreating structures.

**Related BRs:** BR-10, BR-22

**System Must Support:**
- Edit position attributes
- Update pay grades
- Modify reporting relationships
- Update department information
- Immediate synchronization to dependent systems
- Audit trail of all changes

---

### REQ-OSM-03: Submit Requests for Structural Changes (Manager)
**What User Needs:** "As a Manager, I want to submit requests for changes to reporting lines or team assignments."

**Why It Matters:** Allows managers to formally request structural changes while maintaining control.

**Related BRs:** BR-36, BR-22, REQ-OSM-09

**System Must Support:**
- Change request submission
- Reporting line modification requests
- Team assignment change requests
- Validation to prevent structural issues
- Audit trail of requests

---

### REQ-OSM-04: Review and Approve Manager Requests
**What User Needs:** "As a System Admin, I want to review and approve manager requests for changes."

**Why It Matters:** Ensures modifications are controlled and consistent.

**Related BRs:** BR-36, BR-22, REQ-OSM-09

**System Must Support:**
- View pending requests
- Validate changes don't create issues
- Approve or reject requests
- Apply approved changes
- Notify managers of decision

---

### REQ-OSM-05: Deactivate Obsolete Positions
**What User Needs:** "As a System Admin, I want to deactivate or remove obsolete roles or positions."

**Why It Matters:** Keeps organizational structure current and clean.

**Related BRs:** BR-12, BR-16, BR-37

**System Must Support:**
- Mark positions as Frozen/Inactive
- Delimit positions with effective date
- Preserve historical records
- Prevent deletion of positions with history
- Notify dependent systems

---

### REQ-SANV-01: View Organizational Hierarchy (Employee)
**What User Needs:** "As an Employee, I want to view the organizational hierarchy."

**Why It Matters:** Employees understand the organization structure and their place in it.

**Related BRs:** BR-24, BR-41

**System Must Support:**
- Display organizational hierarchy
- Show employee's position in structure
- Graphical chart representation
- Role-based visibility

---

### REQ-SANV-02: View Team Structure (Manager)
**What User Needs:** "As a Manager, I want to view my team's structure and reporting lines."

**Why It Matters:** Managers understand their team composition and reporting relationships.

**Related BRs:** BR-24, BR-41

**System Must Support:**
- Display team members
- Show reporting relationships
- Graphical chart of team
- Filter by department if needed
- Access only to direct reports

---

### REQ-OSM-11: Notify on Structural Changes
**What User Needs:** "As a System Admin, I want the system to notify managers and stakeholders when structural changes occur."

**Why It Matters:** Keeps all affected parties informed of organizational changes.

**Related BRs:** BR-22

**System Must Support:**
- Automatic notifications on changes
- Notification based on hierarchy
- Timestamp and user ID logging
- Version history maintained

---

---

# 📋 COMPLETE ORGANIZATION STRUCTURE BUSINESS RULES REFERENCE TABLE

This section contains ALL Organization Structure Business Rules with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-5** | Unique ID required for all organizational entities (departments, positions). |
| **BR-10** | Position must have Job Key/Position ID, Pay Grade, and Department ID to be created. |
| **BR-12** | Positions cannot be deleted if historical employee assignments exist; they can only be delimited. |
| **BR-16** | Position status includes Frozen/Inactive status for inactive positions. |
| **BR-22** | All changes must be traced with timestamp and user ID for audit purposes. |
| **BR-24** | Organizational structure must be viewable as a graphical chart. |
| **BR-30** | Position creation requires Cost Center and Reporting Manager assignment. |
| **BR-36** | All structural changes must be made via workflow approval process. |
| **BR-37** | Historical records must be preserved using delimiting when positions become inactive. |
| **BR-41** | Access must be role-based, where Direct Managers see their team only and Employees see their own structure. |
| **REQ-OSM-09** | Validation rules must prevent circular reporting lines, duplicate positions, and mismatched department assignments. |

---

**Document Complete. All sections properly formatted and cross-referenced with user stories and business rules.**

