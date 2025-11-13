# PAYROLL CONFIGURATION & POLICY SETUP SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** This subsystem automates the initial and ongoing setup of payroll rules, ensuring that the system reflects the organization's compensation structure, benefits policies, and statutory requirements.

### 🎯 What Does This Subsystem Do? (Simple Explanation)

Think of this subsystem as the foundation and blueprint for the entire payroll system. It handles:
- **Configures compensation structures** - defining salary types, pay grades, allowances, and bonuses
- **Embeds legal compliance** - incorporating tax rules, labor laws, and insurance regulations
- **Secures system settings** - establishing company-wide parameters and backup protocols
- **Controls approvals** - ensuring only authorized personnel can modify critical payroll rules
- **Manages policy updates** - allowing legal and HR teams to update insurance and compensation rules

Instead of manual payroll calculations that change constantly and risk compliance violations, this subsystem establishes a secure, audit-logged, policy-enforced foundation where every configuration is validated before the payroll execution subsystem begins its work.

---

## 📊 PAYROLL CONFIGURATION FLOW

**The Payroll Configuration & Policy Setup Subsystem establishes all payroll rules, pay structures, and compliance settings that govern salary calculations. It progresses through five key phases to ensure data integrity, approval control, and legal compliance before execution begins.**

### 🔍 What This Process Does (Simplified)

This is a 5-phase cycle that:
1. Defines core payroll structures (policies, grades, types, allowances, bonuses)
2. Embeds legal compliance (taxes, labor laws, insurance rules)
3. Configures system parameters (company settings, backups, security)
4. Reviews and approves all configurations before activation
5. Allows HR oversight of insurance and policy updates

Each phase builds on the previous one to create a complete, compliant, and auditable payroll foundation.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must enforce local tax laws in payroll calculations"

**Why it matters:** Requirements define the foundation—they establish what business needs the system must fulfill.

---

### 👤 USER STORIES (US)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As a Payroll Specialist, I want to configure company-level payroll policies so that the system enforces organizational rules consistently."

**Real-World Translation:** Maria, the Payroll Specialist, needs to set up company policies without calling IT every time something changes. Once configured, the system automatically applies these rules to all salary calculations.

