# AB-100 Module 6 — Case Study 1

# Enterprise AI Agent Extension for Legacy Procurement

## Scenario

Contoso Manufacturing operates procurement teams across North America, Europe, and Asia-Pacific.

The company already uses Microsoft 365 Copilot and Copilot Studio. Procurement employees need an AI agent that can prepare supplier information, retrieve approved procurement policies, and perform repetitive tasks in a legacy supplier portal.

The supplier portal does not provide a supported API or connector.

The architecture team must design an extensible solution without giving the agent unrestricted access to business systems.

## Business Requirements

The solution must:

1. Help procurement users understand supplier information.
2. Retrieve approved procurement policies from SharePoint.
3. Retrieve supplier and purchase information from approved business systems.
4. Perform a repetitive task in the legacy supplier portal.
5. Validate the result of UI automation.
6. Create a follow-up task when required.
7. Respect Microsoft 365 and enterprise permissions.
8. Keep business actions auditable.
9. Escalate when the agent cannot safely complete the task.
10. Avoid using Computer Use when a reliable API or connector is available.

## Available Systems

| System | Purpose | Integration |
|---|---|---|
| Microsoft 365 Copilot | Employee experience | Native |
| Copilot Studio | Agent orchestration | Native |
| SharePoint | Procurement policies and procedures | Knowledge |
| Dataverse | Supplier and procurement data | Connector |
| Power Automate | Business workflow | Action |
| Legacy Supplier Portal | Supplier invoice lookup | UI only |
| Microsoft Teams | Collaboration and notifications | Microsoft 365 |

## Architecture Challenge

The architect must decide:

- which capabilities belong in the agent;
- which information should come from SharePoint;
- when to use connectors and APIs;
- when Computer Use is justified;
- how to validate UI actions;
- where human approval is required.

## Proposed Architecture

```text
                         Procurement User
                                |
                                v
                    Microsoft 365 Copilot
                                |
                                v
                       Copilot Studio Agent
                                |
              +-----------------+------------------+
              |                 |                  |
              v                 v                  v
         SharePoint          Dataverse        Power Automate
         Knowledge           Supplier Data       Actions
              |                 |                  |
              +-----------------+------------------+
                                |
                                v
                       Agent Reasoning
                                |
                   +------------+-------------+
                   |                          |
             API/Connector               Computer Use
                   |                          |
                   v                          v
          Enterprise Systems          Legacy Supplier Portal
                                              |
                                              v
                                      Result Validation
                                              |
                                              v
                                      Human Escalation
```

## Agent Responsibilities

### Knowledge

The agent can retrieve:

- procurement policies;
- supplier procedures;
- approved purchasing guidance;
- escalation procedures.

SharePoint is the authoritative knowledge source for these documents.

### Business Data

Supplier and procurement records come from approved enterprise data sources.

The agent should not create a duplicate supplier database simply to support AI.

### Actions

Power Automate can perform approved workflow actions such as:

- create a procurement task;
- notify a procurement team;
- update an approved record.

### Computer Use

Computer Use is used only for the legacy supplier portal because no supported API or connector is available.

Example task:

```text
User Request
     |
     v
Agent
     |
     v
Legacy Supplier Portal
     |
     +--> Sign in
     +--> Search supplier
     +--> Find invoice
     +--> Read status
     |
     v
Validate Result
     |
     +--> Success → Return result
     |
     +--> Failure → Escalate
```

## Reliability Controls

Because UI automation can fail when the portal changes, the architecture includes:

- validation after important actions;
- retry limits;
- failure handling;
- audit logging;
- restricted website scope;
- human escalation.

## Architecture Questions

### Question 1

Why is Computer Use appropriate for the supplier portal?

**Expected Answer:**  
The portal does not provide a supported API or connector, and the task is a structured, repetitive UI workflow. Computer Use provides an integration path through the existing user interface.

### Question 2

Should Computer Use be used for every enterprise integration?

**Expected Answer:**  
No. APIs and supported connectors should normally be preferred because they are more stable and easier to govern. Computer Use is appropriate when a suitable API or connector is unavailable.

### Question 3

Where should procurement policies be maintained?

**Expected Answer:**  
Approved procurement policies should remain in a governed enterprise knowledge source such as SharePoint. The agent should retrieve the authoritative content rather than maintaining an uncontrolled duplicate.

### Question 4

What happens if the supplier portal changes its user interface?

**Expected Answer:**  
The automation should detect failures through validation and error handling, stop unsafe actions, and escalate or use a supported fallback process.

### Question 5

Why use Power Automate for business actions?

**Expected Answer:**  
Power Automate provides a controlled workflow/action layer for approved business operations rather than placing all business-process logic inside the agent.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| Procurement knowledge | SharePoint |
| Supplier data | Enterprise data source |
| Workflow action | Power Automate |
| Legacy UI | Computer Use |
| UI reliability | Validation + error handling |
| Security | Existing identity and permissions |
| High-risk failure | Human escalation |

## Final Architecture

```text
User
 |
 v
Microsoft 365 Copilot
 |
 v
Copilot Studio Agent
 |
 +--> SharePoint Knowledge
 |
 +--> Enterprise Supplier Data
 |
 +--> Power Automate
 |       |
 |       +--> Approved Business Actions
 |
 +--> Computer Use
         |
         v
   Legacy Supplier Portal
         |
         v
   Validate Result
         |
         +--> Success → Business Outcome
         |
         +--> Failure → Human Review
```

## Summary

This case demonstrates how an architect can combine:

- Microsoft 365 Copilot;
- Copilot Studio;
- SharePoint knowledge;
- enterprise data;
- Power Automate;
- Computer Use;
- validation;
- human escalation.

The important architectural principle is to **use the most reliable integration mechanism available and reserve Computer Use for UI-based scenarios where a suitable API or connector is unavailable**.
