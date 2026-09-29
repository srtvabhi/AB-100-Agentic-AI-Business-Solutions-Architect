# AB-100 Module 6 — Case Study 3

# Microsoft 365 Agent Platform for Teams and SharePoint

## Scenario

Northwind Mobility has thousands of employees working in Microsoft Teams and SharePoint.

Employees spend significant time:

- searching for policies;
- summarizing project conversations;
- finding project documents;
- creating follow-up tasks;
- preparing management updates.

The organization wants a Microsoft 365 agent platform that works naturally inside Teams and uses SharePoint as a governed enterprise knowledge source.

The architecture must also support voice interactions and different reasoning requirements.

## Business Requirements

The solution must:

1. Answer employee questions using approved SharePoint content.
2. Respect existing Microsoft 365 permissions.
3. Summarize Teams conversations.
4. Retrieve project documents.
5. Create approved follow-up tasks.
6. Support different agent behaviors for different business scenarios.
7. Use standard reasoning for simple tasks.
8. Use deeper reasoning when complex analysis is required.
9. Support voice interactions for selected scenarios.
10. Provide monitoring and governance.

## Available Systems

| System | Purpose |
|---|---|
| Microsoft 365 Copilot | Employee AI experience |
| Copilot Studio | Agent design and orchestration |
| Teams | Collaboration and conversation |
| SharePoint | Enterprise knowledge |
| Microsoft Graph | Microsoft 365 context |
| Power Automate | Business actions |
| Dataverse | Structured business data |

## Architecture Challenge

The architect must design a Microsoft 365 agent that can operate across Teams and SharePoint without creating a separate uncontrolled data-access layer.

The design must also distinguish between:

- knowledge retrieval;
- conversation support;
- business actions;
- standard reasoning;
- complex reasoning;
- voice interaction.

## Proposed Architecture

```text
                         Employee
                            |
             +--------------+--------------+
             |                             |
             v                             v
           Teams                      Microsoft 365
             |                         Copilot
             |                             |
             +--------------+--------------+
                            |
                            v
                     Copilot Studio
                          Agent
                            |
            +---------------+----------------+
            |               |                |
            v               v                v
       SharePoint      Microsoft Graph   Power Automate
       Knowledge          Context          Actions
            |               |                |
            +---------------+----------------+
                            |
                            v
                    Grounded Context
                            |
                            v
                      Agent Behavior
                            |
                 +----------+----------+
                 |                     |
                 v                     v
           Standard Reasoning     Deep Reasoning
                 |                     |
                 +----------+----------+
                            |
                            v
                    Business Outcome
```

## SharePoint Knowledge Design

The agent uses SharePoint as the governed source for:

- organizational policies;
- project documentation;
- procedures;
- FAQs;
- approved operational guidance.

```text
SharePoint
 |
 +-- Policies
 +-- Procedures
 +-- Project Documents
 +-- FAQs
 +-- Lists
 +-- Pages
 |
 v
Grounding
 |
 v
Agent
 |
 v
Contextual Response
```

## Permissions

The architecture must preserve existing Microsoft 365 access boundaries.

```text
Employee Identity
       |
       v
Microsoft 365
Permissions
       |
       v
Agent
       |
       v
Allowed SharePoint Content
       |
       v
Grounded Response
```

The agent must not expose information simply because the information exists somewhere in SharePoint.

## Teams Project Assistant

The company creates a Teams project assistant.

Example request:

> "Summarize the last week's project discussion and identify the open actions."

Architecture:

```text
Teams Conversation
       |
       v
Project Agent
       |
       +--> Conversation Context
       |
       +--> SharePoint Project Documents
       |
       +--> Microsoft Graph Context
       |
       v
Reasoning
       |
       +--> Summary
       |
       +--> Open Actions
       |
       v
Power Automate
       |
       v
Create Follow-Up Tasks
```

## Standard vs Deep Reasoning

The architect uses different reasoning levels based on the workload.

### Standard Reasoning

Examples:

- summarize a document;
- answer a simple policy question;
- identify a project document;
- create a standard task.

### Deep Reasoning

Examples:

- compare several project risks;
- analyze competing options;
- identify dependencies across multiple documents;
- reason through complex business constraints.

