# Part 2 — BRD & Business Analysis Specification

 This part defines the **Business Analysis layer** of the LLM Application Development Framework (LADF).

 The goal is to transform:

 > **Raw / ambiguous business requirement → complete, testable, architect-ready Business Requirement Package**

 The Business Analyst should **not design LangChain chains, prompts, agents, models, vector databases, or Python classes** at this stage.

 The BA defines **what the business needs and what successful behavior looks like**.

---

 # 1\. Business Analysis Stage

 The complete BA flow should be:

```
Raw Business Request
        ↓
Requirement Intake
        ↓
Stakeholder Discovery
        ↓
Problem Analysis
        ↓
Business Objective
        ↓
User / Actor Analysis
        ↓
Use Case Analysis
        ↓
Business Process
        ↓
Functional Requirements
        ↓
Business Rules
        ↓
Data / Input / Output Requirements
        ↓
Non-Functional Business Expectations
        ↓
Constraints / Assumptions / Dependencies
        ↓
Scope Definition
        ↓
Acceptance Criteria
        ↓
Success Metrics
        ↓
Risks / Open Questions
        ↓
BRD
        ↓
BA Review
        ↓
Business Approval
        ↓
Architect
```

 The output of this entire stage is the:

 # **Business Requirement Package**

---

 # 2\. Business Requirement Package

 I recommend the following artifacts.

```
BA-PACKAGE/
│
├── 01_REQUIREMENT_INTAKE
├── 02_BR​​D
├── 03_STAKEHOLDER_ANALYSIS
├── 04_PERSONAS
├── 05_USE_CASES
├── 06_USER_STORIES
├── 07_USER_JOURNEYS
├── 08_BUSINESS_PROCESS
├── 09_FUNCTIONAL_REQUIREMENTS
├── 10_BUSINESS_RULES
├── 11_DATA_REQUIREMENTS
├── 12_NON_FUNCTIONAL_REQUIREMENTS
├── 13_SCOPE
├── 14_CONSTRAINTS
├── 15_ASSUMPTIONS
├── 16_DEPENDENCIES
├── 17_ACCEPTANCE_CRITERIA
├── 18_SUCCESS_METRICS
├── 19_RISKS
├── 20_OPEN_QUESTIONS
└── 21_REQUIREMENT_TRACEABILITY
```

 Not every project needs a separate physical file for every item.

 For a small project, these can be sections inside one BRD.

 For a large project, each can become its own controlled artifact.

---

 # 3\. Artifact 01 — Requirement Intake

 This is the **first formal artifact**.

 The BA receives a raw request and records it without prematurely interpreting it.

 ## Purpose

 Capture:

 - Who requested it
- What was requested
- Why it was requested
- Initial business value
- Known constraints
- Initial scope
- Questions requiring discovery

---

 ## Copy-Paste Template

```
# LADF-001 — Requirement Intake

## 1. Document Control

| Field | Value |
|---|---|
| Requirement ID | REQ-XXX |
| Requirement Name | |
| Project | |
| Requestor | |
| Business Owner | |
| Business Analyst | |
| Date Raised | |
| Target Date | |
| Priority | |
| Status | Draft |
| Version | 0.1 |

---

## 2. Raw Business Request

### Original Request

> [Capture the request as received.]

### Request Source

- Business meeting
- Email
- Product request
- Customer request
- Management request
- Existing system issue
- Other

---

## 3. Business Problem

What problem is the business currently experiencing?

[Describe the problem.]

---

## 4. Desired Outcome

What outcome does the requester expect?

[Describe desired outcome.]

---

## 5. Initial Users

Who is expected to use the proposed solution?

- [User type]
- [User type]

---

## 6. Initial Scope

### In Scope

- [Item]

### Potentially Out of Scope

- [Item]

---

## 7. Known Constraints

- [Constraint]

---

## 8. Known Dependencies

- [Dependency]

---

## 9. Initial Success Indicators

- [Metric]

---

## 10. Initial Questions

1. [Question]
2. [Question]
3. [Question]

---

## 11. BA Assessment

### Requirement Clarity

[Low / Medium / High]

### Business Value

[Low / Medium / High]

### Complexity

[Low / Medium / High / Unknown]

### AI Relevance

[None / Possible / Required / Unknown]

---

## 12. Next Action

[Discovery / Clarification / Architecture Assessment / Reject / Backlog]
```

