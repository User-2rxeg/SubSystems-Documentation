# RECRUITMENT SUBSYSTEM - COMPLETE DOCUMENTATION

---

## 📌 SUBSYSTEM OVERVIEW & DESCRIPTION

**Module Purpose:** The Recruitment, Onboarding, Offboarding Subsystem manages the entire employee lifecycle, from attracting and hiring talent, through integrating new employees, to facilitating structured and compliant separations. It ensures that hiring, onboarding, and exit processes are efficient, auditable, and integrated across HR, IT, and payroll systems.

**Why This Matters:** In traditional HR systems, recruitment happens in one tool, onboarding in another, and offboarding in spreadsheets—leading to data inconsistencies, manual handoffs, and compliance risks. This integrated subsystem connects all three phases into a seamless pipeline where data flows automatically from "we need to hire someone" through "welcome to the team" to "thanks for your service" without manual re-entry or lost information.

**Integration Philosophy:** The subsystem automates key HR activities, enhances candidate and employee experiences, and maintains compliance with organizational and legal standards. By connecting recruitment pipelines to onboarding workflows and offboarding checklists, it guarantees data consistency, seamless transitions, and controlled access management throughout the employment journey. This module is functionally divided into three core processes, which are tightly integrated with the Employee Profile, Organizational Structure and Payroll subsystems.

### 🎯 What Does This Subsystem Do? (Simple Explanation)

Think of this subsystem as an intelligent employee lifecycle management assistant that handles three critical phases:

**Phase 1 - Recruitment (Getting the Right People):**
- **Standardizes job postings** using templates and structured job descriptions across the organization
- **Automates candidate tracking** through every stage from application to offer acceptance
- **Streamlines evaluations** by coordinating interview panels, scheduling, and scoring
- **Manages communications** with automated candidate status updates and notifications
- **Ensures compliance** with privacy laws and data consent requirements (GDPR)
- **Generates offers** electronically with approval workflows and digital signatures
- **Triggers onboarding** automatically once candidates accept offers

**Phase 2 - Onboarding (Getting People Ready to Work):**
- **Creates onboarding checklists** automatically when offer is accepted
- **Collects required documentation** (ID, contracts, certifications) from new hires
- **Provisions system access** (email, payroll, internal systems) on Day 1
- **Reserves resources** (laptop, desk, access cards) before start date
- **Initiates payroll** automatically based on contract signing date
- **Processes signing bonuses** according to contract terms
- **Tracks progress** with automated reminders to new hires and HR teams

**Phase 3 - Offboarding (Managing Departures Professionally):**
- **Handles resignations** with structured approval workflows
- **Manages terminations** based on performance data with due process
- **Recovers company assets** through multi-department clearance checklists
- **Revokes system access** automatically to maintain security
- **Calculates final settlements** (unused leave, deductions, severance)
- **Terminates benefits** as of notice period end
- **Ensures compliance** with labor laws and company policies

**Real-World Example:**
Instead of HR teams manually tracking hundreds of applicants in spreadsheets, chasing down IT to set up email accounts, and remembering to revoke access when someone leaves, this system automates the entire journey with full auditability, consistency, and compliance built in. When Sarah applies for a job, the system tracks her through interviews, generates her offer, creates her employee profile when she accepts, provisions her laptop and email on Day 1, processes her first paycheck, and—years later when she resigns—ensures every asset is returned and every system access is revoked before her final paycheck is calculated.

---

## 📊 EMPLOYEE LIFECYCLE FLOW (RECRUITMENT → ONBOARDING → OFFBOARDING)

**The Employee Lifecycle Subsystem represents the logical progression of activities through three interconnected phases that form a closed-loop system supporting continuous HR operations. This ensures traceability, efficiency, and security across the entire employee journey from "candidate" to "new hire" to "former employee."**

### 🔍 What This Process Does (Simplified)

This is a complete employee lifecycle that:

**Phase 1: Recruitment (REC) - Acquisition & Offer**
This phase begins with job design and posting, progresses through candidate application, tracking, evaluation, and communication, and concludes with job offer generation and acceptance. Successful offer acceptance automatically triggers pre-boarding tasks and transitions data to the Onboarding phase.

**Phase 2: Onboarding (ONB) - Integration & Provisioning**
The onboarding phase focuses on transforming the accepted candidate into an active employee. It includes creating onboarding task checklists, collecting documentation, provisioning access, assigning resources, and initiating payroll and benefits. Automated notifications guide both HR teams and new hires to ensure readiness before Day 1.

**Phase 3: Offboarding (OFF) - Separation & Clearance**
This phase manages the structured and compliant exit of employees. It covers resignation or termination initiation, clearance workflows, access revocation, and final settlements. Integration with payroll, IT, and facilities ensures that all assets are recovered, benefits are closed, and access rights are securely revoked.

**Together, these phases form a closed-loop lifecycle** that supports continuous HR operations, linking recruitment decisions directly to onboarding preparation and offboarding compliance. This ensures traceability, efficiency, and security across the entire employee journey.

---

### 📋 Complete Workflow Overview

| Phase | # of Steps | Primary Outcome |
|-------|-----------|-----------------|
| **Recruitment** | 12 steps | Signed offer letter → Onboarding triggered |
| **Onboarding** | 7 steps | Active employee profile → Payroll initiated |
| **Offboarding** | 7 steps | Cleared exit → Final settlement processed |

**Why This Matters:** Each phase hands off data to the next automatically. When a candidate signs an offer (Recruitment), the system immediately creates onboarding tasks (Onboarding). When an employee resigns (Offboarding), the system triggers asset recovery and final pay calculations using data from the employee's entire lifecycle.

---

# 📚 KEY DEFINITIONS: UNDERSTANDING REQUIREMENTS, USER STORIES, FLOWS & BUSINESS RULES

## What Are These Different Types, and Why Do They Matter?

### 🎯 REQUIREMENTS (General Concept)

**What it is:** A statement of something the system MUST do or support.

**Example:** "The system must track candidate applications through defined stages"

**Why it matters:** Requirements define what functionality recruiters and candidates need from the system.

---

### 👤 USER STORIES (REC)

**What it is:** A specific need written from a user's perspective showing WHO wants something, WHAT they want, and WHY.

**Format:** "As a [ROLE], I want [ACTION], so that [BENEFIT]"

**Example:** "As an HR Manager, I want to define standardized job description templates, so that postings are consistent."

**Real-World Translation:** Maria, an HR Manager, creates a template for "Software Engineer" positions once. Now whenever anyone posts a Software Engineer job, they use this template—ensuring consistency in requirements, qualifications, and job descriptions across all departments.

**Why it matters:** 
- Makes requirements human-centered (focuses on actual user needs)
- Clear about who uses it and why (helps developers understand context)
- Can be tested ("Can Maria successfully create and reuse job templates?")
- Links to business value (why we're building this feature)

---

### 🔧 BUSINESS RULES (BR)

**What it is:** A specific technical/operational rule that the system MUST enforce.

**Example:** "BR-9: Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired)."

**Real-World Translation:** "Every candidate application in the system must move through specific stages in order, and the system must track which stage they're currently in. You can't skip stages or lose track of where candidates are."

**Why it matters:**
- Defines exact logic developers must code
- Ensures consistency (all candidates follow the same process)
- Creates auditability (complete history of candidate progression)
- Links to legal/compliance requirements (GDPR, equal opportunity)

---

### 🌊 FLOWS (Process Flows)

**What it is:** A step-by-step description of HOW the system works through the recruitment process.

**Example:**
```
HR creates job template
  → HR publishes job posting
  → Candidate applies with CV
  → System tracks candidate through stages
  → HR schedules interviews
  → Panel provides feedback
  → HR generates offer
  → Candidate accepts electronically
  → System triggers onboarding
```

**Real-World Translation:** The entire journey from "we need to hire someone" to "welcome aboard, new employee."

**Why it matters:**
- Shows sequence of operations (order matters)
- Helps everyone understand the big picture
- Identifies where things can fail (what if candidate doesn't respond?)
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
| **REC-008 (User Story)** | "As a HR Employee, I want to track candidates through each stage of the hiring process, so that I can manage progress." |
| **BR-9 (Business Rule)** | "Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired)." |
| **FLOW (Process)** | (1) Candidate applies, (2) HR moves to "Screening", (3) HR moves to "Interview", (4) Panel scores candidate, (5) HR moves to "Offer", (6) System tracks each transition |
| **IMPLEMENTATION** | Developer codes: "Create candidate record with status field. Allow status updates only to next valid stage. Log all transitions with timestamp and user. Trigger notifications on status change." |

---

**Why This Structure Matters for System Implementation:**

1. **User Stories** ensure developers build what recruiters and candidates actually need
2. **Business Rules** ensure every hiring policy is enforced consistently
3. **Flows** ensure everything happens in the right order with proper controls
4. **Together** they create a complete, compliant, auditable recruitment system

---

# 📊 COMPREHENSIVE REQUIREMENTS MATRIX

## Overview of All Requirements by Phase

| Phase | Requirement Name | US ID | BR IDs |
|-------|------------------|-------|--------|
| **Job Design & Posting** | Standardized Job Templates | REC-003 | BR-2 |
| **Job Design & Posting** | Hiring Process Templates | REC-004 | BR-9 |
| **Job Design & Posting** | Career Page Publishing | REC-023 | BR-6 |
| **Candidate Application & Communication** | CV Upload & Application | REC-007 | BR-12 |
| **Candidate Application & Communication** | Application Status Updates | REC-017 | BR-27, BR-36 |
| **Candidate Application & Communication** | Automated Rejection Notifications | REC-022 | BR-36, BR-37 |
| **Candidate Tracking & Evaluation** | Pipeline Stage Tracking | REC-008 | BR-9, BR-11 |
| **Candidate Tracking & Evaluation** | Interview Scheduling | REC-010 | BR-19 |
| **Candidate Tracking & Evaluation** | Interview Feedback & Scoring | REC-011 | BR-10, BR-22 |
| **Candidate Tracking & Evaluation** | Structured Assessment Forms | REC-020 | BR-21, BR-23 |
| **Candidate Tracking & Evaluation** | Interview Panel Coordination | REC-021 | BR-19, BR-20 |
| **Candidate Tracking & Evaluation** | Referral Tagging | REC-030 | BR-14, BR-25 |
| **Recruitment Analytics** | Progress Monitoring | REC-009 | BR-33 |
| **Compliance & Background Checks** | Data Processing Consent | REC-028 | BR-28, NFR-33 |
| **Offers & Hiring Decisions** | Offer Management & Approvals | REC-014 | BR-26 |
| **Offers & Hiring Decisions** | Electronic Offer Letters | REC-018 | BR-26, BR-37 |
| **Offers & Hiring Decisions** | Pre-boarding Task Triggers | REC-029 | BR-26 |

---

---

# PHASE 1: PREPARATION & TEMPLATES

## 📋 Phase Description

**HR Manager defines standardized job description templates and establishes hiring process templates for stages and progress updates. This foundational phase ensures consistency across all job postings and standardizes the candidate journey through predefined stages.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Setting up the foundation for recruitment:
- Create reusable job description templates (so every "Software Engineer" job looks consistent)
- Define hiring process stages (Application → Screening → Interview → Offer → Hired)
- Set up progress tracking (so system knows 50% complete = Interview stage)

Think of this as creating the blueprint before you start building.

---

### STEP 1: Define Standardized Job Description Templates

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Creates standardized job description templates with consistent structure for job details, qualifications, and skills. |
| **Why It Matters** | Ensures all job postings across the organization are professional, consistent, and complete. |
| **Supporting Requirements** | **REC-003**: As an HR Manager, I want to define standardized job description templates, so that postings are consistent. Each job requisition must include Job details (title, department, location, openings) and Qualifications and skills needed. |
| **What Gets Created** | Job description templates stored in system for reuse. |
| **Related Business Rules** | **BR-2**: Each job requisition must include Job details (title, department, location, openings) and Qualifications and skills needed. |
| **Inputs Needed** | Organizational Structure (Jobs/Positions) |
| **Downstream Systems** | Recruitment (Job Posting) |

---

### STEP 2: Establish Hiring Process Templates

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Defines hiring process templates with standardized stages and automatic progress percentage calculation. |
| **Why It Matters** | Creates consistent candidate journey and enables automated progress tracking. |
| **Supporting Requirements** | **REC-004**: As an HR Manager, I want to be able to establish hiring processes templates so that the system can automatically update progress percentage. Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired). |
| **What Gets Created** | Hiring process templates with defined stages and progress metrics. |
| **Related Business Rules** | **BR-9**: Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired). |
| **Inputs Needed** | None (System Configuration) |
| **Downstream Systems** | Recruitment (Candidate Tracking) |

---

---

# PHASE 2: JOB POSTING

## 📋 Phase Description

**HR Employee previews and publishes jobs on the company careers page with employer-brand content, ensuring openings look professional and are automatically posted to internal and external career sites upon approval.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Making jobs visible to candidates:
- HR reviews job posting before publishing
- System publishes to company careers page
- Posting includes branding and professional formatting
- Automatic distribution to job boards if configured

This is where the job goes live and candidates can see it.

---

### STEP 3: Preview and Publish Job Postings

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Previews job posting with employer branding and publishes to company careers page. |
| **Why It Matters** | Ensures job postings are professional, accurate, and visible to candidates. |
| **Supporting Requirements** | **REC-023**: As a HR Employee, I want to preview and publish jobs on the company careers page with employer-brand content, so openings look professional. |
| **What Gets Created** | Live job posting on company careers page and external job boards. |
| **Related Business Rules** | **BR-6**: The system must allow automatic posting of approved requisitions to internal and external career sites. |
| **Inputs Needed** | None |
| **Downstream Systems** | External Careers Page |

---

---

# PHASE 3: APPLICATION & CONSENT

## 📋 Phase Description

**Candidate uploads CV and applies for positions while providing consent for personal-data processing and background checks. This ensures compliance with privacy laws (GDPR) and creates the organization's talent pool.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Candidate applies for job:
- Candidate uploads resume/CV
- Candidate gives consent for data processing (GDPR compliance)
- System stores application in talent pool
- Application is ready for HR review

This is where candidates enter the system.

---

### STEP 4: CV Upload & Application Submission

| Aspect | Details |
|--------|---------|
| **Actor** | Candidate |
| **What They Do** | Uploads CV/resume and submits application for open position. |
| **Why It Matters** | Allows candidates to be considered for opportunities and creates talent pool. |
| **Supporting Requirements** | **REC-007**: As a Candidate, I want to upload my CV and apply for positions, so that I can be considered for opportunities. |
| **What Gets Created** | Candidate application record with CV stored in system. |
| **Related Business Rules** | **BR-12**: The system must support the storage/upload of applications with resumes, which creates the organization's talent pool. |
| **Inputs Needed** | Candidate CVs/Documents |
| **Downstream Systems** | Recruitment (Talent Pool) |

---

### STEP 5: Data Processing Consent

