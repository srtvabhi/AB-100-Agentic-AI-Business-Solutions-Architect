# AB-100 Module 5 — Case Study 1
# Global Customer Service Agent with Dynamics 365 and Copilot Studio

## Scenario

Contoso Industrial Systems operates customer support in North America, Europe, and Asia-Pacific.

The company uses:

- Dynamics 365 Customer Service
- Dynamics 365 Sales
- Dynamics 365 Contact Center
- Dataverse
- SharePoint
- Microsoft Copilot Studio
- Power Platform

Customer-service employees currently move between multiple systems to understand a customer issue.

## Business Requirement

Contoso wants an AI customer-service experience that can:

1. Understand customer questions from chat and digital messaging.
2. Retrieve approved product and troubleshooting information.
3. Summarize the customer's case history.
4. Use Contoso business terminology consistently.
5. Collect information required for a support case.
6. Create or update a case when the required information is available.
7. Escalate high-priority cases through an approved business process.
8. Provide fallback behavior when the request is outside the configured knowledge.

## Current Customer-Service Context

A typical customer interaction contains:

```text
Customer Identity
Case History
Current Conversation
Product
Error Code
Priority
Assigned Team
Previous Actions
Customer Preferences
```

The Contact Center environment supports voice, live chat, and digital messaging.

## Knowledge Sources

The current knowledge environment contains:

```text
SharePoint
│
├── Product Manuals
├── Troubleshooting Guides
├── Warranty Policies
└── Customer-Service FAQ

Dataverse
│
├── Customers
├── Cases
├── Products
├── Priority
└── Resolution Status
```

## Business Terminology

| Term | Definition |
|---|---|
| Escalation | Case requiring priority handling due to business impact |
| Resolution Status | Current state of the customer issue |
| Warranty Request | Request to validate warranty coverage |
| Priority | Service handling priority |

## Agent Requirements

### Task Agent

The agent must collect:

- Customer
- Product
- Serial number
- Error code
- Problem description

before creating a support case.

### Prompt-Driven Agent

The agent must answer:

```text
What should I check when the controller reports F101?
```

using approved product and troubleshooting knowledge.

### Autonomous Behavior

The business wants a scheduled process to identify open high-priority cases that have not been updated according to the service process.

The process must not close cases or make customer-impacting decisions automatically.

## Architecture Challenge

Design the solution using:

- Dynamics 365 Customer Service
- Dynamics 365 Contact Center
- Copilot Studio
- SharePoint knowledge
- Dataverse
- Agent topics
- Agent flows
- Prompt actions
- Responsible AI controls

## Architecture

```text
Customer
   |
   v
Contact Center
Voice / Chat / Messaging
   |
   v
Copilot Studio Agent
   |
   +-------------------+
   |                   |
   v                   v
Customer Context     Knowledge
   |                   |
Dynamics 365       SharePoint /
Customer Service   Dataverse
   |                   |
   +---------+---------+
             |
             v
      Agent Intelligence
             |
       +-----+------+
       |            |
       v            v
   Information    Action
   Retrieval      Agent Flow
       |            |
       |            v
       |       Dynamics 365
       |       Case Update
       |            |
       +------+-----+
              |
              v
        Human Review
              |
              v
        Business Outcome
```

## Architecture Questions

**Q1. Where should enterprise product knowledge be maintained?**

**Expected answer:** Use authoritative governed knowledge sources such as SharePoint and Dataverse, selected according to the information requirement, freshness, access, and governance.

**Q2. Why use a task agent for case creation?**

**Expected answer:** Case creation is a specific business task with defined inputs, actions, rules, and a controlled outcome.

**Q3. What should happen when the customer asks a question outside the configured knowledge?**

**Expected answer:** Use a defined fallback path instead of inventing an answer.

**Q4. Should an autonomous agent automatically close high-priority customer cases?**

**Expected answer:** Not under this scenario. The business requirement defines monitoring and identification, while customer-impacting decisions require appropriate human control.

**Q5. Where should the business action execute?**

**Expected answer:** Through an approved action or agent flow connected to the business system rather than by allowing unrestricted model-generated actions.

## Key Decision

The solution combines prompt-driven interaction, task execution, enterprise grounding, Contact Center context, Dynamics 365 business data, and controlled actions.

---

# Case Study 1 Architecture Summary

```text
Customer
   ↓
Contact Center
   ↓
AI Agent
   ↓
+-----------------------------+
| Knowledge | Context | Tools |
+-----------------------------+
   ↓
Grounded Response / Task
   ↓
Dynamics 365 / Dataverse
   ↓
Human Oversight
   ↓
Customer-Service Outcome
```