---

 # 4\. Example — Requirement Intake

 Suppose the business says:

 > "We need an AI assistant that helps employees understand company policies."

 The BA records:

```
# Requirement Intake

Requirement ID: REQ-001

Requirement Name:
Employee Policy Assistant

Original Request:

"Build an AI assistant that helps employees understand
company policies."

Business Problem:

Employees spend significant time searching through
multiple policy documents and frequently contact HR
for routine policy questions.

Desired Outcome:

Employees should be able to ask policy-related questions
in natural language and receive understandable answers.

Initial Users:

- Employees
- HR support staff

Potential AI Usage:

Natural-language question answering.

Known Constraint:

Responses should be based on approved company policies.

Open Questions:

- Which policy documents are authoritative?
- Should answers contain citations?
- Should the assistant remember conversations?
- Can employees ask questions about their own HR data?
- What happens when policy information cannot be found?
```

 Notice what the BA **didn't** do:

```
❌ "We'll use LangChain."
❌ "We'll use RAG."
❌ "We'll use GPT-X."
❌ "We'll create an agent."
```

 Those decisions belong later.

---

 # 5\. Artifact 02 — Stakeholder Analysis

 Before writing detailed requirements, identify everyone affected.

 ## Template

```
# LADF-003 — Stakeholder Analysis

## Stakeholder Register

| ID | Stakeholder | Role | Interest | Influence | Responsibility |
|---|---|---|---|---|---|
| ST-001 | | | | | |
| ST-002 | | | | | |

## Stakeholder Expectations

### ST-001

Expected outcome:

[Description]

Concerns:

[Description]

Approval Required:

[Yes/No]

---

## Decision Authority

Business Decision Owner:
[Name/Role]

Technical Decision Owner:
[Name/Role]

AI Decision Owner:
[Name/Role]

Security Approval:
[Name/Role]

Production Approval:
[Name/Role]
```

---

 # 6\. Artifact 03 — User Persona

 An LLM application can behave very differently depending on who is using it.

 Therefore define the persona.

 ## Template

```
# LADF-004 — User Persona

## Persona ID

PERSONA-XXX

## Persona Name

[Name]

## Role

[Role]

## Description

[Who is this user?]

## Goals

- [Goal]
- [Goal]

## Problems

- [Problem]
- [Problem]

## Typical Tasks

- [Task]
- [Task]

## Technical Skill

[Low / Medium / High]

## AI Familiarity

[Low / Medium / High]

## Expected Interaction Style

[Conversational / Formal / Concise / Detailed]

## Permissions

[What is the user allowed to access/do?]

## Restrictions

[What must the user not access/do?]
```

---

 # 7\. Artifact 04 — Use Case Specification

 This is one of the most important BA artifacts.

 A use case describes **what the user wants to accomplish**.

 Example:

```
UC-001 — Ask Policy Question
```

 ## Template

```
# LADF-005 — Use Case Specification

## Use Case ID

UC-XXX

## Use Case Name

[Name]

## Objective

[What is the user trying to accomplish?]

## Primary Actor

[Actor]

## Secondary Actors

- [Actor]

## Trigger

[What causes this use case to start?]

## Preconditions

- [Condition]

## Postconditions

- [Condition]

## Main Success Flow

1. User performs [action].
2. System receives [input].
3. System processes request.
4. System returns [result].
5. User receives expected outcome.

## Alternative Flows

### ALT-001

Condition:
[Condition]

Behavior:
[Behavior]

### ALT-002

Condition:
[Condition]

Behavior:
[Behavior]

## Exception Flows

### EX-001

Condition:
[Failure]

Expected behavior:
[Behavior]

## Business Rules

- BR-XXX
- BR-XXX

## Inputs

- [Input]

## Outputs

- [Output]

## Acceptance Criteria

- AC-XXX
- AC-XXX

## Priority

[Must / Should / Could]

## Traceability

Business Requirement:
BR-XXX
```

---

 # 8\. Example Use Case