| Aspect | Details |
|--------|---------|
| **Actor** | Candidate |
| **What They Do** | Provides explicit consent for personal-data processing and background checks. |
| **Why It Matters** | Ensures GDPR compliance and legal authorization for storing candidate data. |
| **Supporting Requirements** | **REC-028**: As a Candidate, I want to give consent for personal-data processing and background checks, so the system remains compliant with privacy laws. |
| **What Gets Created** | Consent record logged and stored with application. |
| **Related Business Rules** | **BR-28**: Storing the talent pool needs to be authorized by applicants in the early stages of the recruitment process. **NFR-33**: All data handling must comply with GDPR and labor laws. |
| **Inputs Needed** | None (Candidate input) |
| **Downstream Systems** | Recruitment |

---

---

# PHASE 4: PIPELINE & TAGS

## 📋 Phase Description

**HR Employee tags candidates as referrals (giving them preferential treatment) and tracks candidates through each stage of the hiring process. System triggers automatic notifications on status changes.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Managing candidate pipeline:
- HR tags referrals for priority treatment
- HR moves candidates through stages (Screening → Shortlisting → Interview)
- System tracks all status changes
- Automatic notifications sent to candidates and hiring team

This is where HR actively manages the candidate journey.

---

### STEP 6: Referral Tagging

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Tags candidates as referrals to give them higher priority in pipeline. |
| **Why It Matters** | Allows organization to prioritize referred candidates per hiring policy. |
| **Supporting Requirements** | **REC-030**: As a HR Employee, I want to be able to tag candidates as referrals in order to give them a higher chance of having an earlier interview. |
| **What Gets Created** | Referral tag added to candidate record affecting prioritization. |
| **Related Business Rules** | **BR-14**: Electronic screening includes rule-based filters. **BR-25**: Tie-Breaking Rules should be predetermined and could be based on Internal candidate preference. |
| **Inputs Needed** | Candidate data, Referral source info |
| **Downstream Systems** | Recruitment |

---

### STEP 7: Candidate Stage Tracking

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Tracks candidates through defined hiring stages and updates status as candidates progress. |
| **Why It Matters** | Maintains visibility on all candidates and their current position in hiring process. |
| **Supporting Requirements** | **REC-008**: As a HR Employee, I want to track candidates through each stage of the hiring process, so that I can manage progress. |
| **What Gets Created** | Status updates logged for each candidate with timestamps and stage history. |
| **Related Business Rules** | **BR-9**: Applications must be tracked through defined stages. **BR-11**: Recruiters and hiring managers must be notified of status changes via alerts or workflow emails. |
| **Inputs Needed** | Hiring Process Template (REC-004) |
| **Downstream Systems** | Recruitment (Status Tracking) |

---

---

# PHASE 5: EVALUATION

## 📋 Phase Description

**HR Employee uses structured assessment and scoring forms per role, coordinates interviews, schedules/manages invitations, and collects panel feedback. Interview panels are coordinated with member availability and scoring is centralized.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Evaluating candidates systematically:
- HR uses standardized assessment forms (same criteria for all candidates)
- HR schedules interviews with calendar integration
- Interview panels receive automatic invites
- Candidates receive automatic notifications
- Panel members submit scores and feedback
- System aggregates scores for ranking

This ensures fair, consistent evaluation with full audit trail.

---

### STEP 8: Structured Assessment Forms Setup

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Uses pre-configured structured assessment and scoring forms specific to each role. |
| **Why It Matters** | Ensures evaluations are consistent, fair, and auditable across all candidates. |
| **Supporting Requirements** | **REC-020**: As an HR Employee, I want structured assessment and scoring forms per role, so evaluations are consistent and auditable. |
| **What Gets Created** | Assessment forms configured per role with predefined criteria. |
| **Related Business Rules** | **BR-21**: The system needs to allow/house the multiple assessment tools to be used. **BR-23**: Criteria used in interview assessment are pre-set and agreed upon. |
| **Inputs Needed** | Evaluation Criteria (REC-015) |
| **Downstream Systems** | Recruitment (Applicant Scoring) |

---

### STEP 9: Interview Scheduling & Management

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Schedules interviews by selecting time slots, panel members, and interview modes (in-person, video, phone). |
| **Why It Matters** | Streamlines interview coordination and ensures all parties are notified automatically. |
| **Supporting Requirements** | **REC-010**: As a HR Employee, I want to schedule and manage interview invitations, so that candidates are engaged efficiently. |
| **What Gets Created** | Interview scheduled with calendar invites sent to panel and candidate. |
| **Related Business Rules** | **BR-19 (a, c, d)**: Recruiters must be able to schedule interviews by selecting time slots, panel members, and modes. Interviewers must receive automatic calendar invites, and candidates must be notified automatically. |
| **Inputs Needed** | Time Management (TM), Email/Calendar systems |
| **Downstream Systems** | Notifications (N) |

---

### STEP 10: Interview Panel Coordination

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Coordinates interview panels by selecting members, checking availability, and managing scoring collection. |
| **Why It Matters** | Centralizes scheduling and feedback collection ensuring no gaps in evaluation. |
| **Supporting Requirements** | **REC-021**: As a HR Employee, I want to coordinate interview panels (members, availability, scoring), so scheduling and feedback collection are centralized. |
| **What Gets Created** | Panel configuration with member assignments and scoring responsibilities. |
| **Related Business Rules** | **BR-19 (a, b)**: Interview scheduling requires selecting panel members. **BR-20**: Panels need to possess the knowledge and/or training to conduct the needed interviews/selection tests. |
| **Inputs Needed** | Calendar/Time Management (Availability) |
| **Downstream Systems** | Recruitment (Interview Scheduling/Feedback) |

---

### STEP 11: Interview Feedback & Scoring

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Provides feedback and interview scores for scheduled interviews to support candidate filtration. |
| **Why It Matters** | Creates objective, documented evaluation for decision-making and compliance. |
| **Supporting Requirements** | **REC-011**: As an HR Employee, I want to be able to provide feedback/interview score for scheduled interviews for filtration. |
| **What Gets Created** | Feedback and scores logged to candidate record for ranking and decision. |
| **Related Business Rules** | **BR-10**: The system must allow adding comments and ratings at each stage. **BR-22**: Feedback at each stage must be submitted by the panel/interviewers to ensure accuracy. |
| **Inputs Needed** | Interview panel feedback/scores |
| **Downstream Systems** | Recruitment (Applicant Scoring) |

---

---

# PHASE 6: MONITORING & COMMUNICATION

## 📋 Phase Description

**HR Manager monitors recruitment progress across all open positions while candidates receive automatic status updates. System provides real-time visibility and automated candidate communications.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Keeping everyone informed:
- HR Manager sees dashboard of all open positions and candidate progress
- Candidates receive automatic emails when status changes
- Rejected candidates receive professional rejection notifications
- All communications are logged for audit trail

Transparency for all parties involved in recruitment.

---

### STEP 12: Recruitment Progress Monitoring

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Monitors recruitment progress across all open positions via dashboard and reports. |
| **Why It Matters** | Provides oversight on hiring pipeline health and identifies bottlenecks. |
| **Supporting Requirements** | **REC-009**: As an HR Manager, I want to monitor recruitment progress across all open positions, so that I stay informed. |
| **What Gets Created** | Progress dashboard showing all positions, candidates, stages, and metrics. |
| **Related Business Rules** | **BR-33**: Multiple reports could be generated like time-to-hire and source effectiveness. |
| **Inputs Needed** | Recruitment data (REC-008) |
| **Downstream Systems** | Recruitment |

---

### STEP 13: Candidate Status Updates

| Aspect | Details |
|--------|---------|
| **Actor** | Candidate |
| **What They Do** | Receives automatic updates about application status via email/portal. |
| **Why It Matters** | Keeps candidates informed and improves candidate experience. |
| **Supporting Requirements** | **REC-017**: As a Candidate, I want to receive updates about my application status, so that I know where I stand. |
| **What Gets Created** | Automated notification sent to candidate on every status change. |
| **Related Business Rules** | **BR-27**: Candidate Status Tracking must be easily visualized and up-to-date in real-time. **BR-36**: The system must send automated alerts/emails to candidates regarding status updates. |
| **Inputs Needed** | Recruitment (Candidate Status Tracking) |
| **Downstream Systems** | Candidate Self-Service Portal |

---

### STEP 14: Automated Rejection Notifications

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Sends automated rejection notifications using professional templates. |
| **Why It Matters** | Ensures candidates are informed respectfully and consistently while maintaining employer brand. |
| **Supporting Requirements** | **REC-022**: As a HR Employee, I want automated rejection notifications and templates, so candidates are informed respectfully and consistently. |
| **What Gets Created** | Rejection email sent with templated professional message. |
| **Related Business Rules** | **BR-36**: The system must support email templates for communication (e.g., rejection). **BR-37**: Communication logs must be stored in the applicant profile. |
| **Inputs Needed** | Recruitment (Rejection Reason/Template) |
| **Downstream Systems** | External Communication (Candidate Email) |

---

---

# PHASE 7: OFFER & TRANSITION

## 📋 Phase Description

**HR Manager manages job offers and approvals; HR Employee/Manager generates and sends e-signed offers; system sends automated rejections to non-selected candidates; and successful offer acceptance triggers pre-boarding tasks and onboarding module.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Closing the deal:
- HR generates offer letter with compensation and benefits
- Offer goes through approval workflow (HR → Finance → Legal if needed)
- Offer sent to candidate electronically for signature
- Candidate accepts offer with e-signature
- System automatically triggers onboarding checklist
- Rejected candidates notified professionally

This is where candidates become new hires.

---

### STEP 15: Offer Management & Approvals

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Manages job offer generation and secures required approvals before sending to candidate. |
| **Why It Matters** | Ensures offers are properly authorized and aligned with budget and policy. |
| **Supporting Requirements** | **REC-014**: As an HR Manager, I want to manage job offers and approvals, so that candidates can be hired smoothly. |
| **What Gets Created** | Approved offer ready for transmission to candidate. |
| **Related Business Rules** | **BR-26 (b, c)**: The system must support securing related parties' approval before sending out the offer. Once candidate acceptance is received, the next module (Onboarding) should be triggered. |
| **Inputs Needed** | Financial Approval (REC-027) |
| **Downstream Systems** | Onboarding |

---

### STEP 16: Electronic Offer Letter Generation & Signing

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee / HR Manager |
| **What They Do** | Generates, sends, and collects electronically signed offer letters with compensation and benefits details. |
| **Why It Matters** | Enables quick, legally binding offer acceptance with full audit trail. |
| **Supporting Requirements** | **REC-018**: As a HR Employee/HR Manager, I want to generate, send and collect electronically signed offer letters, so candidates can accept offers quickly and legally. |
| **What Gets Created** | Electronic offer letter sent; signed acceptance received and stored. |
| **Related Business Rules** | **BR-26 (a, d)**: The system supports issuing an offer letter which needs to be customizable and editable (e.g., include compensation/benefits). **BR-37**: Communication logs must be stored. |
| **Inputs Needed** | Offer template, Candidate signature data |
| **Downstream Systems** | Onboarding |

---

### STEP 17: Pre-boarding Task Triggers

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Triggers pre-boarding tasks (contract signing, forms collection) automatically after offer acceptance and before start date. |
| **Why It Matters** | Ensures new hire is ready on Day 1 with all documentation completed in advance. |
| **Supporting Requirements** | **REC-029**: As a HR Employee, I want to trigger pre-boarding tasks (contract signing, forms) after offer acceptance and before the start date, so new hire readiness is improved. |
| **What Gets Created** | Pre-boarding checklist automatically generated and assigned to candidate. |
| **Related Business Rules** | **BR-26 (c)**: Once a candidate's acceptance is received, the next module (Onboarding) should be triggered. |
| **Inputs Needed** | Offer Acceptance Status |
| **Downstream Systems** | Onboarding Module (Task Checklist) |

---

---

# 📋 COMPLETE RECRUITMENT USER STORIES REFERENCE

### REC-003: Define Standardized Job Description Templates
**What User Needs:** "As an HR Manager, I want to define standardized job description templates, so that postings are consistent. Each job requisition must include Job details (title, department, location, openings) and Qualifications and skills needed."

**Why It Matters:** Creates consistency across all job postings organization-wide.

**Related BRs:** BR-2

**System Must Support:**
- Create job description templates
- Include required fields (title, department, location, openings)
- Include qualifications and skills sections
- Reuse templates across multiple job postings
- Edit and version templates

**Inputs Needed:** Organizational Structure (Jobs/Positions)

**Downstream Impact:** Recruitment (Job Posting)

---

### REC-004: Establish Hiring Process Templates
**What User Needs:** "As an HR Manager, I want to be able to establish hiring processes templates so that the system can automatically update progress percentage. Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired)."

**Why It Matters:** Standardizes candidate journey and enables automatic progress tracking.

**Related BRs:** BR-9

**System Must Support:**
- Define hiring process stages
- Set stage sequence and dependencies
- Calculate automatic progress percentage
- Apply templates to job postings
- Track all candidates through stages

**Inputs Needed:** None (System Configuration)

**Downstream Impact:** Recruitment (Candidate Tracking)

---

### REC-023: Preview and Publish Job Postings
**What User Needs:** "As a HR Employee, I want to preview and publish jobs on the company careers page with employer-brand content, so openings look professional."

**Why It Matters:** Ensures professional, branded job postings that attract quality candidates.

**Related BRs:** BR-6

**System Must Support:**
- Preview job posting before publishing
- Include employer branding elements
- Publish to company careers page
- Automatically post to external job boards if configured
- Track posting status

**Inputs Needed:** None

**Downstream Impact:** External Careers Page

---

### REC-007: CV Upload & Application
**What User Needs:** "As a Candidate, I want to upload my CV and apply for positions, so that I can be considered for opportunities."

**Why It Matters:** Allows candidates to enter recruitment pipeline and creates talent pool.

**Related BRs:** BR-12

**System Must Support:**
- Upload CV/resume in multiple formats (PDF, DOC, DOCX)
- Submit application for specific position
- Store application in talent pool
- Associate CV with candidate profile
- Support multiple applications per candidate

**Inputs Needed:** Candidate CVs/Documents

**Downstream Impact:** Recruitment (Talent Pool)

---

### REC-017: Application Status Updates
**What User Needs:** "As a Candidate, I want to receive updates about my application status, so that I know where I stand."

**Why It Matters:** Improves candidate experience and transparency in hiring process.

**Related BRs:** BR-27, BR-36

**System Must Support:**
- Send automatic email on status change
- Display real-time status in candidate portal
- Show timeline of application progress
- Provide clear status descriptions
- Track notification delivery

**Inputs Needed:** Recruitment (Candidate Status Tracking)

**Downstream Impact:** Candidate Self-Service Portal

---

### REC-022: Automated Rejection Notifications
**What User Needs:** "As a HR Employee, I want automated rejection notifications and templates, so candidates are informed respectfully and consistently."

**Why It Matters:** Maintains professional employer brand and ensures respectful candidate treatment.

**Related BRs:** BR-36, BR-37

**System Must Support:**
- Pre-configured rejection email templates
- Automatic sending on rejection status
- Log all communications in candidate profile
- Customize templates by position or reason
- Track email delivery and opens

**Inputs Needed:** Recruitment (Rejection Reason/Template)