```text
User Request
      |
      v
Agent
      |
      v
Complexity Assessment
      |
   +--+--+
   |     |
 Simple Complex
   |     |
   v     v
Standard Deep
Reasoning Reasoning
   |     |
   +--+--+
      |
      v
Business Result
```

## Voice Interaction

Northwind also wants a voice-based service assistant.

The voice experience should avoid long responses.

```text
Employee Voice
      |
      v
Interpret Request
      |
      v
Retrieve Context
      |
      v
Reason
      |
      v
Confirm Important Action
      |
      v
Execute
      |
      v
Short Spoken Response
```

Example:

> "Create a follow-up task for the project owner."

The agent should confirm important action details before execution when appropriate.

## Agent Behavior

The agent's behavior is defined through:

```text
Purpose
   +
Scope
   +
Instructions
   +
Knowledge
   +
Tools
   +
Policies
   +
Escalation Rules
```

Example:

```text
Project Agent
 |
 +-- Purpose: Project support
 |
 +-- Knowledge: Approved project content
 |
 +-- Tools: Task creation
 |
 +-- Scope: Current project
 |
 +-- Policy: Respect permissions
 |
 +-- Escalation: Uncertain or restricted request
```

## Governance

The platform should include:

- version control;
- content review;
- monitoring;
- usage measurement;
- permission validation;
- agent lifecycle management.

## Architecture Questions

### Question 1

Why use SharePoint as the primary knowledge source?

**Expected Answer:**  
SharePoint already contains governed enterprise content such as policies, procedures, and project documents. Using the existing source reduces duplication and allows the agent to work with controlled enterprise information.

### Question 2

Why are permissions important?

**Expected Answer:**  
The agent must respect the user's existing access boundaries. The existence of a document does not mean every employee should receive its content.

### Question 3

When should standard reasoning be used?

**Expected Answer:**  
For simpler workloads such as straightforward questions, summaries, and routine tasks where complex multi-step reasoning isn't required.

### Question 4

When might deeper reasoning be appropriate?

**Expected Answer:**  
For complex multi-step analysis, competing options, dependencies, business rules, and scenarios requiring more extensive reasoning.

### Question 5

What changes when an agent is voice-based?

**Expected Answer:**  
The interaction should be concise and conversational, support clarification and interruption, and use confirmation before important actions when appropriate.

### Question 6

Why use Power Automate?

**Expected Answer:**  
Power Automate provides a controlled action/workflow layer for executing approved business processes such as creating tasks or sending notifications.

## Key Architectural Decisions

| Requirement | Architectural Decision |
|---|---|
| Enterprise knowledge | SharePoint |
| Microsoft 365 context | Microsoft Graph |
| Agent orchestration | Copilot Studio |
| Collaboration | Teams |
| Business action | Power Automate |
| Simple workload | Standard reasoning |
| Complex workload | Deep reasoning |
| Voice | Voice-optimized interaction |
| Security | Existing Microsoft 365 permissions |
| Governance | Monitoring + lifecycle management |

## Final Architecture

```text
                         Employee
                            |
                 +----------+----------+
                 |                     |
                 v                     v
               Teams          Microsoft 365 Copilot
                 |                     |
                 +----------+----------+
                            |
                            v
                     Copilot Studio
                            |
            +---------------+----------------+
            |               |                |
            v               v                v
       SharePoint      Microsoft Graph   Power Automate
       Knowledge          Context          Actions
            |               |                |
            +---------------+----------------+
                            |
                            v
                    Grounded Context
                            |
                            v
                     Agent Behavior
                            |
                 +----------+----------+
                 |                     |
                 v                     v
          Standard Reasoning      Deep Reasoning
                 |                     |
                 +----------+----------+
                            |
                            v
                  Teams / Voice / User
                            |
                            v
                     Business Outcome
```

## Summary

This case demonstrates how to build a Microsoft 365-centered agent platform using:

- Microsoft 365 Copilot;
- Copilot Studio;
- Teams;
- SharePoint;
- Microsoft Graph;
- Power Automate;
- standard and deeper reasoning;
- voice interaction;
- permissions;
- governance.

The key architectural principle is:

> Use existing Microsoft 365 data, identity, permissions, and collaboration experiences as part of the agent architecture instead of creating a disconnected AI platform.