```
# UC-001 — Ask Policy Question

Objective:

Allow an employee to ask a question about company policy.

Primary Actor:

Employee

Trigger:

Employee submits a natural-language question.

Preconditions:

- Employee is authenticated.
- Employee has access to the assistant.

Main Success Flow:

1. Employee enters a policy question.
2. System accepts the question.
3. System determines relevant company policy information.
4. System generates an understandable answer.
5. System presents the answer to the employee.
6. System identifies the supporting policy information.

Alternative Flow:

If the system cannot determine an answer from approved
policy information, it informs the employee that the
information could not be found.

Exception:

If the service is unavailable, the user receives an
appropriate service-unavailable message.

Business Rules:

- Answers must be based on approved policy information.
- The system must not present unsupported policy claims.

Expected Output:

Policy explanation and supporting source information.
```

---

 # 9\. Artifact 05 — User Story

 Use cases describe behavior.

 User stories describe requirements from the user's perspective.

 ## Template

```
# LADF-006 — User Story

## Story ID

US-XXX

## Title

[Title]

## As a

[User Persona]

## I want

[Capability]

## So that

[Business/User Value]

## Business Rules

- BR-XXX

## Acceptance Criteria

### AC-001

Given [context]

When [action]

Then [expected result]

### AC-002

Given [context]

When [action]

Then [expected result]

## Priority

Must / Should / Could

## Related Use Case

UC-XXX
```

---

 # 10\. Example

```
As an employee,

I want to ask questions about company policies
using natural language,

so that I can understand company policies without
manually searching multiple documents.
```

 Acceptance:

```
Given an authenticated employee

When the employee asks a question about an approved policy

Then the system should provide an understandable answer
based on the available policy information.
```

---

 # 11\. Artifact 06 — User Journey

 For conversational AI, this is especially useful.

 The BA should document the **interaction journey**, not the internal LLM implementation.

 ## Template

```
# LADF-007 — User Journey

## Journey ID

JOURNEY-XXX

## Persona

[Persona]

## Goal

[Goal]

## Journey

### Step 1 — Entry

User:

[What user does]

System:

[Expected system behavior]

### Step 2 — Request

User:

[Action]

System:

[Expected behavior]

### Step 3 — Response

System:

[Expected response behavior]

### Step 4 — Follow-up

User:

[Possible follow-up]

System:

[Expected behavior]

### Step 5 — Completion

[Expected end state]

---

## Pain Points

- [Pain point]

## Desired Experience

- [Expectation]

## Failure Experience

- [Expectation]
```

---

 # 12\. Artifact 07 — Business Process

 Document the business process before introducing AI.

 For example:

```
Employee
   ↓
Has Policy Question
   ↓
Searches Policy Documents
   ↓
Cannot Find Answer
   ↓
Contacts HR
   ↓
HR Searches Documents
   ↓
HR Responds
```

 The future-state process could be:

```
Employee
   ↓
Policy Question
   ↓
AI Assistant
   ↓
Policy Information
   ↓
Answer
   ↓
Employee
```

 But the BA should also identify when escalation is required:

```
AI Assistant
      ↓
Can Answer?
  ┌───┴────┐
 YES       NO
  │         │
  ↓         ↓
Answer    Escalate
            ↓
           HR
```

---

 # 13\. Artifact 08 — Functional Requirements

 This is where requirements become precise.

 Every requirement should have a unique ID.

 ## Template

```
# LADF-008 — Functional Requirements

## FR-001

### Name

[Requirement name]

### Description

The system shall [behavior].

### Rationale

[Why is this required?]

### Actor

[Actor]

### Trigger

[Trigger]

### Input

[Input]

### Processing Requirement

[Expected business behavior]

### Output

[Expected output]

### Exceptions

[Exception behavior]

### Priority

Must / Should / Could

### Acceptance Criteria

- AC-XXX
- AC-XXX

### Source

BR-XXX / UC-XXX / US-XXX
```

---

 # 14\. Example Functional Requirements

```
FR-001

Name:
Submit Policy Question

Description:
The system shall allow an authenticated employee to submit
a natural-language policy question.

Input:
Employee question

Output:
Question accepted for processing.

Priority:
Must
```