**Downstream Impact:** External Communication (Candidate Email)

---

### REC-008: Candidate Stage Tracking
**What User Needs:** "As a HR Employee, I want to track candidates through each stage of the hiring process, so that I can manage progress."

**Why It Matters:** Provides visibility into candidate pipeline and prevents candidates from falling through cracks.

**Related BRs:** BR-9, BR-11

**System Must Support:**
- Display all candidates by stage
- Allow drag-and-drop stage transitions
- Show stage history and timestamps
- Trigger notifications on stage change
- Filter and search candidates by stage

**Inputs Needed:** Hiring Process Template (REC-004)

**Downstream Impact:** Recruitment (Status Tracking)

---

### REC-010: Interview Scheduling
**What User Needs:** "As a HR Employee, I want to schedule and manage interview invitations, so that candidates are engaged efficiently."

**Why It Matters:** Streamlines interview coordination and eliminates manual calendar management.

**Related BRs:** BR-19 (a, c, d)

**System Must Support:**
- Select time slots and check availability
- Choose panel members
- Select interview mode (in-person, video, phone)
- Send automatic calendar invites to interviewers
- Send automatic notifications to candidates
- Sync with calendar systems (Outlook, Google Calendar)

**Inputs Needed:** Time Management (TM), Email/Calendar systems

**Downstream Impact:** Notifications (N)

---

### REC-011: Interview Feedback & Scoring
**What User Needs:** "As an HR Employee, I want to be able to provide feedback/interview score for scheduled interviews for filtration. Recruiters must be able to schedule interviews by selecting time slots, panel members, and modes. Interviewers must receive automatic calendar invites, and candidates must be notified automatically."

**Why It Matters:** Creates objective, documented evaluation for hiring decisions.

**Related BRs:** BR-10, BR-22

**System Must Support:**
- Structured feedback forms per interview
- Numerical scoring per criteria
- Comments and ratings at each stage
- Aggregate scores from multiple panel members
- Submit feedback before status change
- Link feedback to candidate record

**Inputs Needed:** Interview panel feedback/scores

**Downstream Impact:** Recruitment (Applicant Scoring)

---

### REC-020: Structured Assessment Forms
**What User Needs:** "As an HR Employee, I want structured assessment and scoring forms per role, so evaluations are consistent and auditable."

**Why It Matters:** Ensures fair, consistent, legally defensible evaluations.

**Related BRs:** BR-21, BR-23

**System Must Support:**
- Create assessment forms per role
- Define evaluation criteria and weighting
- Pre-set and agree upon criteria
- Support multiple assessment tools
- Store completed assessments for audit
- Compare candidates objectively

**Inputs Needed:** Evaluation Criteria (REC-015)

**Downstream Impact:** Recruitment (Applicant Scoring)

---

### REC-021: Interview Panel Coordination
**What User Needs:** "As a HR Employee, I want to coordinate interview panels (members, availability, scoring), so scheduling and feedback collection are centralized."

**Why It Matters:** Centralizes panel management and ensures all feedback is collected.

**Related BRs:** BR-19 (a, b), BR-20

**System Must Support:**
- Select panel members per interview
- Check member availability
- Ensure panel members have required training
- Assign scoring responsibilities
- Collect and aggregate feedback
- Track completion of panel feedback

**Inputs Needed:** Calendar/Time Management (Availability)

**Downstream Impact:** Recruitment (Interview Scheduling/Feedback)

---

### REC-030: Referral Tagging
**What User Needs:** "As a HR Employee, I want to be able to tag candidates as referrals in order to give them a higher chance of having an earlier interview."

**Why It Matters:** Allows preferential treatment of referred candidates per company policy.

**Related BRs:** BR-14, BR-25

**System Must Support:**
- Tag candidates as referrals
- Track referral source
- Apply referral filters and priority rules
- Include referral status in tie-breaking rules
- Report on referral effectiveness

**Inputs Needed:** Candidate data, Referral source info

**Downstream Impact:** Recruitment

---

### REC-009: Recruitment Progress Monitoring
**What User Needs:** "As an HR Manager, I want to monitor recruitment progress across all open positions, so that I stay informed."

**Why It Matters:** Provides oversight and identifies bottlenecks in hiring pipeline.

**Related BRs:** BR-33

**System Must Support:**
- Dashboard showing all open positions
- Show candidates per stage per position
- Calculate time-to-hire metrics
- Track source effectiveness
- Generate recruitment analytics reports
- Real-time updates

**Inputs Needed:** Recruitment data (REC-008)

**Downstream Impact:** Recruitment

---

### REC-028: Data Processing Consent
**What User Needs:** "As a Candidate, I want to give consent for personal-data processing and background checks, so the system remains compliant with privacy laws."

**Why It Matters:** Ensures GDPR compliance and legal data processing authorization.

**Related BRs:** BR-28, NFR-33

**System Must Support:**
- Present consent form during application
- Require explicit consent before data storage
- Log consent with timestamp
- Allow consent withdrawal
- Comply with GDPR and labor laws
- Store consent records for audit

**Inputs Needed:** None (Candidate input)

**Downstream Impact:** Recruitment

---

### REC-014: Offer Management & Approvals
**What User Needs:** "As an HR Manager, I want to manage job offers and approvals, so that candidates can be hired smoothly."

**Why It Matters:** Ensures offers are properly authorized before extending to candidates.

**Related BRs:** BR-26 (b, c)

**System Must Support:**
- Create offer with compensation and benefits
- Route for approval (HR → Finance → Legal)
- Track approval status
- Secure required approvals before sending
- Trigger onboarding on acceptance
- Store offer history

**Inputs Needed:** Financial Approval (REC-027)

**Downstream Impact:** Onboarding

---

### REC-018: Electronic Offer Letters
**What User Needs:** "As a HR Employee/HR Manager, I want to generate, send and collect electronically signed offer letters, so candidates can accept offers quickly and legally."

**Why It Matters:** Enables fast, legally binding offer acceptance with full audit trail.

**Related BRs:** BR-26 (a, d), BR-37

**System Must Support:**
- Generate offer letter from template
- Customize compensation and benefits
- Send via email with e-signature link
- Collect electronic signature
- Store signed offer document
- Log all communications
- Support legal e-signature standards

**Inputs Needed:** Offer template, Candidate signature data

**Downstream Impact:** Onboarding

---

### REC-029: Pre-boarding Task Triggers
**What User Needs:** "As a HR Employee, I want to trigger pre-boarding tasks (contract signing, forms) after offer acceptance and before the start date, so new hire readiness is improved."

**Why It Matters:** Ensures new hire completes all required steps before Day 1.

**Related BRs:** BR-26 (c)

**System Must Support:**
- Automatically trigger pre-boarding checklist on offer acceptance
- Send tasks to candidate (contract signing, forms, documents)
- Track completion status
- Send reminders for incomplete tasks
- Hand off to onboarding module
- Notify HR of readiness status

**Inputs Needed:** Offer Acceptance Status

**Downstream Impact:** Onboarding Module (Task Checklist)

---

---

# 📋 COMPLETE RECRUITMENT BUSINESS RULES REFERENCE TABLE

This section contains ALL Recruitment Business Rules with their complete descriptions.

| BR ID | BR Description |
|-------|----------------|
| **BR-2** | Each job requisition must include Job details (title, department, location, openings) and Qualifications and skills needed. |
| **BR-6** | The system must allow automatic posting of approved requisitions to internal and external career sites. |
| **BR-9** | Each application must be tracked through defined stages (e.g., Screening, Shortlisting, Interview, Offer, Hired). |
| **BR-10** | The system must allow adding comments and ratings at each stage. |
| **BR-11** | Recruiters and hiring managers must be notified of status changes via alerts or workflow emails. |
| **BR-12** | The system must support the storage/upload of applications with resumes, which creates the organization's talent pool. |
| **BR-14** | Electronic screening includes rule-based filters. |
| **BR-19(a)** | Recruiters must be able to schedule interviews by selecting time slots, panel members, and modes. |
| **BR-19(b)** | Interview scheduling requires selecting panel members. |
| **BR-19(c)** | Interviewers must receive automatic calendar invites. |
| **BR-19(d)** | Candidates must be notified automatically. |
| **BR-20** | Panels need to possess the knowledge and/or training to conduct the needed interviews/selection tests. |
| **BR-21** | The system needs to allow/house the multiple assessment tools to be used. |
| **BR-22** | Feedback at each stage must be submitted by the panel/interviewers to ensure accuracy. |
| **BR-23** | Criteria used in interview assessment are pre-set and agreed upon. The system needs to allow/house the multiple assessment tools to be used. |
| **BR-25** | Tie-Breaking Rules should be predetermined and could be based on Internal candidate preference. |
| **BR-26(a)** | The system supports issuing an offer letter which needs to be customizable and editable (e.g., include compensation/benefits). |
| **BR-26(b)** | The system must support securing related parties' approval before sending out the offer. |
| **BR-26(c)** | Once a candidate's acceptance is received, the next module (Onboarding) should be triggered. |
| **BR-26(d)** | Offer letters support electronic signatures. |
| **BR-27** | Candidate Status Tracking must be easily visualized and up-to-date in real-time. |
| **BR-28** | Storing the talent pool needs to be authorized by applicants in the early stages of the recruitment process. |
| **BR-33** | Multiple reports could be generated like time-to-hire and source effectiveness. |
| **BR-36** | The system must send automated alerts/emails to candidates regarding status updates. The system must support email templates for communication (e.g., rejection). |
| **BR-37** | Communication logs must be stored in the applicant profile. |
| **NFR-33** | All data handling must comply with GDPR and labor laws. |

---

---

# 🔄 RECRUITMENT WORKFLOW SUMMARY

## Phase-by-Phase Flow

### PHASE 1: PREPARATION & TEMPLATES
```
HR Manager defines job templates
  → HR Manager establishes hiring process stages
  → Templates stored and ready for use
```

### PHASE 2: JOB POSTING
```
HR Employee creates job posting from template
  → HR Employee previews posting
  → HR Employee publishes to careers page
  → System auto-posts to external job boards
```

### PHASE 3: APPLICATION & CONSENT
```
Candidate uploads CV
  → Candidate provides data consent
  → Application stored in talent pool
  → HR notified of new application
```

### PHASE 4: PIPELINE & TAGS
```
HR tags referrals for priority
  → HR moves candidates through stages
  → System tracks all transitions
  → Automatic notifications sent
```

### PHASE 5: EVALUATION
```
HR creates structured assessment forms
  → HR schedules interviews with panel
  → Panel receives calendar invites
  → Candidate receives notification
  → Panel submits feedback and scores
  → System aggregates scores
```

### PHASE 6: MONITORING & COMMUNICATION
```
HR Manager monitors dashboard
  → Candidates receive status updates
  → Rejected candidates notified professionally
  → All communications logged
```

### PHASE 7: OFFER & TRANSITION
```
HR generates offer
  → Offer routed for approvals
  → Approved offer sent to candidate
  → Candidate signs electronically
  → System triggers pre-boarding tasks
  → Onboarding module activated
```

---

---

# 📊 INTEGRATION POINTS WITH OTHER SUBSYSTEMS

## Inputs from Other Subsystems

| Input From | Data Received | Used For |
|------------|---------------|----------|
| **Organizational Structure** | Jobs/Positions | Job template creation (REC-003) |
| **Time Management** | Calendar/Availability | Interview scheduling (REC-010, REC-021) |
| **Financial Approval** | Budget authorization | Offer approvals (REC-014) |

---

## Outputs to Other Subsystems

| Output To | Data Sent | Purpose |
|-----------|-----------|---------|
| **Onboarding Module** | Signed offer letter, Candidate data | Trigger onboarding checklist (REC-029) |
| **Employee Profile** | New hire information | Create employee profile (from Onboarding) |
| **Candidate Portal** | Application status | Real-time candidate visibility (REC-017) |
| **External Systems** | Job postings | Career site publishing (REC-023) |
| **Notifications System** | Status changes, Interview schedules | Automated alerts (REC-017, REC-010) |

---

---

---

---

# PHASE 8: ONBOARDING - INTEGRATION & PROVISIONING

## 📋 Phase Description

**Once a candidate accepts an offer, the Onboarding phase transforms them from "accepted candidate" into "active employee." This phase focuses on creating onboarding task checklists, collecting documentation, provisioning access, assigning resources, and initiating payroll and benefits. Automated notifications guide both HR teams and new hires to ensure readiness before Day 1.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Getting new hires ready to work on Day 1:
- HR creates a checklist of everything the new hire needs to complete
- New hire uploads required documents (ID, certifications, signed contract)
- IT provisions email, laptop, and system access
- HR reserves desk, equipment, and access cards
- Payroll is initiated automatically based on contract signing date
- Signing bonuses are processed according to contract
- New hire sees progress tracker and receives reminders
- All departments coordinate automatically

**Why This Matters:** Without automation, new hires show up on Day 1 to find: no laptop, no desk assignment, no email account, and payroll doesn't know they exist. This phase ensures every stakeholder (HR, IT, Facilities, Payroll) completes their responsibilities before the start date.

---

## ONBOARDING WORKFLOW STEPS

### STEP 1: Candidate Uploads Signed Contract and Forms

| Aspect | Details |
|--------|---------|
| **Actor** | Candidate (Pre-boarding) |
| **What They Do** | Uploads signed contract and required forms/templates to initiate onboarding process. |
| **Why It Matters** | Triggers the entire onboarding workflow and provides legal foundation for employment. |
| **Supporting Requirements** | As a Candidate, I want to upload signed contract and candidate required forms and templates to initiate the onboarding process. |
| **What Gets Created** | Signed contract uploaded; onboarding workflow triggered. |
| **Related Business Rules** | To be defined (currently blank in source) |
| **Inputs Needed** | None (Configuration) |
| **Downstream Systems** | New Hire Tracker (ONB-004) |

**Real-World Example:** Maria receives offer letter via email. She signs electronically, uploads her ID scan and certifications. The moment she clicks "Submit," the system automatically notifies HR to start creating her employee profile, IT to prepare her laptop, and Facilities to assign her a desk.

---

### STEP 2: HR Creates Onboarding Task Checklists

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Creates onboarding task checklists so that new hires complete all required steps. |
| **Why It Matters** | Ensures nothing is forgotten and every new hire completes same required steps. |
| **Supporting Requirements** | **ONB-001**: As an HR Manager, I want to create onboarding task checklists, so that new hires complete all required steps. |
| **What Gets Created** | Department-specific onboarding checklist with tasks, owners, and deadlines. |
| **Related Business Rules** | **BR-8, BR-11**: The orientation program must include an onboarding workflow and support department-specific tasks and training plans. |
| **Inputs Needed** | None (Configuration) |
| **Downstream Systems** | New Hire Tracker (ONB-004) |

**Real-World Example:** Engineering new hires get checklist: (1) Complete security training, (2) Set up development environment, (3) Review code standards, (4) Meet team. Sales new hires get different checklist: (1) Complete product training, (2) Shadow senior rep, (3) Set up CRM access, (4) Review sales playbook.

---