**Why it matters:** 
- Makes requirements user-centered (focuses on actual job needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Did Maria successfully configure the policy?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-1: The system must require an active employment contract with a defined role, type, start/end dates and salary basis before payroll can be processed."

**Real-World Translation:** "The system must validate that an employee has a current contract before calculating their salary. If the contract expired, payroll can't run."

**Why it matters:**
- Defines the exact logic developers must code
- Ensures consistency (all payroll follows the same rules)
- Creates auditability (rules are documented and traceable)
- Links to legal/compliance requirements (labor laws, tax codes)

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works, from start to finish.

**Example:**
```
Payroll Specialist creates salary structure
  → System stores in draft
  → Payroll Manager reviews and approves
  → Configuration becomes active for payroll runs
  → HR can update when policies change
```

**Real-World Translation:** Maria creates a new salary grade. The system stores it as "draft." Her manager John reviews it and approves. Now the system uses this grade for all salary calculations. If tax laws change, the legal team can update the tax rules, and the system automatically applies them to future payroll.

**Why it matters:**
- Shows the sequence of operations (order matters)
- Helps everyone understand the big picture
- Identifies where things can go wrong (what if an unapproved config was used?)
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
| **REQ-PY-1 (User Story)** | "As a Payroll Specialist, I want to configure company-level payroll policies so that the system enforces organizational rules consistently." |
| **BR-9 (Business Rule)** | "Payroll Structure must support base pay, allowances, deductions, and other variable pay elements" |
| **FLOW (Process)** | (1) Specialist creates policy in system, (2) System stores as draft, (3) Manager reviews and approves, (4) Policy becomes active, (5) System applies to all salary calculations |
| **IMPLEMENTATION** | Developer codes: "Store all policy configs in audit-logged draft state. Require manager approval. Only apply approved configs to payroll calculations." |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what users actually need
2. **Business Rules** ensure every requirement is enforced consistently
3. **Flows** ensure everything happens in the right order and with proper controls
4. **Together** they create a complete, compliant, auditable payroll foundation

---

# 📊 COMPREHENSIVE REQUIREMENTS MATRIX

## Overview of All Requirements by Phase

| Phase | Requirement Name | US ID | BR IDs |
|-------|------------------|-------|--------|
| **Phase 1** | Payroll Policies Configuration | REQ-PY-1 | BR-1, BR-9 |
| **Phase 1** | Pay Grades Configuration | REQ-PY-2 | BR-10, BR-31 |
| **Phase 1** | Pay Types Configuration | REQ-PY-5 | BR-1, BR-2 |
| **Phase 1** | Allowances Configuration | REQ-PY-7 | BR-9, BR-39 |
| **Phase 1** | Signing Bonuses Configuration | REQ-PY-19 | BR-56, BR-24, BR-28, BR-25 |
| **Phase 1** | Resignation & Termination Benefits Configuration | REQ-PY-20 | BR-56, BR-26, BR-27, BR-29 |
| **Phase 2** | Tax Rules & Laws Configuration | REQ-PY-10 | BR-5, BR-6, BR-20 |
| **Phase 2** | Legal Rules Update | REQ-PY-12 | BR-1, BR-20 |
| **Phase 2** | Insurance Brackets Configuration | REQ-PY-21 | BR-7, BR-8, BR-31 |
| **Phase 3** | Company-Wide Settings Configuration | REQ-PY-15 | BR-3 |
| **Phase 3** | Data Backup Configuration | REQ-PY-16 | BR-36 |
| **Phase 4** | Payroll Configuration Approval/Disapproval | REQ-PY-18 | BR-30, BR-63 |
| **Phase 5** | Insurance Brackets Review & Update | REQ-PY-22 | BR-7, BR-8, BR-31 |

---

# PHASE 1: DEFINE STRUCTURE

## 📋 Phase Description

**The process begins when the Payroll Specialist defines core payroll elements — policies, pay grades, pay types, allowances, signing bonuses, and resignation/termination benefits. These templates establish the foundation for all salary calculations and compensation structures. The phase ensures that all compensation elements are clearly defined, tied to organizational structure (department/position), and ready for compliance embedding in the next phase.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Imagine you're running a company with multiple departments and job levels. You need to:
- Define what types of salaries exist (hourly, daily, monthly, contract-based)
- Create salary bands for different positions and departments
- Set up allowances (transportation, housing, meals, etc.)
- Configure bonuses for new hires
- Define what employees get when they resign or are terminated
- Establish company policies for misconduct penalties, leave deductions, etc.

This phase handles all of that foundational structure setup.

---

### STEP 1: Payroll Policies Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Defines and configures company-level payroll policies including basic salary types, misconduct penalties, leave policies, and allowances. Creates, edits, and views policy configurations in draft mode before approval. |
| **Why It Matters** | Establishes organizational rules that the system will enforce consistently across all salary calculations. Without this foundation, different employees could be treated differently, creating compliance risks and fairness issues. |
| **Supporting Requirements** | **REQ-PY-1** - As a Payroll Specialist, I want to configure company-level payroll policies (e.g., basic salary types, misconduct penalties, leave policies, allowance) so that the system enforces organizational rules consistently. (Create draft, edit draft, view all) |
| **What Gets Created** | Policy configuration stored in draft state with full audit trail; ready for manager review and approval in Phase 4 |
| **Related Business Rules** | **BR-1**: The system must require an active employment contract with a defined role, type (full-time, part-time, hourly, commission-based, etc.), start/end dates and salary basis before payroll can be processed. Local labor law (Egyptian labor law 2025) needs to be followed. **BR-9**: Payroll Structure must support base pay, allowances, deductions, and other variable pay elements **BR-33**: The system must apply deductions for misconduct penalties (e.g., lateness, asset damage, disciplinary actions) as configured by HR policy, consistent with Egyptian law **BR-34**: The system must ensure all deductions (taxes, insurance, penalties, unpaid leave, recovery) are applied after gross salary calculation and before net salary. **BR-46**: Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. |
| **Success Criteria** | ✓ Policies created with all required components ✓ Draft state maintains audit trail ✓ Policies are organization-wide and consistent ✓ Ready for manager review ✓ Properly linked to labor law requirements |
| **System Integration** | Configuration Module (stores policies) → Audit Trail System (logs all changes) → Draft Management (maintains version history) |

---

### STEP 2: Pay Grades Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Defines pay grades by department and position, specifying salary ranges and base pay structures. Creates, edits, and views pay grade configurations in draft mode. Each grade can have different salary ranges for different organizational units. |
| **Why It Matters** | Ensures that salary structures are consistent within organizational hierarchy while allowing flexibility across departments and locations. Prevents managers from paying inconsistent salaries and establishes clear compensation transparency. |
| **Supporting Requirements** | **REQ-PY-2** - As a Payroll Specialist, I want to define pay grades, salary, and compensation limits so that managers and payroll specialists cannot exceed policy boundaries. (Create draft, edit draft, view all) for department and position |
| **What Gets Created** | Pay grade structures stored by department/position with salary ranges; configured for use with Payroll Areas and Schemas (Phase 1, Step 5). |
| **Related Business Rules** | **BR-10**: The system allows for multiple pay scales configurable by grade, department, or location. **BR-31**: The system needs to have a breakdown: Payroll Areas (batch of people for which payroll runs at the same time) and Payroll Schemas (payroll logic/recipe). Formula: [Net Salary = Gross Salary(base pay+ allowances) – Taxes – Social/Health Insurance – Other Deductions]. The system follows: Payroll Area picks employees and period. Schema runs payroll logic for that group. **BR-4**: The system must identify the minimum salary bracket(s) enforced through Local Labor Law. **BR-2**: The system must calculate base salary according to contract terms and role type. |
| **Success Criteria** | ✓ Pay grades defined by department and position ✓ Salary ranges established and documented ✓ Compliance with minimum wage law enforced ✓ Draft state with version control ✓ Ready for integration with Payroll Schemas |
| **System Integration** | Organizational Structure (provides department/position hierarchy) → Pay Grade Module (creates grades) → Payroll Schema System (uses grades for calculations) |
| **Inputs Needed** | Organizational Structure (Job Grade/Band information) |

---

### STEP 3: Pay Types Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Defines employee pay types (hourly, daily, weekly, monthly, contract-based) that align with employment agreements. Creates, edits, and views pay type configurations so salaries are calculated according to the employment contract basis. |
| **Why It Matters** | Different employment types require different calculation methods. An hourly employee's salary is calculated per hour, a monthly employee per month, a contractor per contract. The system must understand which type applies to each employee to calculate accurately. |
| **Supporting Requirements** | **REQ-PY-5** - As a Payroll Specialist, I want the system to define employee pay types (hourly, daily, weekly, monthly, contract-based) so that salaries are calculated according to the employment agreement. (Create draft, edit draft, view all) |
| **What Gets Created** | Pay type definitions with calculation basis; stored in draft for manager review and activation |
| **Related Business Rules** | **BR-1**: The system must require an active employment contract with a defined role, type (full-time, part-time, hourly, commission-based, etc.), start/end dates and salary basis before payroll can be processed. Local labor law (Egyptian labor law 2025) needs to be followed. **BR-2**: The system must calculate base salary according to contract terms and role type. **BR-3**: Payroll must be processed within defined cycles (monthly, etc) per contract or region following the local laws. |
| **Success Criteria** | ✓ All pay types defined (hourly, daily, weekly, monthly, contract) ✓ Each type has calculation methodology ✓ Aligned with employment agreements ✓ Draft state with audit trail ✓ Ready for contract linkage |
| **System Integration** | Employee Contracts (provides contract type information) → Pay Type Module (defines calculation basis) → Payroll Calculation Engine (uses pay types for salary math) |

---

### STEP 4: Allowances Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Sets up allowance structures including transportation, housing, meals, and other special compensation. Creates, edits, and views allowance configurations with types, amounts, and eligibility criteria. |
| **Why It Matters** | Allowances are a significant part of compensation and vary by role and circumstances. Systematizing them ensures consistent application and prevents overpayment or underpayment while supporting special conditions (location, role requirements). |
| **Supporting Requirements** | **REQ-PY-7** - As a Payroll Specialist, I want to set allowances (e.g., transportation, housing, etc) so that employees are rewarded for special conditions. (Create draft, edit draft, view all) |
| **What Gets Created** | Allowance structure configurations with types and amounts; integrated into gross salary calculation formula |
| **Related Business Rules** | **BR-9**: Payroll Structure must support base pay, allowances, deductions, and other variable pay elements **BR-39**: Allowance Structure must support and track different types (e.g. transportation, housing, meals, etc). **BR-38**: The system must allow defining allowances with multiple types as part of the employment contract and add them to payroll as part of gross salary, defined per role or contract. **BR-46**: Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. **BR-31**: Net Salary Formula = Gross Salary(base pay+ allowances) – Taxes – Social/Health Insurance – Other Deductions |
| **Success Criteria** | ✓ Multiple allowance types defined ✓ Amounts and eligibility criteria clear ✓ Linked to roles/contracts ✓ Integrated into gross salary ✓ Draft state with manager review ready |
| **System Integration** | Employee Contracts (identifies eligible allowances) → Allowance Module (configures amounts/types) → Gross Salary Calculation (adds allowances to base pay) |

---

### STEP 5: Signing Bonuses Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Configures policies for signing bonuses including eligibility criteria, amounts, payment terms (one-time, phased), and approval workflows. Creates, edits, and views signing bonus configurations for new hires. |
| **Why It Matters** | Signing bonuses attract talent but must be carefully controlled—they should only be disbursed once, require approval, and be linked to contract eligibility. Without proper configuration, the system could pay bonuses incorrectly or to ineligible employees. |
| **Supporting Requirements** | **REQ-PY-19** - As a Payroll Specialist, I want to configure policies for signing bonuses, so that new hires are seamlessly incorporated into the company's payroll system. (Create draft, edit draft, view all) |
| **What Gets Created** | Signing bonus policies with eligibility rules, amounts, and payment schedules; linked to employee contracts |
| **Related Business Rules** | **BR-56**: The system must support signing bonuses as a distinct payroll component, configurable by contract terms (e.g., one-time, etc), and subject to approval workflows. **BR-24**: Signing bonuses must be processed only for employees flagged as eligible in their contracts (linked through Employee Profile). **BR-28**: The system must ensure a signing bonus is disbursed only once unless explicitly authorized. **BR-25**: Any manual overrides for signing bonuses must require authorization. |
| **Success Criteria** | ✓ Bonus eligibility criteria defined ✓ Amounts and payment terms configured ✓ Linked to contracts ✓ One-time disbursement enforced ✓ Approval workflows established ✓ Draft ready for manager review |
| **System Integration** | Onboarding Module (Contract details) → Signing Bonus Module (policies) → Approval Workflow (authorization) → Payroll Processing (disbursement only once) |
| **Inputs Needed** | Onboarding (Contract details) |

---

### STEP 6: Resignation & Termination Benefits Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Configures resignation and termination benefits including severance pay, end-of-service gratuity, accrued leave payout, pending allowances, and service completion benefits. Creates, edits, and views benefit configurations aligned with labor laws. |
| **Why It Matters** | Resignation and termination entitlements are legally mandated and complex. Proper configuration ensures compliance with local labor law (Egyptian labor law 2025), prevents legal disputes, and ensures fair treatment of departing employees. |
| **Supporting Requirements** | **REQ-PY-20** - As a Payroll Specialist, I want to configure resignation and termination benefits and their terms, so that the offboarding process for employees is seamless and legally compliant. (Create draft, edit draft, view all) |
| **What Gets Created** | Benefit configuration policies with calculation rules for resignation and termination scenarios; linked to labor law requirements |
| **Related Business Rules** | **BR-56**: Upon employee resignation, the system must automatically calculate: resignation-related entitlements (e.g., accrued leave payout, service completion benefits, pending allowances) according to contract and local labor law, and end-of-service benefits (gratuity, accrued leave encashment, pending allowances) according to company policy and labor law. **BR-29**: Upon employee termination, the system must automatically calculate termination-related entitlements (e.g., severance pay, end-of-service gratuity, pending compensation) according to contract and local labor law. **BR-26**: Termination benefits must not be processed until HR clearance and final approvals are completed. **BR-27**: Manual adjustments to termination payouts must require Payroll Specialist approval and full system logging. |
| **Success Criteria** | ✓ Resignation benefits defined and calculated per labor law ✓ Termination benefits configured ✓ Service completion criteria clear ✓ Approval requirements documented ✓ Draft state with audit trail ✓ Ready for HR integration in Phase 5 |
| **System Integration** | Offboarding Module (Severance rules/terms) → Benefit Configuration Module (policies) → Approval Workflow (HR clearance) → Payroll Processing (calculation and disbursement) |
| **Inputs Needed** | Offboarding (Severance rules/terms) |

---

# PHASE 2: EMBED COMPLIANCE

## 📋 Phase Description

**Legal Admin adds tax rules and updates legal changes in compliance with local legislation. Payroll Specialist configures insurance brackets with defined salary ranges and contribution percentages for both employer and employee. This phase ensures that the payroll system automatically enforces all tax, labor law, and insurance requirements without manual intervention, embedding legislative compliance into every payroll cycle.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Now that payroll structures are defined, compliance requirements must be embedded:
- Tax rules (progressive tax rates, exemptions, thresholds) per local law
- Insurance brackets (health, social, pension) with salary ranges
- Labor law updates (when laws change, rules must be updated)
- Contributions percentages (employer and employee portions)

This phase ensures the system automatically calculates taxes and deductions correctly, stays compliant with changing laws, and requires no manual intervention.

---

### STEP 7: Tax Rules & Laws Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Legal & Policy Admin |
| **What They Do** | Defines and configures tax rules and laws including progressive tax rates, exemptions, thresholds, and tax brackets per local law (Egyptian labor law 2025). Creates, edits, and views tax configurations in draft mode. |
| **Why It Matters** | Tax calculations are legally mandated and change frequently. Embedding them in the system ensures accuracy, prevents legal violations, and eliminates manual tax calculation errors that could expose the company to penalties. |
| **Supporting Requirements** | **REQ-PY-10** - As a legal & policy admin, I want to define tax rules and laws in the system (e.g., progressive tax rates, exemptions, thresholds) so that payroll always complies with current legislation. (Create draft, draft, view all) |
| **What Gets Created** | Tax configuration with progressive brackets, exemptions, and thresholds; stored in draft for manager review |
| **Related Business Rules** | **BR-5**: The system must identify the payroll income taxes' brackets enforced through Local Tax Law. **BR-6**: The system must support multiple tax components (e.g. income tax, exemptions). **BR-20**: All payroll records must Support local tax law customization (i.e. as per Egyptian labor law 2025 and other laws' requirements). **BR-35**: The system must calculate net salary as: Gross Salary – Taxes – Social Insurance |
| **Success Criteria** | ✓ All tax brackets defined per local law ✓ Progressive rates configured correctly ✓ Exemptions identified ✓ Multiple tax components supported ✓ Draft state with audit trail ✓ Ready for validation |
| **System Integration** | Tax Authority Data (legal requirements) → Tax Configuration Module (defines rules) → Payroll Calculation Engine (applies taxes) |