```
FR-002

Name:
Provide Policy Answer

Description:
The system shall provide an understandable response to a
policy question when sufficient approved policy information
is available.

Priority:
Must
```

```
FR-003

Name:
Handle Unknown Policy Information

Description:
The system shall clearly inform the employee when sufficient
approved policy information is not available to answer the
question.

Priority:
Must
```

---

 # 15\. Artifact 09 — Business Rules

 Business rules are extremely important for AI applications.

 A prompt instruction is **not automatically a business rule**.

 For example:

 > "Don't hallucinate."

 That's an AI behavior requirement.

 But:

 > "Employees may only view their own salary information."

 That's a business/security rule.

 ## Template

```
# LADF-009 — Business Rules

## BR-001

### Name

[Rule]

### Rule

[The business rule]

### Applies To

[Use cases / personas / processes]

### Reason

[Business justification]

### Priority

Mandatory / Conditional

### Violation Behavior

[What should happen if violated?]

### Source

[Policy / Regulation / Business Owner]
```

---

 # 16\. Example Business Rules

```
BR-001

Employees may access only information they are authorized
to view.
```

```
BR-002

Only approved company policy documents are considered
authoritative sources for policy answers.
```

```
BR-003

If the applicable policy cannot be established, the
employee must be directed to the appropriate HR process.
```

---

 # 17\. Artifact 10 — Business Data Requirements

 At the BA stage, don't define database tables yet.

 Define **business information requirements**.

 ## Template

```
# LADF-010 — Data Requirements

## Data Element

[Name]

### Business Meaning

[What does it represent?]

### Source

[Where does it come from?]

### Owner

[Business owner]

### Required

Yes / No

### Sensitivity

Public / Internal / Confidential / Restricted

### Allowed Usage

[How may it be used?]

### Retention Requirement

[Requirement]

### Accuracy Requirement

[Requirement]

### Update Frequency

[Requirement]
```

---

 # 18\. Input Requirements

 Now define what the application receives.

 Example:

```
INPUT-001

Name:
User Question

Type:
Natural Language Text

Source:
Employee

Required:
Yes

Maximum Expected Size:
Business-defined

Sensitivity:
Potentially confidential

Validation:
Must contain meaningful input.

Purpose:
Determine employee's request.
```

 Other inputs might include:

```
INPUT-002 User Identity
INPUT-003 Conversation Context
INPUT-004 Document Context
INPUT-005 User Preferences
```

 At this point, however, distinguish:

```
Business Input
System Input
AI Context
```

 Don't assume they are the same thing.

---

 # 19\. Output Requirements

 Likewise define the business expectation for output.

```
OUTPUT-001

Name:
Policy Answer

Description:
An understandable explanation of the applicable company policy.

Required:
Yes

Source Information:
Required

Fallback:
If no reliable answer can be determined, communicate
the limitation and provide the appropriate next step.
```

 Notice that we haven't yet said:

```
Pydantic
JSON
AIMessage
OutputParser
```

 Those belong to the AI/System Design stages.

---

 # 20\. Artifact 11 — Non-Functional Requirements

 The BA should capture business expectations even if the Architect later determines the technical implementation.

 Examples:

```
NFR-001 Response Time
NFR-002 Availability
NFR-003 Scalability
NFR-004 Security
NFR-005 Privacy
NFR-006 Accessibility
NFR-007 Auditability
NFR-008 Usability
NFR-009 Reliability
NFR-010 Cost
```

 ## Template

```
# LADF-011 — Non-Functional Requirements

## NFR-XXX

### Category

[Performance / Security / Availability / etc.]

### Requirement

The system shall [requirement].

### Measurement

[How will this be measured?]

### Target

[Target value]

### Priority

Must / Should / Could

### Business Rationale

[Reason]

### Acceptance Method

[Test / Measurement / Review]
```

---

 # 21\. Example NFRs

```
NFR-001

Category:
Performance

Requirement:
The application should provide an initial response within
the business-defined acceptable response time.

Measurement:
End-to-end request latency.

Target:
[Defined during architecture]
```

 Don't invent a technical number during BA if the business has not established one.

 Instead mark:

```
Target: TBD — Architecture/Performance Workshop
```

 That is much better than pretending the requirement is known.