### STEP 3: HR Accesses Contract to Create Employee Profile

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Accesses signed contract details to create an employee profile in the system. |
| **Why It Matters** | Converts candidate record into employee record with all contract terms properly recorded. |
| **Supporting Requirements** | **ONB-002**: As an HR Manager, I want to be able to access signed contract detail to be able create an employee profile. |
| **What Gets Created** | Complete employee profile with position, salary, start date, department, manager, etc. |
| **Related Business Rules** | **BR-17(a, b)**: Employee profile must be created from signed contract data. |
| **Inputs Needed** | Recruitment (Signed Offer Letter/Contract) |
| **Downstream Systems** | Employee Profile (EP) |

**Real-World Example:** HR Manager clicks "Create Employee Profile" button. System automatically pulls: Name from application, Position from offer letter, Salary from contract, Department from job posting, Start Date from offer acceptance. HR just verifies and clicks "Confirm" instead of manually entering everything.

---

### STEP 4: New Hire Views Onboarding Tracker

| Aspect | Details |
|--------|---------|
| **Actor** | New Hire |
| **What They Do** | Views onboarding steps in a tracker to know what to complete next. |
| **Why It Matters** | Gives new hire visibility and control over their onboarding progress. |
| **Supporting Requirements** | **ONB-004**: As a New Hire, I want to view my onboarding steps in a tracker, so that I know what to complete next. |
| **What Gets Created** | Self-service portal showing tasks, completion status, and next steps. |
| **Related Business Rules** | **BR-11(a, b)**: The orientation program must include an onboarding workflow and support department-specific tasks and training plans. |
| **Inputs Needed** | None (Onboarding Checklist Data) |
| **Downstream Systems** | Notifications (N) |

**Real-World Example:** New hire logs into portal and sees: ✅ Upload documents (Complete), ✅ Review employee handbook (Complete), ⏳ Complete I-9 form (In Progress), ⬜ Attend orientation (Scheduled for Monday 9am), ⬜ Meet manager (Pending).

---

### STEP 5: New Hire Receives Reminders and Notifications

| Aspect | Details |
|--------|---------|
| **Actor** | New Hire |
| **What They Do** | Receives automated reminders and notifications so important tasks aren't missed. |
| **Why It Matters** | Prevents tasks from falling through cracks and keeps onboarding on schedule. |
| **Supporting Requirements** | **ONB-005**: As a New Hire, I want to receive reminders and notifications, so that I don't miss important onboarding tasks. |
| **What Gets Created** | Automated email/SMS reminders for incomplete tasks approaching deadlines. |
| **Related Business Rules** | **BR-12**: The system must support sending reminders and task assignments to responsible parties, and track delivery and status accordingly. |
| **Inputs Needed** | Notifications Module (N) |
| **Downstream Systems** | None |

**Real-World Example:** Three days before start date, new hire receives email: "Reminder: Please complete I-9 form before your first day. Click here to complete." One day before start date: "Tomorrow is your first day! Report to Reception at 9am. Your manager is John Smith."

---

### STEP 6: New Hire Uploads Compliance Documents

| Aspect | Details |
|--------|---------|
| **Actor** | New Hire |
| **What They Do** | Uploads required documents (e.g., ID, contracts, certifications) to ensure compliance. |
| **Why It Matters** | Ensures legal compliance and proper documentation before work begins. |
| **Supporting Requirements** | **ONB-007**: As a New Hire, I want to upload documents (e.g., ID, contracts, certifications), so that compliance is ensured. |
| **What Gets Created** | Digital document repository linked to employee profile. |
| **Related Business Rules** | **BR-7**: Documents must be collected and verified by the HR department before the first working day. |
| **Inputs Needed** | None (New Hire Input) |
| **Downstream Systems** | Employee Profile (EP) |

**Real-World Example:** New hire uploads: (1) Government-issued ID (for I-9 verification), (2) Professional certifications (for licensed positions), (3) Educational transcripts (for roles requiring degrees), (4) Background check authorization. HR receives notification to verify each document.

---

### STEP 7: System Admin Provisions System Access

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin |
| **What They Do** | Provisions system access (payroll, email, internal systems) so employee can work. |
| **Why It Matters** | Ensures new hire has all necessary tools and access on Day 1. |
| **Supporting Requirements** | **ONB-009**: As a System Admin, I want to provision system access (payroll, email, internal systems), so that the employee can work. |
| **What Gets Created** | User accounts created across all systems with appropriate permissions. |
| **Related Business Rules** | **BR-9(b)**: Auto onboarding tasks are generated for IT (allocation of email, laptop, system access). |
| **Inputs Needed** | Employee Profile (New Hire Record) |
| **Downstream Systems** | Notifications (N) to IT/Access Systems, Payroll |

**Real-World Example:** System automatically creates: (1) Email account: maria.johnson@company.com, (2) Payroll system access, (3) Time tracking access, (4) Department-specific tool access (Salesforce for sales, GitHub for engineering, etc.). IT just reviews and approves instead of manually creating each account.

---

### STEP 8: HR Employee Reserves and Tracks Equipment

| Aspect | Details |
|--------|---------|
| **Actor** | HR Employee |
| **What They Do** | Reserves and tracks equipment, desk, and access cards for new hires so resources are ready on Day 1. |
| **Why It Matters** | Prevents "first day chaos" where new hire has nowhere to sit or no computer to use. |
| **Supporting Requirements** | **ONB-012**: As a HR Employee, I want to reserve and track equipment, desk and access cards for new hires, so resources are ready on Day 1. |
| **What Gets Created** | Equipment reservation logged; facilities notified to prepare workspace. |
| **Related Business Rules** | **BR-9(c)**: Auto onboarding tasks are generated for Admin (allocation and assignment of workspace, ID badge). |
| **Inputs Needed** | None |
| **Downstream Systems** | Notifications (N) to Facilities/Admin Systems |

**Real-World Example:** Facilities receives notification: "Reserve desk in Engineering section for Maria Johnson, start date May 15." IT receives notification: "Prepare laptop (MacBook Pro per department standard) with standard engineering software." Security receives notification: "Create access badge for Maria Johnson."

---

### STEP 9: HR Manager Ensures Automated Account Provisioning

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager / System Admin |
| **What They Do** | Ensures automated account provisioning (SSO/email/tools) on start date and schedules revocation on exit for consistency and security. |
| **Why It Matters** | Maintains security by ensuring access is granted exactly when needed and revoked when employment ends. |
| **Supporting Requirements** | **ONB-013**: As a HR Manager, I want automated account provisioning (SSO/email/tools) on start date and scheduled revocation on exit, so access is consistent and secure. |
| **What Gets Created** | Scheduled provisioning rules; future revocation triggers set. |
| **Related Business Rules** | **BR-9(b)**: IT (allocation of email, laptop, system access) is an automated task. **BR-20**: The system should allow onboarding cancellation/termination of the created employee profile in case of a "no show". |
| **Inputs Needed** | System Admin Configuration |
| **Downstream Systems** | IT/Access Systems, Offboarding |

**Real-World Example:** System schedules: (1) Enable all accounts on May 15 at 8am (start date), (2) Set future trigger: "If employee status changes to 'Terminated' or 'Resigned,' automatically disable all accounts within 24 hours." This prevents the common security risk of former employees retaining system access.

**Edge Case Handled:** If new hire doesn't show up on Day 1 (called a "no show"), HR can cancel the onboarding. System automatically: (1) Disables all provisioned accounts, (2) Releases reserved equipment, (3) Cancels payroll initiation, (4) Notifies all stakeholders.

---

