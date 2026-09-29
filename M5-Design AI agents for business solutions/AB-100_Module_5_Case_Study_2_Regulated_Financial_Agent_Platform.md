# AB-100 Module 5 — Case Study 2
# Regulated Financial Services Agent Platform

## Scenario

Fabrikam Financial Services operates across multiple regions.

The organization wants to introduce AI agents for employees who work with:

- Customer onboarding
- Financial documents
- Internal policies
- Service requests
- Compliance processes

The organization has strict requirements for data access, security, responsible AI, and human oversight.

## Business Requirement

Fabrikam wants three agent capabilities.

### Capability 1 — Employee Policy Agent

Employees ask questions such as:

```text
What documents are required for this onboarding process?
```

The answer must come from approved internal policy sources.

### Capability 2 — Document Task Agent

An employee submits a customer document.

The agent should:

1. Identify required information.
2. Summarize the document.
3. Identify missing information.
4. Prepare a structured result.
5. Send the result to the appropriate business workflow.

The agent must not make the final compliance decision.

### Capability 3 — Autonomous Monitoring Agent

The organization wants an agent to identify incomplete onboarding records based on defined system events.

The agent may:

- Retrieve the record.
- Identify missing information.
- Create a task.
- Notify the responsible employee.

The agent may not approve or reject the customer independently.

## Data Environment

```text
Dataverse
   |
   +-- Customer Records
   +-- Onboarding Records
   +-- Case Data

SharePoint
   |
   +-- Approved Policies
   +-- Procedures
   +-- Compliance Guidance

Business Systems
   |
   +-- Document Service
   +-- Notification Service
```

## Responsible AI Requirements

The solution must address:

- Fairness
- Reliability and safety
- Privacy and security
- Inclusiveness
- Transparency
- Accountability

## Data and Access Requirements

The architecture must ensure:

1. Users only access information permitted by their identity.
2. The agent does not expose documents outside the user's authorized scope.
3. Knowledge sources have defined ownership.
4. Sensitive information is not unnecessarily included in prompts or responses.
5. Business actions have explicit rules.
6. Human review exists for high-impact decisions.

## Agent Design

### Policy Agent

Use a prompt-driven experience with enterprise knowledge.

### Document Agent

Use a task-oriented design with:

```text
Goal
Skills
Knowledge
Actions
Context
Rules
```

### Autonomous Agent

Use a system event as the trigger.

```text
Onboarding Record Updated
          |
          v
Autonomous Agent
          |
          v
Check Required Information
          |
     +----+----+
     |         |
 Complete    Missing
     |         |
     |         v
     |    Create Task
     |         |
     |         v
     |      Notify User
     |
     v
Continue Business Process
```

## Custom Connector Requirement

Fabrikam uses an external document service.

The connector must expose:

```text
GET /documents/{documentId}
```

Example:

```text
GET /documents/DOC1001
```

Example response:

```json
{
  "documentId": "DOC1001",
  "documentType": "Customer Onboarding",
  "status": "Received",
  "region": "EU",
  "owner": "Onboarding Team"
}
```

Authentication must use the organization's supported identity and connector security model.

## Architecture Challenge

Design the solution so that:

- Policy knowledge is grounded.
- Document processing is task-oriented.
- Autonomous monitoring is bounded.
- External document data is accessed through a connector.
- High-impact decisions remain controlled.
- Access permissions are preserved.
- Agent behavior can be tested and monitored.

## Architecture

```text
                         Fabrikam Employee
                                |
                                v
                         Copilot / Agent
                                |
              +-----------------+-----------------+
              |                 |                 |
              v                 v                 v
        Policy Agent       Document Agent   Autonomous Agent
              |                 |                 |
              v                 v                 v
         SharePoint         Connector       System Event
         Knowledge          / Business          |
              |              Systems            v
              |                 |          Record Check
              +-----------------+                 |
                        |                          v
                        v                    Task / Notify
                 Grounded Context
                        |
                        v
               Rules + Permissions
                        |
                        v
                  Human Review
                        |
                        v
                 Business Process
```

## Architecture Questions

**Q1. Why should the policy agent use approved enterprise knowledge?**

**Expected answer:** Policy responses require authoritative, governed information with appropriate freshness and access controls.

**Q2. Why should the document agent not make the final compliance decision?**

**Expected answer:** The scenario defines the AI as a processing and preparation capability; the final high-impact business decision requires appropriate human oversight.

**Q3. Why use a custom connector?**

**Expected answer:** The document service is an external business system that needs a controlled integration and defined action/data contract.

**Q4. What should trigger the autonomous agent?**

**Expected answer:** A defined system event such as an onboarding record update, rather than unrestricted autonomous behavior.

**Q5. What Responsible AI controls are important?**

**Expected answer:** Access control, privacy and security, reliability and safety, transparency, accountability, defined action boundaries, and human oversight.

## Key Decision

The solution separates knowledge retrieval, task execution, autonomous monitoring, and high-impact decision authority.

---

# Case Study 2 Architecture Summary

```text
Business Requirement
        |
        v
Agent Pattern
        |
  +-----+------+----------------+
  |            |                |
Policy       Task          Autonomous
Agent        Agent           Agent
  |            |                |
Knowledge    Tools         System Events
  |            |                |
  +------------+----------------+
               |
               v
        Security + Rules
               |
               v
          Human Oversight
               |
               v
        Business Outcome
```