---

 # 22\. Artifact 12 — Scope

 This is essential for preventing AI projects from becoming unlimited.

 ## Template

```
# LADF-012 — Scope

## Objective

[Overall objective]

## In Scope

- [Item]
- [Item]

## Out of Scope

- [Item]
- [Item]

## Future Scope

- [Item]

## Explicitly Prohibited

- [Item]
```

 For an AI assistant:

```
In Scope:
- Answer policy questions
- Explain policy language
- Provide supporting policy references

Out of Scope:
- Change employee records
- Approve leave
- Make HR decisions
```

 This distinction becomes very important later when designing tools and agents.

---

 # 23\. Artifact 13 — Constraints

 Constraints are conditions the solution must operate within.

 ## Template

```
# LADF-013 — Constraints

| ID | Constraint | Category | Mandatory | Source |
|---|---|---|---|---|
| CON-001 | | Regulatory | Yes | |
| CON-002 | | Security | Yes | |
| CON-003 | | Technology | | |
| CON-004 | | Budget | | |
```

 Categories:

```
Regulatory
Security
Privacy
Budget
Time
Technology
Infrastructure
Data
Organization
Vendor
Operational
```

---

 # 24\. Artifact 14 — Assumptions

 An assumption is something we currently believe to be true but haven't fully verified.

 Example:

```
ASM-001

The company has a centralized repository containing
approved policy documents.
```

 ## Template

```
# LADF-014 — Assumptions

## ASM-XXX

### Assumption

[Statement]

### Impact If False

[Impact]

### Validation Required

Yes / No

### Owner

[Role]

### Status

Open / Validated / Rejected
```

 This prevents hidden assumptions from entering architecture.

---

 # 25\. Artifact 15 — Dependencies

 Example:

```
DEP-001

Dependency:
Approved policy repository

Owner:
HR

Required By:
Policy Assistant

Impact:
Application cannot provide authoritative answers
without policy content.
```

 ## Template

```
# LADF-015 — Dependencies

| ID | Dependency | Owner | Required By | Status | Risk |
|---|---|---|---|---|---|
| DEP-001 | | | | | |
```

---

 # 26\. Artifact 16 — Acceptance Criteria

 This is one of the most important artifacts.

 The acceptance criteria must describe **observable behavior**.

 Bad:

```
The LLM should be intelligent.
```

 Good:

```
Given an employee asks a question whose answer exists
in an approved policy,

when the request is processed,

then the system should provide an answer supported by
the applicable policy information.
```

---

 ## Standard Acceptance Criteria Format

```
Given
    [initial condition]

When
    [user/system action]

Then
    [expected result]
```

 And for AI applications:

```
Given
    [input + context]

When
    [AI capability is executed]

Then
    [observable expected behavior]

And
    [constraint that must hold]
```

---

 # 27\. Example Acceptance Criteria

 ### AC-001 — Known Answer

```
Given an approved policy contains the answer,

When the employee asks the corresponding question,

Then the system should provide an answer based on
the approved policy information.
```

 ### AC-002 — Unknown Answer

```
Given no approved policy contains sufficient information,

When the employee asks the question,

Then the system should not present an unsupported answer,

And should inform the employee that sufficient information
is unavailable.
```

 ### AC-003 — Unauthorized Data

```
Given the employee does not have permission to access
specific information,

When the employee asks for that information,

Then the system must not disclose the restricted information.
```

 ### AC-004 — Follow-up

```
Given the employee previously asked a policy question,

When the employee asks a related follow-up question,

Then the system should interpret the follow-up in the context
of the previous conversation when appropriate.
```

 Notice how AC-004 gives the later architect a clue that **conversation state may be required**, without telling the architect how to implement it.

 That's exactly how the BA layer should work.

---

 # 28\. Artifact 17 — Success Metrics

 Don't confuse:

```
Application Metrics
```

 with:

```
Business Success Metrics
```

 The BA defines the latter.

 Examples:

```
Business Metric:
Reduction in routine HR inquiries

User Metric:
Employee satisfaction

Operational Business Metric:
Percentage of questions successfully resolved

Adoption Metric:
Percentage of target employees using assistant

Quality Metric:
Percentage of accepted answers
```

 ## Template