### STEP 10: HR Manager Initiates Automatic Payroll Setup

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Initiates system to automatically handle payroll initiation based on contract signing day for current payroll cycle. |
| **Why It Matters** | Ensures new hire gets paid correctly in their first paycheck without manual intervention. |
| **Supporting Requirements** | **ONB-018**: As a HR Manager, I want the system to automatically handle payroll initiation based on the contract signing day for the current payroll cycle. |
| **What Gets Created** | Employee added to active payroll cycle with pro-rated salary if mid-cycle start. |
| **Related Business Rules** | **BR-9(a)**: Auto onboarding tasks are generated for HR (payroll & benefits' creation). This relates to the Payroll requirement REQ-PY-23 to automatically process payroll initiation. |
| **Inputs Needed** | Recruitment (Contract Signing Date) |
| **Downstream Systems** | Payroll Module (PY) |

**Real-World Example:** New hire starts May 15 (mid-month). Contract salary is $6,000/month. System automatically calculates: (1) May has 31 days, (2) Employee works 17 days in May (15-31), (3) Pro-rated salary = $6,000 × (17/31) = $3,290.32. Payroll team doesn't manually calculate anything—it's automatic.

---

### STEP 11: HR Manager Processes Signing Bonuses

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Initiates system to automatically process signing bonuses based on contract after new hire is signed. |
| **Why It Matters** | Ensures signing bonuses promised in offer letter are paid correctly and on time. |
| **Supporting Requirements** | **ONB-019**: As a HR Manager, I want the system to automatically process signing bonuses based on contract after a new hire is signed. |
| **What Gets Created** | Signing bonus payment added to first paycheck or separate payment per contract terms. |
| **Related Business Rules** | **BR-9(a)**: This relates to the Payroll requirement REQ-PY-27 to automatically process signing bonuses. |
| **Inputs Needed** | Recruitment (Contract Details) |
| **Downstream Systems** | Payroll Module (PY) |

**Real-World Example:** Contract states: "$5,000 signing bonus paid in first paycheck." System automatically: (1) Adds $5,000 to first paycheck, (2) Marks bonus as paid in employee record, (3) Prevents duplicate payment if payroll is re-run. Alternative contract terms supported: "50% on Day 1, 50% after 6 months"—system schedules both payments automatically.

---

---

# PHASE 9: OFFBOARDING - SEPARATION & CLEARANCE

## 📋 Phase Description

**The Offboarding phase manages the structured and compliant exit of employees, whether through resignation or termination. It covers exit initiation, clearance workflows across multiple departments, access revocation, asset recovery, and final settlements. Integration with payroll, IT, and facilities ensures that all assets are recovered, benefits are closed, and access rights are securely revoked.**

### 🎯 What This Phase Actually Does (Non-Technical Explanation)

Managing employee departures professionally and compliantly:
- Employee submits resignation or HR initiates termination
- Multi-department clearance checklist created (IT, Finance, Facilities, HR)
- System access revoked automatically
- Company assets tracked and recovered (laptop, ID badge, keys)
- Final paycheck calculated (unused leave, deductions, severance)
- Benefits terminated as of end date
- All actions logged for compliance and audit

**Why This Matters:** Without structured offboarding, companies face: (1) Security risks (former employees with system access), (2) Lost assets (unreturned laptops worth thousands), (3) Compliance violations (incorrect final settlements), (4) Bad employee experience (delayed final paychecks). This phase ensures every departure is handled consistently and completely.

---

## OFFBOARDING WORKFLOW STEPS

### STEP 1: Employee Submits Resignation Request

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Submits resignation request with reasoning through the system. |
| **Why It Matters** | Creates official record and triggers approval workflow and clearance process. |
| **Supporting Requirements** | **OFF-018**: As an Employee, I want to be able to request a Resignation request with reasoning. |
| **What Gets Created** | Resignation request submitted with effective date and reason. |
| **Related Business Rules** | **BR-6**: Employee separation can be triggered by resignation. A clearly identified offboarding approval workflow should be identified (e.g., Employee resigning > Line Manager > Financial approval > HR processing/approval). |
| **Inputs Needed** | Employee Profile (Resignation Reason) |
| **Downstream Systems** | Offboarding Approval Workflow |

**Real-World Example:** Sarah logs into HR portal and submits: "I am resigning effective June 30, 2025. Reason: Accepted position at another company. Notice period: 2 weeks per contract." System automatically: (1) Notifies her manager, (2) Starts approval workflow, (3) Creates offboarding checklist, (4) Calculates her last working day.

---

### STEP 2: Employee Tracks Resignation Status

| Aspect | Details |
|--------|---------|
| **Actor** | Employee |
| **What They Do** | Tracks resignation request status to know where it stands in approval process. |
| **Why It Matters** | Provides transparency and allows employee to plan their departure. |
| **Supporting Requirements** | **OFF-019**: As an Employee, I want to be able to track my resignation request status. |
| **What Gets Created** | Status updates visible in employee self-service portal. |
| **Related Business Rules** | **BR-6**: Clearly identified offboarding approval workflow. |
| **Inputs Needed** | Employee Profile (Resignation Reason) |
| **Downstream Systems** | Offboarding Approval Workflow |

**Real-World Example:** Employee sees in portal: ✅ Resignation Submitted (May 1), ✅ Manager Approved (May 2), ⏳ HR Processing (Current), ⬜ Finance Clearance (Pending), ⬜ Final Settlement (Not Started). Expected completion date: June 30.

---

### STEP 3: HR Manager Initiates Termination Review

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Initiates termination reviews based on warnings and performance data / manager requests to ensure exits are justified. |
| **Why It Matters** | Ensures terminations follow due process and comply with labor laws. |
| **Supporting Requirements** | **OFF-001**: As an HR Manager, I want to initiate termination reviews based on warnings and performance data / manager requests, so that exits are justified. |
| **What Gets Created** | Termination review initiated with documented justification. |
| **Related Business Rules** | **BR-4**: Employee separation needs an effective date and a clearly stated and identified reason for exit. Termination reviews based on performance must follow due process. |
| **Inputs Needed** | Performance Management (PM) (Warnings/Low Scores) |
| **Downstream Systems** | Offboarding Approval Workflow |

**Real-World Example:** Manager escalates: "John has received 3 written warnings for attendance violations and performance is below standards." HR reviews: (1) Performance review history showing consistent underperformance, (2) Written warnings properly documented, (3) Performance improvement plan that wasn't met. HR determines termination is justified and initiates offboarding with proper documentation for legal protection.

**Why Due Process Matters:** If termination is challenged legally, company needs evidence of: (1) Documented performance issues, (2) Warnings given, (3) Opportunity to improve provided, (4) Consistent application of policy. System provides complete audit trail.

---

### STEP 4: HR Manager Creates Offboarding Checklist

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Creates offboarding checklist for asset recovery (IT assets, ID cards, equipment) to ensure no company property is lost. |
| **Why It Matters** | Protects company assets and ensures nothing is overlooked. |
| **Supporting Requirements** | **OFF-006**: As an HR Manager, I want an offboarding checklist (IT assets, ID cards, equipment), so no company property is lost. |
| **What Gets Created** | Department-specific clearance checklist with items to return and sign-offs required. |
| **Related Business Rules** | **BR-13(a)**: Offboarding checklist must cover all departments and asset types. |
| **Inputs Needed** | None (Configuration) |
| **Downstream Systems** | Clearance Workflow (OFF-010) |

**Real-World Example:** System generates checklist for departing employee:
**IT:** ☐ Return laptop, ☐ Return mobile phone, ☐ Return access tokens, ☐ Transfer file ownership
**Facilities:** ☐ Return ID badge, ☐ Return office keys, ☐ Return parking pass
**Finance:** ☐ Settle expense reports, ☐ Return company credit card
**HR:** ☐ Exit interview completed, ☐ Benefits termination processed
**Manager:** ☐ Knowledge transfer completed, ☐ Handover document signed

---

### STEP 5: HR Manager Obtains Multi-Department Clearance Sign-Offs

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Obtains multi-department exit clearance sign-offs (IT, Finance, Facilities, Line Manager) with statuses tracking to ensure employee is fully cleared. |
| **Why It Matters** | Ensures all departments confirm assets returned before final payment is released. |
| **Supporting Requirements** | **OFF-010**: As HR Manager, I want multi-department exit clearance sign-offs (IT, Finance, Facilities, Line Manager), with statuses, so the employee is fully cleared. |
| **What Gets Created** | Clearance sign-offs tracked per department; final settlement blocked until complete. |
| **Related Business Rules** | **BR-13(b, c)**: Clearance checklist required across departments (IT, HR, Admin, Finance). **BR-14**: Final approvals/signature form should be filed to HR to complete the offboarding process. |
| **Inputs Needed** | Clearance Status Updates (from Depts) |
| **Downstream Systems** | Payroll (Final Settlement) |

**Real-World Example:** 
**Day 1:** IT signs off: "Laptop returned, files transferred, access revoked ✅"
**Day 2:** Facilities signs off: "ID badge and keys returned ✅"
**Day 3:** Finance signs off: "Expense reports settled, no outstanding debts ✅"
**Day 4:** Manager signs off: "Knowledge transfer completed, no pending tasks ✅"
**Day 5:** HR releases final paycheck only after all four sign-offs complete.

**What Happens If Items Not Returned:** System blocks final paycheck until: (1) Employee returns items, OR (2) HR approves deduction from final pay for unreturned items (e.g., $1,200 for unreturned laptop).

---

### STEP 6: System Admin Revokes System and Account Access

| Aspect | Details |
|--------|---------|
| **Actor** | System Admin |
| **What They Do** | Revokes system and account access upon termination to maintain security. |
| **Why It Matters** | Critical security measure to prevent unauthorized access by former employees. |
| **Supporting Requirements** | **OFF-007**: As a System Admin, I want to revoke system and account access upon termination, so security is maintained. |
| **What Gets Created** | All system access disabled; access revocation logged for audit. |
| **Related Business Rules** | **BR-3(c), BR-19**: Access revocation required for security. |
| **Inputs Needed** | Employee Profile (Inactive Status) |
| **Downstream Systems** | Notifications (N), IT/Access Systems |

**Real-World Example:** On employee's last day at 5pm, system automatically:
(1) **Disables email account** (emails forward to manager for 30 days)
(2) **Revokes VPN access** (can't connect remotely)
(3) **Disables SSO/Active Directory** (can't log into any company systems)
(4) **Revokes building access card** (can't enter building)
(5) **Disables cloud service access** (Salesforce, AWS, etc.)
(6) **Logs all revocations** with timestamps for security audit

**Security Best Practice:** Access is revoked automatically based on termination date, not manually (which is error-prone). System prevents the common security vulnerability of "former employee still has access weeks later."

---

### STEP 7: HR Manager Triggers Final Settlement Calculation

| Aspect | Details |
|--------|---------|
| **Actor** | HR Manager |
| **What They Do** | Sends offboarding notification to trigger benefits termination and final pay calculation (unused leave, deductions, severance) to ensure settlements are accurate. |
| **Why It Matters** | Ensures employee receives all entitled compensation and benefits are properly terminated. |
| **Supporting Requirements** | **OFF-013**: As HR Manager, I want to send offboarding notification to trigger benefits termination and final pay calc (unused leave, deductions), so settlements are accurate. |
| **What Gets Created** | Final paycheck calculated; benefits termination scheduled; all settlements documented. |
| **Related Business Rules** | **BR-9, BR-11**: Leaves' Balance must be reviewed and settled (unused annuals to be encashed). Benefits plans are set to be auto-terminated as of the end of the notice period. |
| **Inputs Needed** | Leaves Module (Balance), Employee Profile (Benefits) |
| **Downstream Systems** | Payroll Module (PY) |

**Real-World Example - Final Settlement Calculation:**

**Employee:** Sarah Johnson
**Last Working Day:** June 30, 2025
**Annual Salary:** $72,000
**Final Settlement Breakdown:**

**ADDITIONS:**
- Pro-rated June salary (30 days): $6,000
- Unused vacation days (10 days): $2,307.69
- Accrued bonus (50% of quarterly): $3,000
- **Severance (if applicable - depends on reason):** $12,000 (2 months salary per company policy for layoffs)

**DEDUCTIONS:**
- Unreturned equipment: -$0 (all items returned)
- Outstanding loans: -$500 (remaining balance on employee laptop loan)
- Final health insurance premium: -$200

**TOTAL FINAL PAYMENT:** $22,607.69

**Benefits Termination:**
- Health insurance: Coverage ends June 30
- Life insurance: Coverage ends June 30
- 401(k): Vested amount transferred to employee's control
- Stock options: Vesting stops June 30; 90 days to exercise vested options

System calculates all of this automatically based on contract terms, company policies, and labor laws—no manual spreadsheet calculations needed.

---

---

# 📋 COMPLETE ONBOARDING USER STORIES REFERENCE

### ONB-001: Create Onboarding Task Checklists
**What User Needs:** "As an HR Manager, I want to create onboarding task checklists, so that new hires complete all required steps."

**Why It Matters:** Standardizes onboarding experience and ensures nothing is forgotten.

**Related BRs:** BR-8, BR-11

**System Must Support:**
- Create customizable checklists per department/role
- Assign tasks to responsible parties (HR, IT, New Hire, Manager)
- Set deadlines and dependencies
- Track completion status
- Send automatic reminders for overdue tasks

**Inputs Needed:** None (Configuration)

**Downstream Impact:** New Hire Tracker (ONB-004)

---

### ONB-002: Access Contract to Create Employee Profile
**What User Needs:** "As an HR Manager, I want to be able to access signed contract detail to be able create an employee profile."

**Why It Matters:** Converts candidate data into employee record with contract terms properly captured.

**Related BRs:** BR-17(a, b)

**System Must Support:**
- Import data from signed contract automatically
- Create employee profile with position, salary, start date
- Link to organizational structure (department, manager)
- Populate payroll information
- Maintain audit trail from recruitment to employment

**Inputs Needed:** Recruitment (Signed Offer Letter/Contract)

**Downstream Impact:** Employee Profile (EP)

---

### ONB-004: View Onboarding Tracker
**What User Needs:** "As a New Hire, I want to view my onboarding steps in a tracker, so that I know what to complete next."

**Why It Matters:** Empowers new hire to manage their own onboarding progress.

**Related BRs:** BR-11(a, b)

**System Must Support:**
- Self-service portal showing all tasks
- Visual progress indicators (% complete)
- Next-action recommendations
- Links to complete tasks directly
- Department-specific task visibility

**Inputs Needed:** None (Onboarding Checklist Data)

**Downstream Impact:** Notifications (N)

---

### ONB-005: Receive Onboarding Reminders
**What User Needs:** "As a New Hire, I want to receive reminders and notifications, so that I don't miss important onboarding tasks."

**Why It Matters:** Prevents tasks from being forgotten and keeps onboarding on schedule.

**Related BRs:** BR-12

**System Must Support:**
- Automated email/SMS reminders
- Configurable reminder timing (e.g., 3 days before, 1 day before deadline)
- Escalation notifications if tasks overdue
- Track notification delivery and opens
- Multi-channel notifications (email, SMS, portal)

**Inputs Needed:** Notifications Module (N)

**Downstream Impact:** None

---

### ONB-007: Upload Compliance Documents
**What User Needs:** "As a New Hire, I want to upload documents (e.g., ID, contracts, certifications), so that compliance is ensured."

**Why It Matters:** Ensures legal compliance before work begins.

**Related BRs:** BR-7

**System Must Support:**
- Upload multiple document types (PDF, JPG, PNG)
- Categorize documents (ID, Certifications, Contracts)
- Notify HR when documents uploaded
- HR verification workflow
- Secure document storage
- Prevent work start if required documents missing

**Inputs Needed:** None (New Hire Input)

**Downstream Impact:** Employee Profile (EP)

---

### ONB-009: Provision System Access
**What User Needs:** "As a System Admin, I want to provision system access (payroll, email, internal systems), so that the employee can work."

**Why It Matters:** Ensures new hire has all tools needed on Day 1.

**Related BRs:** BR-9(b)

**System Must Support:**
- Automated account creation across systems
- Role-based access provisioning
- SSO/Active Directory integration
- Email account creation
- Department-specific tool access
- Audit logging of all provisioning actions

**Inputs Needed:** Employee Profile (New Hire Record)

**Downstream Impact:** Notifications (N) to IT/Access Systems, Payroll

---

### ONB-012: Reserve and Track Equipment
**What User Needs:** "As a HR Employee, I want to reserve and track equipment, desk and access cards for new hires, so resources are ready on Day 1."

**Why It Matters:** Prevents "first day chaos" where new hire lacks workspace or equipment.

**Related BRs:** BR-9(c)

**System Must Support:**
- Equipment reservation system
- Workspace assignment tracking
- Access badge generation requests
- Facilities notifications
- Equipment inventory integration
- Track asset assignment to employees

**Inputs Needed:** None

**Downstream Impact:** Notifications (N) to Facilities/Admin Systems

---

### ONB-013: Automated Account Provisioning and Revocation
**What User Needs:** "As a HR Manager, I want automated account provisioning (SSO/email/tools) on start date and scheduled revocation on exit, so access is consistent and secure."

**Why It Matters:** Maintains security throughout entire employee lifecycle.

**Related BRs:** BR-9(b), BR-20

**System Must Support:**
- Scheduled account activation on start date
- Scheduled account deactivation on termination
- Handle "no show" scenarios (cancel onboarding)
- Automatic access revocation triggers
- Exception handling for early/late starts
- Security audit trail

**Inputs Needed:** System Admin Configuration

**Downstream Impact:** IT/Access Systems, Offboarding

---

### ONB-018: Automatic Payroll Initiation
**What User Needs:** "As a HR Manager, I want the system to automatically handle payroll initiation based on the contract signing day for the current payroll cycle."

**Why It Matters:** Ensures new hire is paid correctly without manual intervention.

**Related BRs:** BR-9(a) - Links to REQ-PY-23

**System Must Support:**
- Automatic payroll enrollment on start date
- Pro-rated salary calculation for mid-cycle starts
- Benefits enrollment integration
- Tax withholding setup
- Bank account information capture
- Payroll cycle alignment

**Inputs Needed:** Recruitment (Contract Signing Date)

**Downstream Impact:** Payroll Module (PY)

---

### ONB-019: Automatic Signing Bonus Processing
**What User Needs:** "As a HR Manager, I want the system to automatically process signing bonuses based on contract after a new hire is signed."

**Why It Matters:** Ensures signing bonuses are paid as promised in offer letter.

**Related BRs:** BR-9(a) - Links to REQ-PY-27

**System Must Support:**
- Parse signing bonus terms from contract
- Schedule payment per contract (first check, after 6 months, etc.)
- One-time payment verification (prevent duplicates)
- Track bonus payment status
- Integration with payroll processing
- Audit trail of bonus payments

**Inputs Needed:** Recruitment (Contract Details)

**Downstream Impact:** Payroll Module (PY)

---

---

# 📋 COMPLETE OFFBOARDING USER STORIES REFERENCE

### OFF-001: Initiate Termination Reviews
**What User Needs:** "As an HR Manager, I want to initiate termination reviews based on warnings and performance data / manager requests, so that exits are justified."

**Why It Matters:** Ensures terminations follow due process and legal compliance.

**Related BRs:** BR-4

**System Must Support:**
- Link to performance management system
- View performance history and warnings
- Document termination justification
- Approval workflow for terminations
- Legal compliance checklist
- Due process documentation

**Inputs Needed:** Performance Management (PM) (Warnings/Low Scores)

**Downstream Impact:** Offboarding Approval Workflow

---

### OFF-006: Offboarding Checklist for Asset Recovery
**What User Needs:** "As an HR Manager, I want an offboarding checklist (IT assets, ID cards, equipment), so no company property is lost."

**Why It Matters:** Protects company assets worth thousands of dollars per employee.

**Related BRs:** BR-13(a)

**System Must Support:**
- Generate checklist of all assigned assets
- Track return status per item
- Multi-department coordination
- Photo/documentation of returned items
- Escalation for unreturned items
- Deduction authorization for unreturned assets

**Inputs Needed:** None (Configuration)

**Downstream Impact:** Clearance Workflow (OFF-010)

---

### OFF-007: Revoke System Access
**What User Needs:** "As a System Admin, I want to revoke system and account access upon termination, so security is maintained."

**Why It Matters:** Critical security control to prevent unauthorized access.

**Related BRs:** BR-3(c), BR-19

**System Must Support:**
- Automatic access revocation on termination date
- Disable SSO/Active Directory accounts
- Revoke VPN access
- Disable email (with forwarding option)
- Revoke application-specific access
- Security audit logging

**Inputs Needed:** Employee Profile (Inactive Status)

**Downstream Impact:** Notifications (N), IT/Access Systems

---

### OFF-010: Multi-Department Clearance Sign-Offs
**What User Needs:** "As HR Manager, I want multi-department exit clearance sign-offs (IT, Finance, Facilities, Line Manager), with statuses, so the employee is fully cleared."

**Why It Matters:** Ensures all stakeholders confirm asset recovery before final payment.

**Related BRs:** BR-13(b, c), BR-14

**System Must Support:**
- Route clearance checklist to all departments
- Track sign-off status per department
- Block final settlement until all cleared
- Escalation for delayed clearances
- Final approval signature collection
- Complete audit trail

**Inputs Needed:** Clearance Status Updates (from Depts)

**Downstream Impact:** Payroll (Final Settlement)

---

### OFF-013: Trigger Final Settlement Calculation
**What User Needs:** "As HR Manager, I want to send offboarding notification to trigger benefits termination and final pay calc (unused leave, deductions), so settlements are accurate."

**Why It Matters:** Ensures accurate final compensation per legal requirements.

**Related BRs:** BR-9, BR-11

**System Must Support:**
- Automatic leave balance calculation
- Unused leave encashment
- Pro-rated salary calculation
- Severance calculation per policy
- Deductions for unreturned assets
- Benefits termination scheduling
- Final pay approval workflow
- Integration with payroll system

**Inputs Needed:** Leaves Module (Balance), Employee Profile (Benefits)

**Downstream Impact:** Payroll Module (PY)

---

### OFF-018: Employee Resignation Request
**What User Needs:** "As an Employee, I want to be able to request a Resignation request with reasoning."

**Why It Matters:** Provides official resignation documentation and triggers exit process.

**Related BRs:** BR-6

**System Must Support:**
- Self-service resignation submission
- Capture resignation reason
- Capture effective date and notice period
- Automatic manager notification
- Trigger approval workflow
- Store resignation documentation

**Inputs Needed:** Employee Profile (Resignation Reason)

**Downstream Impact:** Offboarding Approval Workflow

---

### OFF-019: Track Resignation Status
**What User Needs:** "As an Employee, I want to be able to track my resignation request status."

**Why It Matters:** Provides transparency during exit process.

**Related BRs:** BR-6

**System Must Support:**
- Self-service status viewing
- Show approval workflow progress
- Show clearance completion status
- Show final settlement timeline
- Notifications on status changes
- Estimated completion dates

**Inputs Needed:** Employee Profile (Resignation Reason)

**Downstream Impact:** Offboarding Approval Workflow

---

---

# 📋 ONBOARDING & OFFBOARDING BUSINESS RULES

| BR ID | BR Description | Applies To |
|-------|----------------|------------|
| **BR-4** | Employee separation needs an effective date and a clearly stated and identified reason for exit. Termination reviews based on performance must follow due process. | Offboarding |
| **BR-6** | Employee separation can be triggered by resignation. A clearly identified offboarding approval workflow should be identified (e.g., Employee resigning > Line Manager > Financial approval > HR processing/approval). | Offboarding |
| **BR-7** | Documents must be collected and verified by the HR department before the first working day. | Onboarding |
| **BR-8** | The orientation program must include an onboarding workflow. | Onboarding |
| **BR-9(a)** | Auto onboarding tasks are generated for HR (payroll & benefits' creation). | Onboarding |
| **BR-9(b)** | Auto onboarding tasks are generated for IT (allocation of email, laptop, system access). | Onboarding |
| **BR-9(c)** | Auto onboarding tasks are generated for Admin (allocation and assignment of workspace, ID badge). | Onboarding |
| **BR-9** | Leaves' Balance must be reviewed and settled (unused annuals to be encashed). | Offboarding |
| **BR-11(a, b)** | The orientation program must include an onboarding workflow and support department-specific tasks and training plans. | Onboarding |
| **BR-11** | Benefits plans are set to be auto-terminated as of the end of the notice period. | Offboarding |
| **BR-12** | The system must support sending reminders and task assignments to responsible parties, and track delivery and status accordingly. | Onboarding |
| **BR-13(a)** | Offboarding checklist must cover all asset types. | Offboarding |
| **BR-13(b, c)** | Clearance checklist required across departments (IT, HR, Admin, Finance). | Offboarding |
| **BR-14** | Final approvals/signature form should be filed to HR to complete the offboarding process. | Offboarding |
| **BR-17(a, b)** | Employee profile must be created from signed contract data. | Onboarding |
| **BR-19** | Access revocation required for security. | Offboarding |
| **BR-20** | The system should allow onboarding cancellation/termination of the created employee profile in case of a "no show". | Onboarding |
| **BR-3(c)** | Access revocation required upon termination. | Offboarding |

---

---

# 🔄 COMPLETE EMPLOYEE LIFECYCLE WORKFLOW SUMMARY

## Phase-by-Phase Flow with Data Handoffs

### PHASE 1: RECRUITMENT (Acquisition & Offer)
```
HR Manager defines job templates
  → HR Manager establishes hiring process stages
  → Templates stored and ready for use
  
HR Employee creates job posting from template
  → HR Employee previews posting
  → HR Employee publishes to careers page
  → System auto-posts to external job boards
  
Candidate uploads CV
  → Candidate provides data consent (GDPR)
  → Application stored in talent pool
  → HR notified of new application
  
HR tags referrals for priority
  → HR moves candidates through stages
  → System tracks all transitions
  → Automatic notifications sent
  
HR creates structured assessment forms
  → HR schedules interviews with panel
  → Panel receives calendar invites
  → Candidate receives notification
  → Panel submits feedback and scores
  → System aggregates scores
  
HR Manager monitors dashboard
  → Candidates receive status updates
  → Rejected candidates notified professionally
  → All communications logged
  
HR generates offer
  → Offer routed for approvals
  → Approved offer sent to candidate
  → Candidate signs electronically
  → System triggers pre-boarding tasks
  → **DATA HANDOFF TO ONBOARDING**
```

### PHASE 2: ONBOARDING (Integration & Provisioning)
```
[Receives: Signed offer letter, candidate data from Recruitment]

Candidate uploads signed contract and required forms
  → System triggers onboarding workflow
  
HR Manager creates onboarding checklist
  → HR Manager creates employee profile from contract
  → Employee profile activated in system
  
New Hire views tracker and receives reminders
  → New Hire uploads compliance documents
  → HR verifies documents
  
HR Employee reserves equipment and workspace
  → System Admin provisions system access
  → Accounts scheduled for activation on Day 1
  → Future revocation triggers set
  
HR Manager initiates payroll setup
  → System calculates pro-rated salary if mid-cycle
  → Signing bonus scheduled per contract
  → **DATA SENT TO PAYROLL MODULE**
  → **DATA SENT TO EMPLOYEE PROFILE**
  → **ACCESS REVOCATION SCHEDULE SENT TO OFFBOARDING (future use)**
```

### PHASE 3: OFFBOARDING (Separation & Clearance)
```
[Receives: Employee profile, access revocation schedule from Onboarding]

Employee submits resignation with reason
  → System triggers approval workflow
  → Employee tracks status in portal
  
OR

HR Manager initiates termination review
  → Reviews performance data and warnings
  → Documents justification
  → Approval workflow triggered
  
HR Manager creates offboarding checklist
  → Multi-department clearance initiated:
      • IT: Return laptop, phone, revoke access
      • Facilities: Return ID badge, keys, parking pass
      • Finance: Settle expenses, return credit card
      • Manager: Knowledge transfer, handover
  
System Admin revokes all access on termination date
  → Email disabled (with forwarding)
  → VPN access revoked
  → All system access disabled
  → Security audit logged
  
HR Manager waits for all department sign-offs
  → All departments must confirm clearance
  → Final settlement blocked until complete
  
HR Manager triggers final settlement
  → System calculates:
      • Pro-rated final salary
      • Unused leave encashment
      • Severance (if applicable)
      • Deductions for unreturned items
  → Benefits termination scheduled
  → **DATA SENT TO PAYROLL MODULE for final paycheck**
  → **DATA SENT TO LEAVES MODULE for leave settlement**
  
Final paycheck issued
  → Employee record moved to "Former Employee"
  → Complete audit trail archived
```

---

## Data Flow Across Phases

```
RECRUITMENT
  ↓
  Outputs:
  • Signed offer letter
  • Candidate personal data
  • Position, salary, start date
  • Signing bonus terms
  ↓
ONBOARDING
  ↓
  Outputs:
  • Employee profile (active)
  • Payroll initiation
  • System access provisioning
  • Access revocation schedule (for future)
  • Equipment assignments
  ↓
EMPLOYEE LIFECYCLE (not covered in this doc)
  ↓
OFFBOARDING
  ↓
  Outputs:
  • Final settlement calculation
  • Leave balance encashment
  • Benefits termination
  • Access revocation confirmation
  • Asset recovery confirmation
  • Employee record archived
```

---

---

# 📊 INTEGRATION POINTS WITH OTHER SUBSYSTEMS (UPDATED)

## Inputs from Other Subsystems

| Input From | Data Received | Used For |
|------------|---------------|----------|
| **Organizational Structure** | Jobs/Positions | Job template creation (REC-003) |
| **Time Management** | Calendar/Availability | Interview scheduling (REC-010, REC-021) |
| **Financial Approval** | Budget authorization | Offer approvals (REC-014) |
| **Performance Management** | Warnings, Performance Data | Termination justification (OFF-001) |
| **Leaves Module** | Leave balances | Final settlement calculation (OFF-013) |
| **Employee Profile** | Benefits, Resignation Status | Offboarding triggers and final pay (OFF-013) |

---

## Outputs to Other Subsystems

| Output To | Data Sent | Purpose |
|-----------|-----------|---------|
| **Employee Profile** | New hire information, Active employee record | Create and maintain employee data |
| **Payroll Module** | Payroll initiation, Signing bonuses, Final settlements | Process compensation |
| **IT/Access Systems** | Access provisioning requests, Access revocation | Manage system security |
| **Facilities/Admin** | Equipment reservations, Workspace assignments | Prepare physical resources |
| **Candidate Portal** | Application status | Real-time candidate visibility (REC-017) |
| **External Systems** | Job postings | Career site publishing (REC-023) |
| **Notifications System** | Status changes, Reminders, Alerts | Automated communications |
| **Leaves Module** | Leave encashment data | Final settlement |

---

---

# 🎯 KEY METRICS & ANALYTICS (UPDATED)

## Recruitment Metrics

| Report Type | Description | Users |
|-------------|-------------|-------|
| **Time-to-Hire** | Days from job posting to offer acceptance | HR Manager |
| **Source Effectiveness** | Which job boards/sources yield best candidates | HR Manager |
| **Pipeline Metrics** | Candidates per stage per position | HR Manager, HR Employee |
| **Conversion Rates** | % of candidates advancing per stage | HR Manager |
| **Referral Effectiveness** | Success rate of referred candidates | HR Manager |
| **Interview Completion** | Panel feedback completion rates | HR Manager |
| **Offer Acceptance Rate** | % of offers accepted vs rejected | HR Manager |

---

## Onboarding Metrics

| Report Type | Description | Users |
|-------------|-------------|-------|
| **Onboarding Completion Rate** | % of new hires completing onboarding by Day 1 | HR Manager |
| **Average Onboarding Duration** | Days from offer acceptance to first day readiness | HR Manager |
| **Document Compliance Rate** | % of new hires with all documents submitted on time | HR Employee, HR Manager |
| **Task Completion by Department** | Which departments complete onboarding tasks on time | HR Manager, Department Managers |
| **No-Show Rate** | % of accepted offers where candidate doesn't show up | HR Manager |
| **Time to Productivity** | Days from start date to full productivity | HR Manager |
| **New Hire Equipment Readiness** | % of new hires with all equipment on Day 1 | HR Employee, IT Manager |

---

## Offboarding Metrics

| Report Type | Description | Users |
|-------------|-------------|-------|
| **Voluntary vs Involuntary Turnover** | Resignation vs termination rates | HR Manager |
| **Average Notice Period** | Days between resignation and last day | HR Manager |
| **Clearance Completion Rate** | % of exits with all clearances completed | HR Manager |
| **Asset Recovery Rate** | % of company assets recovered from departing employees | HR Manager, Finance |
| **Final Settlement Accuracy** | % of final settlements calculated correctly first time | Payroll Manager, Finance |
| **Time to Full Clearance** | Days from last day to complete clearance | HR Manager |
| **Turnover by Department** | Which departments have highest turnover | HR Manager, Executives |
| **Exit Interview Completion** | % of departing employees completing exit interviews | HR Manager |

---

---

# ✅ EMPLOYEE LIFECYCLE SUBSYSTEM COMPLETION CHECKLIST (UPDATED)

## For HR Managers

### Recruitment
- [ ] Define standardized job description templates (REC-003)
- [ ] Establish hiring process stage templates (REC-004)
- [ ] Monitor recruitment progress dashboard (REC-009)
- [ ] Manage job offers and approvals (REC-014)
- [ ] Review recruitment analytics reports (BR-33)

### Onboarding
- [ ] Create onboarding task checklists (ONB-001)
- [ ] Access signed contracts to create employee profiles (ONB-002)
- [ ] Ensure automated account provisioning configured (ONB-013)
- [ ] Verify payroll initiation for new hires (ONB-018)
- [ ] Verify signing bonus processing (ONB-019)
- [ ] Monitor onboarding completion metrics

### Offboarding
- [ ] Initiate termination reviews with proper justification (OFF-001)
- [ ] Create offboarding checklists (OFF-006)
- [ ] Obtain multi-department clearance sign-offs (OFF-010)
- [ ] Trigger final settlement calculations (OFF-013)
- [ ] Monitor turnover analytics and exit trends

---

## For HR Employees

### Recruitment
- [ ] Preview and publish job postings (REC-023)
- [ ] Tag referral candidates (REC-030)
- [ ] Track candidates through stages (REC-008)
- [ ] Create structured assessment forms (REC-020)
- [ ] Schedule and coordinate interviews (REC-010, REC-021)
- [ ] Submit interview feedback and scores (REC-011)
- [ ] Send automated rejection notifications (REC-022)
- [ ] Generate and send electronic offer letters (REC-018)
- [ ] Trigger pre-boarding tasks (REC-029)

### Onboarding
- [ ] Reserve and track equipment for new hires (ONB-012)
- [ ] Verify document uploads and compliance (ONB-007)
- [ ] Coordinate with IT on access provisioning (ONB-009)
- [ ] Monitor new hire task completion
- [ ] Follow up on incomplete onboarding items

### Offboarding
- [ ] Process resignation requests
- [ ] Track clearance status across departments
- [ ] Follow up on unreturned assets
- [ ] Coordinate exit interviews

---

## For Candidates / New Hires

### Recruitment
- [ ] Upload CV and apply (REC-007)
- [ ] Provide data processing consent (REC-028)
- [ ] Receive application status updates (REC-017)
- [ ] Attend scheduled interviews
- [ ] Sign offer letter electronically (REC-018)

### Onboarding
- [ ] Upload signed contract and required forms
- [ ] View onboarding tracker (ONB-004)
- [ ] Respond to reminders and notifications (ONB-005)
- [ ] Upload compliance documents (ONB-007)
- [ ] Complete all assigned onboarding tasks
- [ ] Attend orientation sessions

---

## For Employees (Offboarding)
- [ ] Submit resignation request with reasoning (OFF-018)
- [ ] Track resignation status (OFF-019)
- [ ] Complete knowledge transfer to team
- [ ] Return all company assets (laptop, ID, keys)
- [ ] Complete exit interview
- [ ] Attend exit clearance meetings

---

## For System Administrators

### Recruitment
- [ ] Configure job posting automation (BR-6)
- [ ] Set up email templates (BR-36)
- [ ] Configure consent forms (BR-28, NFR-33)
- [ ] Set up e-signature integration (BR-26d)
- [ ] Configure communication logging (BR-37)

### Onboarding
- [ ] Configure automated account provisioning (ONB-009)
- [ ] Set up access provisioning workflows (ONB-013)
- [ ] Configure IT system integrations
- [ ] Set up SSO/Active Directory sync
- [ ] Configure no-show handling (BR-20)

### Offboarding
- [ ] Configure automated access revocation (OFF-007)
- [ ] Set up security access controls
- [ ] Configure asset tracking system
- [ ] Set up multi-department workflow routing

---

## For Payroll Specialists

### Onboarding
- [ ] Verify payroll initiation triggers (ONB-018)
- [ ] Process signing bonuses per contract (ONB-019)
- [ ] Verify pro-rated salary calculations for mid-cycle starts

### Offboarding
- [ ] Calculate final settlements (OFF-013)
- [ ] Process leave encashments
- [ ] Calculate severance payments (if applicable)
- [ ] Process deductions for unreturned assets
- [ ] Verify benefits termination dates

---

## For IT/System Admins

### Onboarding
- [ ] Provision email accounts (ONB-009)
- [ ] Provision system access per role (ONB-009)
- [ ] Configure SSO/Active Directory accounts
- [ ] Prepare laptops and equipment
- [ ] Test access before Day 1

### Offboarding
- [ ] Revoke all system access on termination date (OFF-007)
- [ ] Disable email (configure forwarding if needed)
- [ ] Revoke VPN access
- [ ] Disable building access cards
- [ ] Revoke application-specific access
- [ ] Archive or transfer file ownership

---

## For Facilities/Admin Teams

### Onboarding
- [ ] Reserve workspace for new hires (ONB-012)
- [ ] Prepare access badges (ONB-012)
- [ ] Assign parking passes
- [ ] Set up desk and equipment

### Offboarding
- [ ] Recover ID badges and keys
- [ ] Recover parking passes
- [ ] Clear workspace
- [ ] Update space allocation records

---

## For Finance Teams

### Offboarding
- [ ] Verify expense report settlements
- [ ] Recover company credit cards
- [ ] Sign off on financial clearance
- [ ] Approve final settlement amounts
- [ ] Process final payment

---

## For Line Managers

### Recruitment
- [ ] Provide input on job requirements
- [ ] Participate in interview panels
- [ ] Approve/reject candidates
- [ ] Approve job offers

### Onboarding
- [ ] Welcome new hire on Day 1
- [ ] Assign buddy/mentor
- [ ] Conduct department orientation
- [ ] Set initial goals and expectations

### Offboarding
- [ ] Approve resignation requests
- [ ] Ensure knowledge transfer completed
- [ ] Complete manager clearance sign-off
- [ ] Conduct exit interview (optional)
- [ ] Update team structure

---

**Document Complete. All three employee lifecycle phases (Recruitment, Onboarding, Offboarding) fully documented with user stories, business rules, workflows, and integration points cross-referenced.**

---

---

# 📊 DETAILED WORKFLOW ELABORATION: STEP-BY-STEP WITH DATA FLOWS

**This section provides a comprehensive step-by-step breakdown of the entire employee lifecycle, showing WHO does WHAT, WHICH user stories and business rules apply, and HOW data flows between steps. Use this section to understand the complete end-to-end process.**

---

## PHASE I: RECRUITMENT (Acquisition & Offer)

### Step 1: Setup Templates

| Element | Details |
|---------|---------|
| **Actor** | HR Manager |
| **Action / Process** | Define standardized job description templates [REC-003] and establish hiring process templates [REC-004]. |
| **Why This Step Matters** | Creates foundation for consistent, professional job postings and standardized candidate evaluation across entire organization. |
| **Supporting User Stories & Rules** | **US:** REC-003, REC-004<br>**BR:** Process template defines stages and progress percentage. |
| **Outputs & Data Flow** | **Output:** Standardized Templates (Stored in system)<br>**Data Flow:** Templates consumed by job posting step (REC-023). Ready for reuse across all departments. |

**Real-World Example:**  
HR Manager creates "Software Engineer" template with: Required skills (Python, JavaScript), Education (BS Computer Science), Experience (3+ years), Salary range ($80k-$120k). Creates hiring process: Application → Phone Screen (Week 1) → Technical Interview (Week 2) → Final Interview (Week 3) → Offer (Week 4). Now every Software Engineer posting uses same template, ensuring fairness and consistency.

---

### Step 2: Publish Job

| Element | Details |
|---------|---------|
| **Actor** | HR Employee |
| **Action / Process** | Preview and publish jobs on the company careers page [REC-023]. |
| **Why This Step Matters** | Makes position visible to candidates and attracts qualified applicants. |
| **Supporting User Stories & Rules** | **US:** REC-023<br>**BR:** Posting must be automatic once approved (BR-6). |
| **Outputs & Data Flow** | **Output:** Active Job Posting (Live on careers page)<br>**Data Flow:** Feeds job list to Candidate Dashboard. Updates Organizational Structure (position marked "Vacant" or "Hiring"). Automatically posts to external job boards if configured. |

**Real-World Example:**  
HR Employee selects "Software Engineer" template, customizes for specific team (Frontend team needs React experience), previews posting, clicks "Publish." System automatically: (1) Posts to company careers page, (2) Posts to LinkedIn, Indeed, Glassdoor, (3) Sends email to internal employees for referrals, (4) Updates org chart showing "Frontend Engineer - Open Position."

---

### Step 3: Application & Consent

| Element | Details |
|---------|---------|
| **Actor** | Candidate |
| **Action / Process** | Upload CV [REC-007] and give consent for personal-data processing [REC-028]. |
| **Why This Step Matters** | Candidate enters system legally (with proper consent) and provides information needed for evaluation. |
| **Supporting User Stories & Rules** | **US:** REC-007, REC-028<br>**BR:** Storing applications requires applicant authorization (BR-28, NFR-33 GDPR compliance). |
| **Outputs & Data Flow** | **Output:** Applicant Record created; Consent Logged with timestamp<br>**Data Flow:** CV stored in Talent Pool; consent enables compliance checks and background verification later. Candidate appears in HR dashboard for review. |

**Real-World Example:**  
Sarah sees job posting, clicks "Apply Now." She uploads her resume (PDF), fills in contact info. System shows: "By clicking Submit, you consent to Company processing your personal data per GDPR. Your data will be stored for 2 years." Sarah clicks consent checkbox and submits. System logs: "Sarah Johnson - Consent granted May 1, 2025 at 2:15 PM." Her application now appears in HR's candidate pipeline.

---

### Step 4: Pipeline & Tags

| Element | Details |
|---------|---------|
| **Actor** | HR Employee |
| **Action / Process** | Tag candidates as referrals [REC-030] and track candidates through each stage of the hiring process [REC-008]. |
| **Why This Step Matters** | Organizes candidate pipeline and applies business rules (referral priority) for efficient processing. |
| **Supporting User Stories & Rules** | **US:** REC-030, REC-008<br>**BR:** Applications tracked through defined stages (BR-9). Referrals get preferential filtering (BR-14, BR-25). |
| **Outputs & Data Flow** | **Output:** Updated Candidate Status (e.g., "Application" → "Screening"); Referral Tagged<br>**Data Flow:** Status change triggers notifications (system sends email to candidate: "Your application is now under review"). Referral tag affects priority in ranking algorithms. |

**Real-World Example:**  
HR sees Sarah's application came through employee referral link (John from Engineering referred her). HR clicks "Tag as Referral." System automatically: (1) Moves her to top of screening queue, (2) Credits John with referral for bonus tracking, (3) Sends John email: "Thanks for referring Sarah. We'll keep you updated." HR moves Sarah from "Application" to "Phone Screen" stage. Sarah receives email: "Congratulations! Your application has been selected for phone screening."

---

### Step 5: Evaluation

| Element | Details |
|---------|---------|
| **Actor** | HR Employee |
| **Action / Process** | Use structured assessment and scoring forms per role [REC-020], coordinate interviews [REC-021], and schedule/manage invitations [REC-010]. Submit feedback and scores [REC-011]. |
| **Why This Step Matters** | Ensures objective, consistent, legally defensible candidate evaluation with complete audit trail. |
| **Supporting User Stories & Rules** | **US:** REC-020, REC-021, REC-010, REC-011<br>**BR:** Structured assessment forms required (BR-21, BR-23); ranking rules enforced (BR-10, BR-22). |
| **Outputs & Data Flow** | **Output:** Interview Feedback / Score Completed (e.g., Technical: 8/10, Culture Fit: 9/10, Communication: 7/10)<br>**Data Flow:** Scores logged to candidate record for ranking. System can now compare: Sarah (Total: 24/30) vs Tom (Total: 20/30). Sarah ranks higher automatically. |

**Real-World Example:**  
HR schedules Sarah's technical interview using system. System: (1) Checks calendar availability of 3 engineering managers, (2) Finds common time slot (Tuesday 2pm), (3) Sends calendar invites to panel, (4) Sends email to Sarah with video call link. After interview, each panel member submits structured form: Technical Skills (0-10), Problem Solving (0-10), Communication (0-10), Culture Fit (0-10). System aggregates: Sarah scored 34/40 average across 3 interviewers. This becomes her permanent evaluation record.

---

### Step 6: Monitoring & Communication

| Element | Details |
|---------|---------|
| **Actor** | HR Manager / Candidate |
| **Action / Process** | HR monitors recruitment progress [REC-009]; candidates get automatic updates [REC-017]; automated rejections sent [REC-022]. |
| **Why This Step Matters** | Provides transparency to all stakeholders and maintains professional candidate experience. |
| **Supporting User Stories & Rules** | **US:** REC-009, REC-017, REC-022<br>**BR:** Status tracking must be real-time and visualized (BR-27); automated notifications required (BR-36); communication logs stored (BR-37). |
| **Outputs & Data Flow** | **Output:** Progress Dashboard View (HR sees: 50 applicants, 20 screened, 8 interviewed, 2 in final round); Status Notifications sent to candidates<br>**Data Flow:** Consumes pipeline data from REC-008. Generates reports on time-to-hire, bottlenecks, etc. |

**Real-World Example:**  
HR Manager opens dashboard and sees: "Frontend Engineer position - Posted 30 days ago. 127 applications, 45 screened, 12 phone interviews, 5 technical interviews, 2 final round. Average time in screening: 5 days (WARNING: Industry average is 3 days - process is slow)." Meanwhile, Tom (who wasn't selected) receives professional email: "Thank you for your interest in our Frontend Engineer position. While your background is impressive, we've decided to move forward with other candidates whose experience more closely matches our needs. We encourage you to apply for future openings." All communication logged for compliance.

---

### Step 7: Offer & Transition

| Element | Details |
|---------|---------|
| **Actor** | HR Manager / HR Employee |
| **Action / Process** | Manage job offers and approvals [REC-014]; generate and send e-signed offers [REC-018]; send automated rejections [REC-022]; trigger pre-boarding [REC-029]. |
| **Why This Step Matters** | Closes hiring process and seamlessly hands off to onboarding without manual intervention. |
| **Supporting User Stories & Rules** | **US:** REC-014, REC-018, REC-022, REC-029<br>**BR:** Offer acceptance triggers Onboarding (BR-26c); offer data used for contract creation (BR-26a,d); communications logged (BR-37). |
| **Outputs & Data Flow** | **Output:** Signed Offer Letter (Stored as legal document); Rejection Sent (for non-selected candidates)<br>**Data Flow:** Triggers Onboarding initiation automatically; data populates Employee Profile (name, position, salary, start date all flow from offer to employee record); Tom receives rejection email with stored log. |

**Real-World Example:**  
HR creates offer for Sarah: "$95,000 salary, $5,000 signing bonus, start date June 1." Offer goes through approval workflow: HR Manager approves → Finance approves (budget available) → Legal reviews (standard terms). System generates offer PDF with all terms, sends to Sarah via DocuSign. Sarah signs electronically on May 15. The moment she signs: (1) System triggers onboarding module, (2) Creates onboarding checklist, (3) Sends welcome email, (4) Notifies IT to prepare laptop, (5) Notifies Facilities to assign desk, (6) Initiates payroll setup. Tom and other finalists receive professional rejection emails.

**Critical Data Handoff:** All data from recruitment (name, position, salary, start date, signing bonus, department, manager) automatically flows to onboarding. No manual re-entry required.

---

---

## PHASE II: ONBOARDING (Integration & Provisioning)

### Step 8: Profile Creation & Checklist

| Element | Details |
|---------|---------|
| **Actor** | HR Manager |
| **Action / Process** | Create onboarding task checklists [ONB-001]; access signed contract to create employee profile [ONB-002]. |
| **Why This Step Matters** | Transforms "candidate" record into "employee" record with all systems initialized. |
| **Supporting User Stories & Rules** | **US:** ONB-001, ONB-002<br>**BR:** Triggered by offer acceptance (BR-26c); checklists customizable per department (BR-8, BR-11). |
| **Outputs & Data Flow** | **Output:** Employee Profile (Active with employee ID assigned); Onboarding Checklist (Activated with tasks assigned to stakeholders)<br>**Data Flow:** Uses signed contract data from Recruitment (Step 7); outputs to Employee Profile subsystem (permanent record created); checklist feeds task tracker (ONB-004). |

**Real-World Example:**  
Sarah signed offer on May 15 for June 1 start. On May 16, HR clicks "Create Employee Profile." System automatically: (1) Assigns employee ID: EMP-2025-1847, (2) Creates email: sarah.johnson@company.com, (3) Adds to org chart under "Frontend Engineering Team" reporting to Manager John Smith, (4) Creates checklist: HR tasks (upload docs, complete I-9), IT tasks (prep laptop, create accounts), Facilities tasks (assign desk, create badge), Sarah's tasks (upload ID, review handbook). Each stakeholder receives their task list.

---

### Step 9: Compliance & Tracking

| Element | Details |
|---------|---------|
| **Actor** | New Hire |
| **Action / Process** | View onboarding tracker [ONB-004]; receive reminders [ONB-005]; upload compliance documents [ONB-007]. |
| **Why This Step Matters** | Ensures new hire completes legal requirements before work begins. |
| **Supporting User Stories & Rules** | **US:** ONB-004, ONB-005, ONB-007<br>**BR:** Tracker and reminders required (BR-11, BR-12); documents stored securely and verified before first day (BR-7). |
| **Outputs & Data Flow** | **Output:** Documents Uploaded (Stored in secure employee file); Task Progress Updated (checklist items marked complete)<br>**Data Flow:** Documents stored in Employee Profile subsystem for compliance audit; HR receives notification when Sarah uploads each document for verification. |

**Real-World Example:**  
Sarah receives email May 17: "Welcome! Your first day is June 1. Please complete these tasks." She logs into portal and sees tracker: ⬜ Upload government ID (Due: May 24), ⬜ Complete I-9 form (Due: May 24), ⬜ Upload certifications (Due: May 27), ⬜ Review employee handbook (Due: May 31). She uploads her driver's license and diploma. HR receives notification: "Sarah uploaded 2 documents - please verify." HR reviews and approves. Sarah's tracker updates: ✅ Upload government ID (Verified May 17), ✅ Upload certifications (Verified May 17).

---

### Step 10: Resource Provisioning

| Element | Details |
|---------|---------|
| **Actor** | HR Employee / System Admin |
| **Action / Process** | Reserve and track equipment [ONB-012]; provision secure system access [ONB-009]. |
| **Why This Step Matters** | Ensures new hire has all tools needed from minute they arrive on Day 1. |
| **Supporting User Stories & Rules** | **US:** ONB-012, ONB-009<br>**BR:** IT and payroll access automated (BR-9b); all resources tracked for asset management (BR-9c). |
| **Outputs & Data Flow** | **Output:** Access Granted (sarah.johnson@company.com created, SSO enabled); Equipment Reserved (MacBook Pro #8472 assigned to Sarah)<br>**Data Flow:** Logged for audit; feeds Time Management subsystem (Sarah can now clock in/out once active); feeds Asset Management (laptop #8472 tracked to Sarah); feeds IT Security (access permissions logged). |

**Real-World Example:**  
May 20: Facilities receives task "Assign desk for Sarah Johnson, start June 1." They reserve Desk #247 in Engineering section, create access badge, assign parking spot P-142. IT receives task "Provision access for Sarah Johnson." They: (1) Create sarah.johnson@company.com, (2) Provision SSO access to Slack, GitHub, Jira, (3) Prepare MacBook Pro with development tools, (4) Create VPN certificate, (5) Schedule all access to activate June 1 at 8am. May 31: Everything ready. June 1 at 8am: Sarah's badge works at front door, her email is active, laptop logs in automatically, all tools accessible.

---

### Step 11: Payroll Initiation & Benefits

| Element | Details |
|---------|---------|
| **Actor** | HR Manager |
| **Action / Process** | Automate payroll initiation upon contract signing [ONB-018]; process signing bonuses [ONB-019]. |
| **Why This Step Matters** | Ensures new hire gets paid correctly without any manual calculation errors. |
| **Supporting User Stories & Rules** | **US:** ONB-018, ONB-019<br>**BR:** Bonuses treated as distinct payroll components (BR-9a); payroll trigger automatic (links to Payroll subsystem REQ-PY-23, REQ-PY-27). |
| **Outputs & Data Flow** | **Output:** Payroll Initiation Triggered (Sarah added to June payroll cycle); Bonus Processed ($5,000 signing bonus scheduled for June 30 paycheck)<br>**Data Flow:** Triggers Payroll subsystem processing steps; data sent: Employee ID, Salary ($95k annual = $7,916.67 monthly), Start Date (June 1 - pro-rated to $5,645.16 for June), Signing Bonus ($5,000), Bank Account info, Tax withholding. |

**Real-World Example:**  
May 16 (day after Sarah signs offer): Payroll system automatically calculates: (1) Annual salary: $95,000, (2) Monthly: $7,916.67, (3) Sarah starts June 1, works 21 days of June (June has 30 days), (4) Pro-rated June salary: $95,000 × (21/365) = $5,465.75, (5) Signing bonus: $5,000, (6) **First paycheck (June 30): $5,465.75 + $5,000 = $10,465.75 (before taxes)**. Payroll specialist doesn't manually calculate anything—it's automatic. Sarah's bank account info from onboarding flows to payroll automatically.

---

### Step 12: Scheduled Access Management

| Element | Details |
|---------|---------|
| **Actor** | HR Manager / System Admin |
| **Action / Process** | Schedule automatic provisioning and revocation of accounts [ONB-013]. |
| **Why This Step Matters** | Creates security controls that will protect company when employee eventually leaves (could be years later). |
| **Supporting User Stories & Rules** | **US:** ONB-013<br>**BR:** Provisioning and security must be consistent (BR-9b); support no-show handling (BR-20). |
| **Outputs & Data Flow** | **Output:** Scheduled Revocation Flag (Future trigger set: "When Sarah's employee status changes to 'Terminated' or 'Resigned,' revoke all access within 24 hours")<br>**Data Flow:** Info passed to Offboarding subsystem (OFF-007) for future security control when Sarah eventually leaves company. |

**Real-World Example:**  
When Sarah's profile is created, system automatically sets future rules: (1) **If employee status changes to "Resigned":** Start offboarding checklist, schedule access revocation for last working day, (2) **If employee status changes to "Terminated":** Immediate access revocation, (3) **If June 1 arrives and Sarah doesn't show up ("no show"):** HR can click "Cancel Onboarding" - system automatically revokes prepared access, releases laptop back to inventory, cancels payroll, notifies all stakeholders. This prevents years-later security incidents where "we forgot to revoke access when someone left."

---

---

## PHASE III: OFFBOARDING (Separation & Clearance)

### Step 13: Exit Initiation

| Element | Details |
|---------|---------|
| **Actor** | Employee / HR Manager |
| **Action / Process** | Employee submits resignation [OFF-018] or HR initiates termination review [OFF-001]. Track status [OFF-019]. |
| **Why This Step Matters** | Creates official exit record and triggers all downstream processes (clearance, access revocation, final pay). |
| **Supporting User Stories & Rules** | **US:** OFF-018, OFF-019, OFF-001<br>**BR:** Separation may result from resignation or termination; justification mandatory (BR-4, BR-6); due process required for terminations. |
| **Outputs & Data Flow** | **Output:** Resignation Request Submitted (with effective date, notice period, reason); OR Termination Review Started (with documented justification from Performance Management subsystem)<br>**Data Flow:** Status triggers workflow approval (Manager → HR → Finance); triggers clearance checklist creation; updates employee status from "Active" to "Exiting"; sends notifications to all stakeholders. |

**Real-World Example:**  
**Scenario A - Resignation:** Sarah logs in and submits: "I am resigning effective August 31, 2025. Reason: Relocating to another city. Notice period: 4 weeks per contract." System: (1) Calculates last working day = August 31, (2) Sends notification to her manager for approval, (3) Creates offboarding checklist, (4) Sarah can track status in portal: ✅ Submitted, ⏳ Manager Approval Pending, ⬜ HR Processing, ⬜ Clearance, ⬜ Final Settlement.

**Scenario B - Termination:** Manager escalates John for repeated performance issues. HR reviews: (1) Performance Management subsystem shows: 3 documented warnings, 2 failed improvement plans, consistent underperformance scores, (2) HR determines termination is justified, (3) Creates termination record with all documentation attached, (4) Sends for approval workflow, (5) Once approved, system triggers immediate offboarding with effective date = termination date.

---

### Step 14: Clearance & Assets

| Element | Details |
|---------|---------|
| **Actor** | HR Manager |
| **Action / Process** | Manage offboarding checklist and departmental sign-offs (IT, Finance, Facilities, etc.) [OFF-006, OFF-010]. |
| **Why This Step Matters** | Ensures no company property is lost and all departments confirm employee has no outstanding obligations. |
| **Supporting User Stories & Rules** | **US:** OFF-006, OFF-010<br>**BR:** Multi-department clearance required (BR-13a, BR-13b,c); completion tracked; final settlement blocked until all cleared (BR-14). |
| **Outputs & Data Flow** | **Output:** Offboarding Checklist Active (all departments see their tasks); Clearance Sign-offs Logged (IT ✅, Facilities ⏳, Finance ⬜, Manager ⬜)<br>**Data Flow:** Clearance governs final payroll release—system won't process final pay until all departments sign off. This prevents paying someone who still has unreturned laptop worth $2,000. |

**Real-World Example:**  
Sarah's last day is August 31. System creates checklist:

**IT Department (Assigned to IT Manager):**
- ☐ Laptop returned (MacBook Pro #8472)
- ☐ Mobile phone returned
- ☐ VPN token returned
- ☐ File ownership transferred to manager
- ☐ Ready to revoke access

**Facilities (Assigned to Facilities Manager):**
- ☐ ID badge returned
- ☐ Office keys returned
- ☐ Parking pass returned

**Finance (Assigned to Finance Team):**
- ☐ Expense reports settled
- ☐ Company credit card returned
- ☐ No outstanding debts

**Manager (Assigned to John Smith):**
- ☐ Knowledge transfer completed
- ☐ No pending projects
- ☐ Handover document signed

August 28: IT signs off ✅ (all items returned). August 29: Facilities signs off ✅. August 30: Finance signs off ✅. August 31: Manager signs off ✅. **Final paycheck now released because all departments confirmed clearance.**

---

### Step 15: Security Revocation

| Element | Details |
|---------|---------|
| **Actor** | System Admin |
| **Action / Process** | Revoke system and account access on termination [OFF-007]. |
| **Why This Step Matters** | Critical security control preventing unauthorized access by former employees. |
| **Supporting User Stories & Rules** | **US:** OFF-007<br>**BR:** Access revocation required for security (BR-3c, BR-19). |
| **Outputs & Data Flow** | **Output:** Access Disabled (Logged with timestamp: "Sarah Johnson - All access revoked August 31, 2025 at 5:00 PM")<br>**Data Flow:** Logs stored in audit trail for security compliance; confirms ONB-013 revocation schedule was executed; feeds Security subsystem with revocation confirmation. |

**Real-World Example:**  
August 31 at 5:00 PM (end of Sarah's last working day), system automatically executes:

1. **Email:** sarah.johnson@company.com disabled. Emails forward to her manager for 30 days (in case clients email her).
2. **SSO/Active Directory:** Account disabled—can't log into any company system.
3. **VPN:** Certificate revoked—can't connect to company network remotely.
4. **Building Access:** Badge #2847 deactivated—can't enter building.
5. **Application Access:** Slack (disabled), GitHub (access removed from all repos), Jira (account deactivated), AWS (permissions revoked).
6. **Audit Log Generated:**
```
August 31, 2025 5:00 PM - OFFBOARDING REVOCATION EXECUTED
Employee: Sarah Johnson (EMP-2025-1847)
Reason: Resignation
- Email: DISABLED (forwarding to john.smith@company.com for 30 days)
- SSO: DISABLED
- VPN: REVOKED
- Badge #2847: DEACTIVATED
- Slack: DISABLED
- GitHub: ACCESS REMOVED
- Jira: DEACTIVATED
- AWS: PERMISSIONS REVOKED
All revocations confirmed. Security protocol complete.
```

This happens automatically—no manual checklist for IT to follow, preventing human error.

---

### Step 16: Final Settlement

| Element | Details |
|---------|---------|
| **Actor** | HR Manager |
| **Action / Process** | Trigger final pay calculation and benefits termination [OFF-013]. |
| **Why This Step Matters** | Ensures employee receives all entitled compensation per legal requirements. |
| **Supporting User Stories & Rules** | **US:** OFF-013<br>**BR:** Final pay includes unused leave, deductions, loans, severance (BR-9, BR-11); benefits auto-terminate at notice period end. |
| **Outputs & Data Flow** | **Output:** Final Pay Calculation Triggered (detailed breakdown created); Benefits Termination Scheduled (health insurance ends August 31)<br>**Data Flow:** Sends encashment data from Leaves subsystem (Sarah has 5 unused vacation days = $1,826.92); triggers Payroll subsystem processing; benefits termination sent to Benefits subsystem. |

**Real-World Example - Sarah's Final Settlement:**

**Last Working Day:** August 31, 2025  
**Calculation Date:** September 1, 2025  
**Payment Date:** September 15, 2025 (regular payroll date)

**ADDITIONS:**
- **August Pro-Rated Salary:** $95,000 × (31/365) = $8,082.19
- **Unused Vacation Days (5 days):** ($95,000 / 260 working days) × 5 = $1,826.92
- **Accrued but Unpaid Bonus:** $2,000 (quarterly bonus pro-rated)
- **Severance:** $0 (voluntary resignation - no severance per policy)

**DEDUCTIONS:**
- **Unreturned Items:** -$0 (all items returned and verified)
- **Outstanding Loan:** -$0 (no loans)
- **Pro-Rated Benefits:** -$150 (final health insurance premium)

**TOTAL FINAL PAYMENT (GROSS):** $11,759.11  
**After Taxes/Deductions:** ~$8,500 (approximate net)

**BENEFITS TERMINATION:**
- Health Insurance: Coverage ends August 31, 2025 (COBRA offered)
- Life Insurance: Coverage ends August 31, 2025
- 401(k): Vested amount = 100% (Sarah worked 3 years), transferred to her control
- Stock Options: Vesting stopped August 31; 90 days to exercise vested options

**System automatically:**
1. Calculates everything above
2. Gets approval from Finance
3. Processes payment on September 15
4. Sends Sarah email with detailed breakdown
5. Provides COBRA enrollment information
6. Provides 401(k) rollover information

**What flows to Payroll subsystem:**
- Employee ID: EMP-2025-1847
- Final pay components (salary + vacation + bonus)
- Deductions
- Bank account (final direct deposit)
- Tax withholding calculations
- Final pay authorization (all clearances complete ✅)

---

---

# 🔄 CRITICAL DATA HANDOFFS SUMMARY

## What Data Flows Where (Complete Picture)

### Recruitment → Onboarding
```
DATA TRANSFERRED:
✓ Full Name
✓ Contact Information (email, phone, address)
✓ Position/Job Title
✓ Department
✓ Manager/Supervisor
✓ Salary (annual)
✓ Start Date
✓ Signing Bonus Terms
✓ Employment Type (full-time, part-time, contract)
✓ Signed Offer Letter (PDF)
✓ Benefits Election (from offer)

TRIGGER: Candidate electronically signs offer letter

RESULT: Onboarding checklist automatically created
```

### Onboarding → Employee Profile Subsystem
```
DATA TRANSFERRED:
✓ Employee ID (EMP-2025-XXXX)
✓ All recruitment data (above)
✓ Uploaded compliance documents (ID, certifications)
✓ Emergency contacts
✓ Bank account information
✓ Tax withholding forms (W-4)
✓ Benefits enrollment
✓ Equipment assignments (laptop #, desk #, badge #)
✓ System access permissions

TRIGGER: HR creates employee profile from contract

RESULT: Permanent employee record created
```

### Onboarding → Payroll Subsystem
```
DATA TRANSFERRED:
✓ Employee ID
✓ Annual Salary
✓ Start Date (for pro-rating)
✓ Signing Bonus Amount & Schedule
✓ Bank Account (routing #, account #)
✓ Tax Withholding (federal, state, local)
✓ Benefits Deductions (health insurance, 401k)
✓ Pay Frequency (monthly, bi-weekly)

TRIGGER: Contract signing date

RESULT: Employee added to payroll cycle
```

### Onboarding → IT/Access Systems
```
DATA TRANSFERRED:
✓ Full Name
✓ Department
✓ Position/Role
✓ Manager (for org chart)
✓ Start Date (for access activation)
✓ Required System Access (per role)
✓ Equipment Needs (per department standards)

TRIGGER: Employee profile created

RESULT: Accounts provisioned, equipment prepared
```

### Employee Profile → Offboarding
```
DATA TRANSFERRED:
✓ Employee ID
✓ Employment History
✓ Current Salary
✓ Benefits Enrollment
✓ Assigned Equipment (from Onboarding)
✓ System Access List (from Onboarding)
✓ Manager
✓ Department

TRIGGER: Resignation submitted OR Termination initiated

RESULT: Offboarding checklist created
```

### Leaves Subsystem → Offboarding
```
DATA TRANSFERRED:
✓ Unused Vacation Days
✓ Unused Sick Days
✓ Accrued Leave Balance
✓ Leave Policies (encashment rules)

TRIGGER: Final settlement calculation

RESULT: Leave encashment added to final pay
```

### Performance Management → Offboarding (Terminations)
```
DATA TRANSFERRED:
✓ Performance Review History
✓ Written Warnings
✓ Performance Improvement Plans
✓ Manager Documentation

TRIGGER: Termination review initiated

RESULT: Justification documented for legal compliance
```

### Offboarding → Payroll Subsystem
```
DATA TRANSFERRED:
✓ Last Working Date
✓ Unused Leave Balance (for encashment)
✓ Severance Terms (if applicable)
✓ Deductions for Unreturned Assets
✓ Outstanding Loans
✓ Clearance Completion Status (block payment until cleared)

TRIGGER: All department clearances signed off

RESULT: Final paycheck calculated and processed
```

---

**This completes the comprehensive end-to-end documentation with step-by-step workflows, data flows, and real-world examples for the entire Employee Lifecycle Subsystem (Recruitment → Onboarding → Offboarding).**