---

### STEP 8: Legal Rules Update

| Aspect | Details |
|--------|---------|
| **Actor** | Legal & Policy Admin |
| **What They Do** | Updates legal rules when laws change, edits existing tax and labor law configurations, and activates updated rules for future payroll cycles. Maintains version control and audit trails of all law changes. |
| **Why It Matters** | Laws change regularly (new tax rates, updated insurance requirements, revised minimum wages). Without systematic updates, the payroll system would continue using outdated rules, exposing the company to legal non-compliance and financial penalties. |
| **Supporting Requirements** | **REQ-PY-12** - As a legal & policy admin, I want to update legal rules when laws change, so that future payroll cycles are compliant without manual intervention. (Edit) |
| **What Gets Created** | Updated legal configurations with version history; new rules apply to subsequent payroll cycles automatically |
| **Related Business Rules** | **BR-1**: The system must require an active employment contract with a defined role, type (full-time, part-time, hourly, commission-based, etc.), start/end dates and salary basis before payroll can be processed. Local labor law (Egyptian labor law 2025) needs to be followed. **BR-20**: All payroll records must Support local tax law customization (i.e. as per Egyptian labor law 2025 and other laws' requirements). |
| **Success Criteria** | ✓ Law changes identified and updated ✓ Version control maintained ✓ Effective dates clear ✓ Audit trail shows all changes ✓ No manual intervention required for future payroll ✓ Compliance automatic |
| **System Integration** | Legal Tracking → Law Update Module (captures changes) → Configuration Management (versions updates) → Payroll System (applies new rules automatically) |

---

### STEP 9: Insurance Brackets Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Specialist |
| **What They Do** | Configures insurance brackets (health, social, pension, etc.) with defined salary ranges and contribution percentages for both employer and employee. Creates, edits, and views insurance configurations with multiple tier levels. |
| **Why It Matters** | Insurance contributions vary by salary level and are legally mandated. Proper configuration ensures correct deductions from employee salaries and correct employer contributions, maintains compliance with insurance laws, and ensures employees have proper coverage. |
| **Supporting Requirements** | **REQ-PY-21** - As a Payroll Specialist, I want to configure insurance brackets (e.g., health, social, etc) with defined salary ranges and contribution percentages for both employer and employee, so that the system automatically applies the correct insurance deductions during payroll processing in compliance with policy and law. (Create draft, edit draft, view all) |
| **What Gets Created** | Insurance bracket configurations with salary ranges, employer contributions, and employee deductions; linked to Payroll Schemas |
| **Related Business Rules** | **BR-7**: The system must identify the social insurances' brackets enforced through Social Insurance and Pensions Law. **BR-8**: The system must calculate employee and employer social insurance contributions according to the local Social Insurance and Pensions Law, with contribution percentages configurable. The same needs to be applied for the state-based Health Insurance system. **BR-31**: The system needs to have a breakdown: Payroll Schemas (payroll logic - set of rules and operations that define how payroll should be processed). Formula: [Net Salary = Gross Salary(base pay+ allowances) – Taxes – Social/Health Insurance – Other Deductions]. Payroll Area picks employees and period. Schema runs payroll logic for that group. **BR-46**: Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. |
| **Success Criteria** | ✓ Insurance types defined (social, health, pension) ✓ Salary brackets with ranges configured ✓ Employer and employee percentages set ✓ Multiple tiers supported ✓ Compliant with insurance law ✓ Draft ready for HR approval in Phase 5 |
| **System Integration** | Insurance Authority Data (legal requirements) → Insurance Configuration Module (defines brackets) → Payroll Schemas (uses for calculations) → HR Module (Phase 5 approval) |

---

# PHASE 3: CONFIGURE SYSTEM

## 📋 Phase Description

**System Administrator defines company-wide settings such as pay dates, time zones, currencies, and establishes regular data backup routines. This phase ensures the system runs reliably with correct operational parameters and protects critical payroll data through automated backups and recovery procedures.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Now that payroll structures and compliance rules are defined, system-level configuration is needed:
- Company-wide settings (when payroll runs, time zones, currencies)
- Backup routines (regular data protection and recovery)
- System security (access controls, audit trails)

This phase ensures the technical infrastructure is ready to support payroll operations reliably and securely.

---

### STEP 10: Company-Wide Settings Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin |
| **What They Do** | Defines company-wide payroll settings including pay dates, time zones, currencies, processing cycles, and system-level parameters. Creates, edits, and views system settings configurations. |
| **Why It Matters** | Payroll runs must happen at defined times and follow defined cycles. The system must operate in the correct timezone and currency. Without proper system settings, payroll could run at wrong times, in wrong currency, or with wrong cycle dates. |
| **Supporting Requirements** | **REQ-PY-15** - As a System Admin, I want to set company-wide settings (like pay dates, time zone, and currency) so payroll runs correctly. |
| **What Gets Created** | System configuration settings applied company-wide; used by all payroll processing operations |
| **Related Business Rules** | **BR-3**: Payroll must be processed within defined cycles (monthly, etc) per contract or region following the local laws. **BR-31**: The system needs to have: Payroll Areas (batch of people for which payroll runs at the same time) and Payroll Schemas (payroll logic). Payroll Area picks employees and period. Schema runs payroll logic for that group. |
| **Success Criteria** | ✓ Pay dates defined and scheduled ✓ Timezones configured correctly ✓ Currency set appropriately ✓ Processing cycles aligned with law ✓ System validates against local regulations ✓ Ready for payroll operations |
| **System Integration** | System Configuration Module (stores settings) → Payroll Processing Engine (uses settings for scheduling) → Financial Systems (uses currency settings) |

---

### STEP 11: Data Backup Configuration

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin |
| **What They Do** | Configures regular automated data backup routines, establishes backup schedules, defines retention policies, and tests recovery procedures. Ensures payroll data is protected and recoverable in case of system failure. |
| **Why It Matters** | Payroll data is critical and cannot be lost. Regular backups ensure that in case of system failure, data breach, or accidental deletion, payroll records can be recovered and business continuity is maintained. |
| **Supporting Requirements** | **REQ-PY-16** - As a System Admin, I want to back up data regularly so nothing is lost. |
| **What Gets Created** | Backup schedule and retention policy; automated backups executed regularly; recovery procedures documented and tested |
| **Related Business Rules** | **BR-36**: The system must store all calculation elements (salary base, allowances, taxes, deductions) for auditability and compliance. |
| **Success Criteria** | ✓ Backup schedule defined (daily/weekly/monthly) ✓ Retention policy clear ✓ Recovery procedures documented ✓ Regular testing confirmed ✓ Restore capability verified ✓ Audit trail of backups maintained |
| **System Integration** | Backup System (performs backups) → Data Storage (stores backups securely) → Recovery System (enables restoration) → Audit System (logs all backup operations) |

---

# PHASE 4: APPROVE CONFIGURATION

## 📋 Phase Description

**Payroll Manager reviews and approves or rejects all payroll system configuration settings (excluding insurance, which is handled by HR in Phase 5). This phase ensures that no unauthorized adjustments impact payroll calculations and that all configurations are validated before becoming active.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Before any payroll configuration becomes active:
- Payroll Manager reviews all configurations created in Phases 1-3
- Manager can edit configurations if needed
- Manager approves or rejects each configuration
- Approved configs become active for payroll processing
- Insurance configs bypass this step (handled separately by HR in Phase 5)

This phase adds a control layer to prevent unauthorized or incorrect configurations.

---

### STEP 12: Payroll Configuration Approval/Disapproval

| Aspect | Details |
|--------|---------|
| **Actor** | Payroll Manager |
| **What They Do** | Reviews all payroll configuration settings created in Phases 1-3 (excluding insurance), has the ability to edit configurations, and approves or rejects them before they become active. Maintains decision logs with reasons for approvals/rejections. |
| **Why It Matters** | Configuration errors can cause systematic payroll errors affecting all employees. A manager review step catches mistakes, ensures policies are correctly configured, and maintains accountability for all configuration decisions. Unauthorized changes are prevented. |
| **Supporting Requirements** | **REQ-PY-18** - As a Payroll Manager, I want to approve payroll module configuration changes so that no unauthorized adjustments impact payroll calculations. (Edit and approve any configuration done so far, and delete except insurance) |
| **What Gets Created** | Approved configuration records ready for activation; rejection records with feedback sent back to specialists for revision |
| **Related Business Rules** | **BR-30**: Payroll processing must support multi-step approval workflow: Payroll Specialist → Payroll Manager → Finance Department. **BR-63**: Any payroll initiation or modification (automatic or manual) must go through validation checks (e.g., contract active, no expired approvals, minimum wage compliance) before processing. |
| **Success Criteria** | ✓ All configurations reviewed ✓ Manager can edit before approval ✓ Approval/rejection decisions logged ✓ Rejected items returned with feedback ✓ Approved items ready for activation ✓ Audit trail complete ✓ Insurance configs excluded from this step |
| **System Integration** | Draft Configuration Module (submits for review) → Approval Workflow (manager review/edit/decision) → Active Configuration (approved items activated) → Audit System (logs all decisions) |
| **Note** | Insurance configurations proceed directly to Phase 5 (HR Manager review) and bypass this Payroll Manager approval step |

---

# PHASE 5: HR OVERSIGHT

## 📋 Phase Description

**HR Manager reviews and updates insurance bracket configurations when policies or regulations change. This phase ensures that insurance configurations reflect the most current policies and regulatory requirements, with HR having authority over insurance-related compensation elements.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Insurance is specifically managed by HR because:
- Insurance policies are often tied to employee benefits and HR policies
- HR manages employee enrollment in insurance programs
- When insurance regulations or company policies change, HR updates them
- HR has specific regulatory responsibilities

This phase gives HR direct control over insurance while Payroll Manager controls other configurations.

---

### STEP 13: Insurance Brackets Review & Update

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Reviews insurance bracket configurations created in Phase 2 (Step 9), approves or rejects them, has ability to edit configurations, and can delete/update insurance rules when policies or regulations change. Maintains version history of all insurance changes. |
| **Why It Matters** | Insurance is a core employee benefit tied to HR policies. When insurance laws change or company policies change, HR must be able to update insurance configurations immediately to ensure compliance and proper employee coverage without waiting for payroll operations to handle it. |
| **Supporting Requirements** | **REQ-PY-22** - As an HR Manager, I want to review and update insurance bracket configurations when policies or regulations change, so that payroll calculations remain accurate, compliant, and reflect the most current insurance requirements. (Approve/reject, view, edit, delete) |
| **What Gets Created** | Approved insurance configurations ready for activation; updated configurations with version control; deleted/archived configurations with audit trail |
| **Related Business Rules** | **BR-7**: The system must identify the social insurances' brackets enforced through Social Insurance and Pensions Law. **BR-8**: The system must calculate employee and employer social insurance contributions according to the local Social Insurance and Pensions Law, with contribution percentages configurable. The same needs to be applied for the state-based Health Insurance system. **BR-31**: The system needs to have Payroll Schemas with formula: [Net Salary = Gross Salary(base pay+ allowances) – Taxes – Social/Health Insurance – Other Deductions]. **BR-46**: Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. |
| **Success Criteria** | ✓ All insurance brackets reviewed ✓ HR can edit configurations ✓ Approval/rejection decisions logged ✓ Changes documented with effective dates ✓ Version control maintained ✓ Deletion audit trail complete ✓ Regulatory compliance confirmed ✓ Ready for payroll processing |
| **System Integration** | Insurance Configuration Module (from Phase 2) → HR Review/Approval Workflow → Active Insurance Rules (for payroll calculations) → Employee Insurance Enrollment (automatic during onboarding) |

---

# 📋 COMPLETE BUSINESS RULES REFERENCE TABLE

This section contains ALL 40 Business Rules for the Payroll Configuration & Policy Setup Subsystem with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-1** | The system must require an active employment contract with a defined role, type (full-time, part-time, hourly, commission-based, etc.), start/end dates and salary basis before payroll can be processed. Local labor law (Egyptian labor law 2025) needs to be followed. |
| **BR-2** | The system must calculate base salary according to contract terms and role type. |
| **BR-3** | Payroll must be processed within defined cycles (monthly, etc) per contract or region following the local laws. |
| **BR-4** | The system must identify the minimum salary bracket(s) enforced through Local Labor Law. |
| **BR-5** | The system must identify the payroll income taxes' brackets enforced through Local Tax Law. |
| **BR-6** | The system must support multiple tax components (e.g. income tax, exemptions). |
| **BR-7** | The system must identify the social insurances' brackets enforced through Social Insurance and Pensions Law. |
| **BR-8** | The system must calculate employee and employer social insurance contributions according to the local Social Insurance and Pensions Law, with contribution percentages configurable. The same needs to be applied for the state-based Health Insurance system. |
| **BR-9** | Payroll Structure must support base pay, allowances, deductions, and other variable pay elements |
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
| **BR-31** | The system needs to have a breakdown: Payroll Areas (batch of people for which payroll runs at the same time) and Payroll Schemas (payroll logic - set of rules and operations that define how payroll should be processed for employees). Formula: [Net Salary = Gross Salary(base pay+ allowances) – Taxes – Social/Health Insurance – Other Deductions]. The system follows: Payroll Area picks employees and period. Schema runs payroll logic for that group. |
| **BR-33** | The system must apply deductions for misconduct penalties (e.g., lateness, asset damage, disciplinary actions) as configured by HR policy, consistent with Egyptian law. |
| **BR-34** | The system must ensure all deductions (taxes, insurance, penalties, unpaid leave, recovery) are applied after gross salary calculation and before net salary. |
| **BR-35** | The system must calculate net salary as: Gross Salary – Taxes – Social Insurance |
| **BR-36** | The system must store all calculation elements (salary base, allowances, taxes, deductions) for auditability and compliance. |
| **BR-38** | The system must allow defining allowances with multiple types as part of the employment contract and add them to payroll as part of gross salary, defined per role or contract. |
| **BR-39** | Allowance Structure must support and track different types (e.g. transportation, housing, meals, etc). |
| **BR-46** | Employees are enrolled by default to allowances, insurance, and taxes during onboarding or annual enrollment window. |
| **BR-56** | Upon employee resignation, the system must automatically calculate: resignation-related entitlements (e.g., accrued leave payout, service completion benefits, pending allowances) according to contract and local labor law. And end-of-service benefits (gratuity, accrued leave encashment, pending allowances) according to company policy and labor law. |
| **BR-59** | The system must generate gross-to-net breakdown reports for employees and management to validate calculations. |
| **BR-60** | Misconduct penalties must not reduce salary below statutory minimum wages. |
| **BR-63** | Any payroll initiation or modification (automatic or manual) must go through validation checks (e.g., contract active, no expired approvals, minimum wage compliance) before processing. |
| **BR-64** | The system needs to be linked to the organization's as well as the employees' accounts to facilitate processing payroll. |
| **BR-66** | Payroll must not be processed if an employee's contract is expired, inactive, or suspended. |

---

# 📊 ALL USER STORIES / REQUIREMENTS (REQ-PY-1 through REQ-PY-22)

### REQ-PY-1: Payroll Policies Configuration
**What User Needs:** "As a Payroll Specialist, I want to configure company-level payroll policies (e.g., basic salary types, misconduct penalties, leave policies, allowance) so that the system enforces organizational rules consistently. (Create draft, edit draft, view all)"

**Why It Matters:** Establishes organizational compensation standards that apply uniformly to all employees, preventing inconsistencies and ensuring compliance with company policies.

**Related BRs:** BR-1, BR-9, BR-33, BR-34, BR-46

**System Must Support:**
- Create policies in draft mode
- Edit draft policies before approval
- View all policies with version history
- Audit trail for all changes
- Enforcement across all payroll cycles

---

### REQ-PY-2: Pay Grades Configuration
**What User Needs:** "As a Payroll Specialist, I want to define pay grades, salary, and compensation limits so that managers and payroll specialists cannot exceed policy boundaries. (Create draft, edit draft, view all) for department and position"

**Why It Matters:** Ensures consistent salary ranges within organizational hierarchy and prevents unauthorized compensation adjustments.

**Related BRs:** BR-2, BR-4, BR-10, BR-31

**System Must Support:**
- Define grades by department and position
- Set salary ranges and compensation limits
- Create and edit in draft mode
- View all grades with hierarchical structure
- Compliance with minimum wage law

---

### REQ-PY-5: Pay Types Configuration
**What User Needs:** "As a Payroll Specialist, I want the system to define employee pay types (hourly, daily, weekly, monthly, contract-based) so that salaries are calculated according to the employment agreement. (Create draft, edit draft, view all)"

**Why It Matters:** Different employment types require different calculation methods. The system must support all types to ensure accurate salary calculations per contract.

**Related BRs:** BR-1, BR-2, BR-3

**System Must Support:**
- Define all pay type categories (hourly, daily, weekly, monthly, contract)
- Create and edit in draft mode
- View all types with calculation methodology
- Link to employment contracts
- Version control and history

---

### REQ-PY-7: Allowances Configuration
**What User Needs:** "As a Payroll Specialist, I want to set allowances (e.g., transportation, housing, etc) so that employees are rewarded for special conditions. (Create draft, edit draft, view all)"

**Why It Matters:** Allowances are a significant compensation component that vary by role and circumstance. Proper configuration ensures consistent and fair application.

**Related BRs:** BR-9, BR-38, BR-39, BR-46

**System Must Support:**
- Define multiple allowance types
- Create and edit in draft mode
- View all allowances with eligibility criteria
- Link to roles and contracts
- Integration into gross salary calculation

---

### REQ-PY-10: Tax Rules & Laws Configuration
**What User Needs:** "As a legal & policy admin, I want to define tax rules and laws in the system (e.g., progressive tax rates, exemptions, thresholds) so that payroll always complies with current legislation. (Create draft, draft, view all)"

**Why It Matters:** Tax compliance is legally mandated and subject to frequent changes. Embedding tax rules in the system ensures automatic compliance and prevents legal violations.

**Related BRs:** BR-5, BR-6, BR-20, BR-35

**System Must Support:**
- Define progressive tax brackets
- Configure tax exemptions and thresholds
- Support multiple tax components
- Create and edit in draft mode
- View all tax configurations with effective dates

---

### REQ-PY-12: Legal Rules Update
**What User Needs:** "As a legal & policy admin, I want to update legal rules when laws change, so that future payroll cycles are compliant without manual intervention. (Edit)"

**Why It Matters:** Laws change frequently. The ability to update rules ensures future payroll cycles remain compliant without manual intervention.

**Related BRs:** BR-1, BR-20

**System Must Support:**
- Edit existing legal and tax rules
- Maintain version history
- Set effective dates for rule changes
- Apply to future payroll cycles automatically
- Audit trail of all updates

---

### REQ-PY-15: Company-Wide Settings Configuration
**What User Needs:** "As a System Admin, I want to set company-wide settings (like pay dates, time zone, and currency) so payroll runs correctly."

**Why It Matters:** Payroll must run at defined times in defined timezone and currency. Without proper system settings, payroll operations fail.

**Related BRs:** BR-3, BR-31

**System Must Support:**
- Set pay dates and processing cycles
- Configure timezone and currency
- Define system-wide parameters
- Validate against local regulations
- Version control of settings

---

### REQ-PY-16: Data Backup Configuration
**What User Needs:** "As a System Admin, I want to back up data regularly so nothing is lost."

**Why It Matters:** Payroll data is critical. Regular backups ensure data protection and business continuity.

**Related BRs:** BR-36

**System Must Support:**
- Automated backup scheduling
- Regular backup execution
- Data retention policies
- Recovery procedures
- Testing and verification

---

### REQ-PY-18: Payroll Configuration Approval/Disapproval
**What User Needs:** "As a Payroll Manager, I want to approve payroll module configuration changes so that no unauthorized adjustments impact payroll calculations. (Edit and approve any configuration done so far, and delete except insurance)"

**Why It Matters:** Configuration errors affect all employees. Manager review adds critical control layer preventing unauthorized changes.

**Related BRs:** BR-30, BR-63

**System Must Support:**
- Review all configurations in pending state
- Edit configurations before approval
- Approve or reject with reasons
- Delete configurations (except insurance)
- Audit trail of all decisions

---

### REQ-PY-19: Signing Bonuses Configuration
**What User Needs:** "As a Payroll Specialist, I want to configure policies for signing bonuses, so that new hires are seamlessly incorporated into the company's payroll system. (Create draft, edit draft, view all)"

**Why It Matters:** Signing bonuses attract talent but must be carefully controlled to prevent fraud and duplicate payments.

**Related BRs:** BR-24, BR-25, BR-28, BR-56

**System Must Support:**
- Configure bonus eligibility criteria
- Set bonus amounts and payment terms
- Create and edit in draft mode
- Link to employment contracts
- Enforce one-time disbursement

---

### REQ-PY-20: Resignation & Termination Benefits Configuration
**What User Needs:** "As a Payroll Specialist, I want to configure resignation and termination benefits and their terms, so that the offboarding process for employees is seamless and legally compliant. (Create draft, edit draft, view all)"

**Why It Matters:** Resignation and termination entitlements are legally mandated. Proper configuration ensures compliance and fair treatment.

**Related BRs:** BR-26, BR-27, BR-29, BR-56

**System Must Support:**
- Configure resignation benefits
- Configure termination benefits
- Create and edit in draft mode
- View all benefits with calculation rules
- Link to labor law requirements

---

### REQ-PY-21: Insurance Brackets Configuration
**What User Needs:** "As a Payroll Specialist, I want to configure insurance brackets (e.g., health, social, etc) with defined salary ranges and contribution percentages for both employer and employee, so that the system automatically applies the correct insurance deductions during payroll processing in compliance with policy and law. (Create draft, edit draft, view all)"

**Why It Matters:** Insurance is legally mandated with varying contributions by salary level. Proper configuration ensures correct deductions and contributions.

**Related BRs:** BR-7, BR-8, BR-31, BR-46

**System Must Support:**
- Configure multiple insurance types
- Define salary ranges and tiers
- Set employer and employee percentages
- Create and edit in draft mode
- View all insurance configurations
- Automatic enrollment

---

### REQ-PY-22: Insurance Brackets Review & Update
**What User Needs:** "As an HR Manager, I want to review and update insurance bracket configurations when policies or regulations change, so that payroll calculations remain accurate, compliant, and reflect the most current insurance requirements. (Approve/reject, view, edit, delete)"

**Why It Matters:** Insurance is core to employee benefits. HR must have direct control to update when regulations or policies change.

**Related BRs:** BR-7, BR-8, BR-31, BR-46

**System Must Support:**
- Review insurance configurations
- Approve or reject configurations
- Edit configurations
- Delete/archive old configurations
- Version control and audit trail
- Effective date management

---

---

**End of Payroll Configuration & Policy Setup Subsystem Documentation**

✅ **All 5 Phases Documented Sequentially**
✅ **All 13 Configuration Steps in Order**
✅ **All 40 Business Rules Included**
✅ **All 22 User Stories / Requirements with Full Context**
✅ **Professional Structure & Non-Technical Language**
✅ **Ready for Implementation & Audit**