```
# LADF-017 — Business Success Metrics

## Metric ID

MET-XXX

## Name

[Metric]

## Definition

[What does it measure?]

## Baseline

[Current value]

## Target

[Desired value]

## Measurement Method

[How measured?]

## Frequency

[Daily / Weekly / Monthly]

## Owner

[Role]

## Success Threshold

[Threshold]
```

---

 # 29\. Artifact 18 — Risk Register

 AI projects require a broader risk analysis.

 ## Categories

```
Business Risk
AI Risk
Data Risk
Security Risk
Privacy Risk
Operational Risk
Cost Risk
Vendor Risk
Compliance Risk
User Experience Risk
```

 ## Template

```
# LADF-018 — Risk Register

| ID | Risk | Category | Probability | Impact | Severity | Mitigation | Owner |
|---|---|---|---|---|---|---|---|
| RSK-001 | | | | | | | |
```

 Example:

```
RSK-001

Risk:
AI may provide an incorrect policy interpretation.

Category:
AI / Business

Probability:
Medium

Impact:
High

Mitigation:
Responses must be grounded in approved policy information
and evaluated against a representative test dataset.

Owner:
AI Product Owner
```

---

 # 30\. Artifact 19 — Open Questions

 Never hide uncertainty.

 Create an explicit register.

```
# LADF-019 — Open Questions

| ID | Question | Raised By | Owner | Due Date | Impact | Status |
|---|---|---|---|---|---|---|
| Q-001 | | | | | | |
```

 Example:

```
Q-001:
Should answers contain citations?

Q-002:
What policy repository is authoritative?

Q-003:
Should the assistant support multiple languages?

Q-004:
Should conversation history be retained?

Q-005:
Should employees be allowed to perform HR actions
through the assistant?
```

 These questions eventually feed architecture decisions.

---

 # 31\. Artifact 20 — Out-of-Scope Register

 I recommend a separate explicit artifact for AI applications.

 Why?

 Because users naturally assume:

 > "If the AI can answer it, perhaps it can also do it."

 Define prohibited capabilities.

```
# LADF-020 — Out of Scope

| ID | Capability | Reason |
|---|---|---|
| OOS-001 | Approve employee leave | Not part of initial release |
| OOS-002 | Modify employee records | Security / scope |
| OOS-003 | Provide legal advice | Business restriction |
```

 This will later influence tool availability for an agent.

---

 # 32\. Artifact 21 — Requirement Traceability Matrix

 This is the **master BA artifact**.

 It connects the business requirement to everything downstream.

 At this stage:

```
Business Requirement
       ↓
Use Case
       ↓
User Story
       ↓
Functional Requirement
       ↓
Acceptance Criteria
```

 Later it will expand to:

```
BR
 ↓
SRS
 ↓
Architecture
 ↓
AI Spec
 ↓
Prompt
 ↓
Workflow
 ↓
Implementation
 ↓
Test
 ↓
Evaluation
```

 ## Template

```
# LADF-021 — Requirement Traceability Matrix

| Business ID | Use Case | User Story | Functional Req | Business Rule | Acceptance Criteria |
|---|---|---|---|---|---|
| BR-001 | UC-001 | US-001 | FR-001 | BR-001 | AC-001 |
```

---

 # 33\. The Master BRD

 Now we can assemble the artifacts into the formal **Business Requirement Document**.

 I recommend this structure:

```
BRD
│
├── 1. Document Control
├── 2. Executive Summary
├── 3. Business Problem
├── 4. Business Objective
├── 5. Current State
├── 6. Desired Future State
├── 7. Stakeholders
├── 8. Personas
├── 9. Scope
├── 10. Use Cases
├── 11. User Stories
├── 12. User Journeys
├── 13. Business Process
├── 14. Functional Requirements
├── 15. Business Rules
├── 16. Data Requirements
├── 17. Input Requirements
├── 18. Output Requirements
├── 19. Non-Functional Requirements
├── 20. Constraints
├── 21. Assumptions
├── 22. Dependencies
├── 23. Acceptance Criteria
├── 24. Success Metrics
├── 25. Risks
├── 26. Open Questions
├── 27. Out of Scope
├── 28. Traceability
├── 29. Approval
└── 30. Change History
```

---

 # 34\. Complete BRD Template

```
# LADF-002 — Business Requirements Document

# 1. Document Control

| Field | Value |
|---|---|
| Document ID | BRD-XXX |
| Project ID | PROJECT-XXX |
| Project Name | |
| Version | 1.0 |
| Status | Draft |
| Business Analyst | |
| Business Owner | |
| Product Owner | |
| Created Date | |
| Last Updated | |
| Approval Date | |

---

# 2. Executive Summary

[Brief description of the initiative.]

---

# 3. Business Problem

## 3.1 Current Problem

[Problem description.]

## 3.2 Business Impact

[Impact.]

## 3.3 Current Pain Points

-
-
-

---

# 4. Business Objective

## Primary Objective

[Objective.]

## Secondary Objectives

-
-

---

# 5. Current State

[Describe current process/system.]

---

# 6. Desired Future State

[Describe desired business outcome.]

---

# 7. Stakeholders

[Reference stakeholder artifact.]

---

# 8. User Personas

[Reference personas.]

---

# 9. Scope

## In Scope

-

## Out of Scope

-

## Future Scope

-

---

# 10. Use Cases

| ID | Name | Actor | Priority |
|---|---|---|---|
| UC-001 | | | |

---

# 11. User Stories

| ID | Story | Priority |
|---|---|---|
| US-001 | | |

---

# 12. User Journeys

[Reference journeys.]

---

# 13. Business Process

## Current Process

[Process.]

## Future Process

[Process.]

---

# 14. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-001 | | |

---

# 15. Business Rules

| ID | Rule | Priority |
|---|---|---|
| BR-001 | | |

---

# 16. Data Requirements

[Business data requirements.]

---

# 17. Input Requirements

[Business inputs.]

---

# 18. Output Requirements

[Expected outputs.]

---

# 19. Non-Functional Requirements

| ID | Category | Requirement | Priority |
|---|---|---|---|
| NFR-001 | | | |

---

# 20. Constraints

| ID | Constraint | Mandatory |
|---|---|---|
| CON-001 | | |

---

# 21. Assumptions

| ID | Assumption | Status |
|---|---|---|
| ASM-001 | | |

---

# 22. Dependencies

| ID | Dependency | Owner | Status |
|---|---|---|---|
| DEP-001 | | | |

---

# 23. Acceptance Criteria

| ID | Requirement | Acceptance Criteria |
|---|---|---|
| AC-001 | | |

---

# 24. Success Metrics

| ID | Metric | Baseline | Target |
|---|---|---|---|
| MET-001 | | | |

---

# 25. Risks

| ID | Risk | Impact | Mitigation |
|---|---|---|---|
| RSK-001 | | | |

---

# 26. Open Questions

| ID | Question | Owner | Status |
|---|---|---|---|
| Q-001 | | | |

---

# 27. Out of Scope

| ID | Capability | Reason |
|---|---|---|
| OOS-001 | | |

---

# 28. Requirement Traceability

[RTM reference.]

---

# 29. Approval

| Role | Name | Decision | Date |
|---|---|---|---|
| Business Owner | | Approved/Rejected | |
| Product Owner | | Approved/Rejected | |
| BA | | Reviewed | |

---

# 30. Change History

| Version | Date | Author | Change |
|---|---|---|---|
| 0.1 | | | Initial draft |
```

---

 # 35\. BA → Architect Handoff

 This is the **critical boundary** between Part 2 and Part 3.

 The BA should not simply send the Architect:

 > "Here is the BRD."

 The BA should provide a **Business-to-Architecture Handoff Package**.

 It should contain:

```
Business Problem
        ↓
Business Objectives
        ↓
Users
        ↓
Use Cases
        ↓
Functional Requirements
        ↓
Business Rules
        ↓
Inputs
        ↓
Outputs
        ↓
NFRs
        ↓
Constraints
        ↓
Dependencies
        ↓
Acceptance Criteria
        ↓
Success Metrics
        ↓
Risks
        ↓
Open Questions
```

 The Architect then asks:

 > **"What technical architecture can satisfy all of these?"**

---

 # 36\. BA Stage Gate

 The BA stage should not finish merely because the BRD document exists.

 It should pass:

 # **Gate 1 — Business Requirement Ready**

 ### Mandatory conditions

```
✓ Business problem clearly defined
✓ Business objective defined
✓ Stakeholders identified
✓ Personas identified
✓ Scope defined
✓ Out-of-scope defined
✓ Use cases defined
✓ Functional requirements defined
✓ Business rules defined
✓ Inputs identified
✓ Outputs identified
✓ NFR expectations captured
✓ Constraints captured
✓ Assumptions documented
✓ Dependencies documented
✓ Acceptance criteria defined
✓ Success metrics defined
✓ Risks documented
✓ Open questions documented
✓ Business owner approval obtained
```

 Then:

```
                 BA
                  │
                  ▼
              BRD PACKAGE
                  │
             Gate 1 Review
                  │
          ┌───────┴────────┐
          │                │
       Approved         Rework
          │                │
          ▼                └────→ BA
      ARCHITECT
```

---

 # 37\. The Most Important BA Rule for LLM Projects

 There is one additional rule I strongly recommend.

 ## Separate "Business Requirement" from "AI Solution"

 For example, don't write:

 > "The system shall use RAG to answer employee questions."

 That's already an architectural decision.

 Instead write:

 > "The system shall answer employee policy questions using authoritative company policy information."

 Then the Architect determines whether the appropriate solution is:

```
RAG
```

 or:

```
Database Query
```

 or:

```
API
```

 or:

```
Knowledge Graph
```

 or something else.

 Likewise:

 Don't write:

 > "The agent shall call the leave-balance tool."

 Write:

 > "The employee shall be able to obtain their current leave balance through the application, subject to authorization."

 The AI Architect later determines whether that requires a tool.

 This preserves **requirements independence from implementation technology**.

---

 # 38\. What Part 2 Produces

 At the end of Business Analysis, the Architect should receive this:

```
┌───────────────────────────────────────────┐
│        BUSINESS REQUIREMENT PACKAGE       │
├───────────────────────────────────────────┤
│                                           │
│ Business Problem                          │
│ Business Objectives                      │
│ Stakeholders                              │
│ Personas                                  │
│ Current State                             │
│ Future State                              │
│ Scope                                     │
│ Use Cases                                 │
│ User Stories                              │
│ User Journeys                             │
│ Business Process                          │
│ Functional Requirements                   │
│ Business Rules                            │
│ Data Requirements                         │
│ Input Requirements                        │
│ Output Requirements                       │
│ NFRs                                      │
│ Constraints                               │
│ Assumptions                               │
│ Dependencies                              │
│ Acceptance Criteria                       │
│ Success Metrics                           │
│ Risks                                     │
│ Open Questions                            │
│ Out of Scope                              │
│ Traceability                              │
│ Approval                                  │
│                                           │
└──────────────────────┬────────────────────┘
                       │
                       ▼
                  ARCHITECT
```

 And the key boundary is:

 > **Part 2 tells the Architect what must be achieved. It deliberately does not prescribe how LangChain/LangGraph or any other technology must achieve it.**

---

 # Part 3 — Next Layer

 The next stage should be **Part 3: SRS + System Requirements Specification**.

 There we take the approved BRD and systematically transform:

```
BRD
 │
 ├── Business Requirement
 ├── Use Case
 ├── User Story
 ├── Business Rule
 └── Acceptance Criteria
          │
          ▼
         SRS
          │
          ├── Functional System Requirements
          ├── System Inputs
          ├── System Outputs
          ├── API Requirements
          ├── Data Requirements
          ├── Integration Requirements
          ├── Security Requirements
          ├── Authorization
          ├── Error Requirements
          ├── Performance
          ├── Availability
          ├── Scalability
          ├── Auditability
          └── System Acceptance Criteria
```

 The important distinction will be:

 **BRD = business behavior and business need**

 **SRS = precise system behavior and technical requirements**

 **Architecture = technical design**

 **AI Specification = AI behavior/design**

 That separation is what will ultimately allow us to hand a developer a genuinely **development-ready LLM/Agentic implementation package**, rather than a requirement document that still contains dozens of unanswered design decisions.
