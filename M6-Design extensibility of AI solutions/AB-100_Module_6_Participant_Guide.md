# AB-100 Module 6 — Design Extensibility of AI Solutions

## Module Overview

Module 6 focuses on designing extensible AI solutions. The main architectural goal is to select the appropriate extension mechanism for a business requirement without adding unnecessary complexity.

The module covers:

1. Introduction
2. Design AI solutions with custom models in Microsoft Foundry
3. Design agents in Microsoft 365 Copilot
4. Design agent extensibility in Copilot Studio
5. Design agent extensibility with Model Context Protocol (MCP)
6. Design agents to automate tasks in apps and websites with Computer Use
7. Design agent behaviors in Copilot Studio
8. Optimize solution design for agents in Microsoft 365, Teams, and SharePoint

---

# 1. Introduction

## Concept

Module 6 is about making AI solutions extensible.

A basic AI solution might answer questions or summarize information. An extensible AI solution can go further:

- use custom models;
- connect to enterprise systems;
- perform business actions;
- use Microsoft 365 data;
- work across Teams and SharePoint;
- interact with applications and websites;
- use Model Context Protocol (MCP);
- support specialized reasoning;
- operate through voice.

The central architectural idea is:

> Start with a business capability, then choose the smallest extensibility mechanism that provides the required capability.

## Architecture

```text
                    Business Requirement
                           |
                           v
                 +---------------------+
                 |   AI Solution       |
                 +---------------------+
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
   Custom Model       Agent Extension    Microsoft 365
   Foundry            Copilot Studio     Teams/SharePoint
          |                |                |
          +----------------+----------------+
                           |
                           v
                 Enterprise Systems
                           |
                           v
                 Secure Business Outcome
```

## Key Components

| Component | Purpose |
|---|---|
| Microsoft Foundry | Custom model development and operationalization |
| Microsoft 365 Copilot | Agents embedded into Microsoft 365 experiences |
| Copilot Studio | Extend agents with instructions, skills, actions, integrations |
| MCP | Standardized context and system interaction |
| Computer Use | UI-based automation where APIs/connectors aren't available |
| Teams | Conversational and collaborative agent experience |
| SharePoint | Enterprise knowledge and site context |

## Example

A company already uses Microsoft 365 Copilot but wants an agent that:

1. reads project documents;
2. checks a legacy procurement portal;
3. retrieves supplier information;
4. creates a procurement task.

A simple Copilot configuration isn't enough.

```text
Microsoft 365 Copilot
        |
        v
Copilot Studio Agent
        |
        +---- SharePoint knowledge
        |
        +---- Business system connector
        |
        +---- Computer Use for legacy portal
        |
        v
Procurement workflow
```

## Key Takeaway

Extensibility means extending an AI solution only where the business requirement requires it.

---

# 2. Design AI Solutions with Custom Models in Microsoft Foundry

## Concept

A standard foundation model isn't always enough.

Microsoft Foundry supports organizations that need to build, fine-tune, evaluate, deploy, and operate custom AI models.

A custom model becomes relevant when the organization needs things such as:

- highly specialized domain language;
- high-impact decision support;
- strict data sovereignty;
- unique workflows;
- personalization;
- high-volume inference cost optimization.

### Easy way to remember

> Standard model = general capability  
> Custom model = specialized capability

## Architecture

```text
                 Enterprise Data
                       |
                       v
              +------------------+
              | Data Preparation |
              +------------------+
                       |
                       v
              +------------------+
              | Model Development|
              | / Fine-Tuning    |
              +------------------+
                       |
                       v
              +------------------+
              | Evaluation       |
              +------------------+
                       |
                       v
              +------------------+
              | Deployment       |
              +------------------+
                       |
                       v
              +------------------+
              | Monitoring       |
              +------------------+
                       |
                       v
              Business Applications
```

## Key Components

### Model Catalog

Provides base models that can be fine-tuned or adapted for specialized workloads.

### Training and Fine-Tuning

Used when the model needs to behave differently for a particular domain or task.

### Evaluation

Evaluate:

- accuracy;
- safety;
- bias;
- latency;
- scalability;
- business value.

### Deployment

The model must be deployed into an architecture where applications and agents can consume it.

### Monitoring

Monitor:

- model drift;
- performance degradation;
- latency;
- unexpected outputs;
- user friction.

### Lifecycle Management

Use:

- model versions;
- approval processes;
- deployment automation;
- rollback strategies.

## Example

A manufacturing company needs an AI model that understands highly specialized engineering terminology.

```text
Engineering Documents
        |
        v
   Data Preparation
        |
        v
   Domain Dataset
        |
        v
 Microsoft Foundry
        |
   Fine-Tuning
        |
        v
 Custom Model
        |
        +------> Evaluation
        |
        +------> Safety Testing
        |
        +------> Performance Testing
        |
        v
 Enterprise Agent
        |
        v
 Engineering Application
```

## Key Takeaway

Choose a custom model when domain specificity, compliance, performance, workflow requirements, or cost optimization justify the additional complexity.

## Architecture Questions

1. Does the workload actually require a custom model?
2. Is the training data allowed to be used?
3. How will the model be evaluated?
4. How will model versions be managed?
5. How will model drift be detected?
6. What happens if the new model performs worse than the previous version?

---

# 3. Design Agents in Microsoft 365 Copilot

## Concept

A Microsoft 365 Copilot agent is an instruction-driven AI component designed for a specific business task or workflow.

Agents can:

- automate tasks;
- retrieve information;
- summarize information;
- perform multi-step operations;
- collaborate with other agents or systems.

They can operate within:

- Microsoft Teams;
- Outlook;
- Loop;
- SharePoint;
- custom line-of-business applications through extensibility.

The important architecture concept is:

> Don't start with "What can the agent do?" Start with "What business task should the agent own?"

## Architecture

```text
                 User
                   |
                   v
          Microsoft 365 Copilot
                   |
                   v
            +-------------+
            |    Agent    |
            +-------------+
             /     |      \
            /      |       \
           v       v        v
      Microsoft   Graph   Connectors
      365 Data
           \       |       /
            \      |      /
             v     v     v
             Business Context
                    |
                    v
             Business Action
```

## Key Components

### 1. Business Problem

Define:

- task;
- business goal;
- decisions;
- systems involved.

### 2. Agent Behavior

Define:

- role;
- allowed capabilities;
- prohibited capabilities;
- guardrails;
- escalation conditions.

### 3. Data and Tools

Agents can use:

- Microsoft Graph;
- SharePoint;
- OneDrive;
- Teams;
- connectors;
- APIs.

### 4. Collaboration

Common collaboration patterns include:

```text
Sequential:
Agent A → Agent B → Human Review

Parallel:
Agent A ─┐
Agent B ─┼→ Combined Result
Agent C ─┘

Delegation:
Primary Agent
      |
      +--> Research Agent
      |
      +--> Workflow Agent
      |
      +--> Communication Agent
```

## Agent Builder

Typical flow:

```text
Define Purpose
      ↓
Add Instructions
      ↓
Add Guardrails
      ↓
Connect Data
      ↓
Configure Actions
      ↓
Test
      ↓
Publish
      ↓
Monitor
```

## Example

A sales organization wants an opportunity-preparation agent.

```text
Sales User
    |
    v
Microsoft 365 Copilot
    |
    v
Opportunity Preparation Agent
    |
    +---- CRM opportunity data
    |
    +---- Customer documents
    |
    +---- Previous communications
    |
    +---- Product information
    |
    v
Opportunity Summary
    |
    v
Recommended Preparation Actions
```

## Key Takeaway

A good Microsoft 365 Copilot agent has a clear purpose, controlled access, defined behavior, appropriate tools, and lifecycle management.

## Architecture Questions

- What single business problem does the agent solve?
- What data can it access?
- What actions can it perform?
- What actions are prohibited?
- When should it involve a person?
- Does it need another specialized agent?

---

# 4. Design Extensible Agents in Microsoft Copilot Studio

## Concept

Copilot Studio provides several layers for extending an agent.

Important areas include:

1. Instruction-level extensibility
2. Skill and capability extensibility
3. Integration extensibility
4. Pro-code extensibility

Think about these as increasing levels of customization.

## Architecture

```text
                  Copilot Studio Agent
                           |
        +------------------+------------------+
        |                  |                  |
        v                  v                  v
 Instructions          Skills            Integrations
        |                  |                  |
        |             Retrieval          Connectors
        |             Actions             APIs
        |             Workflows           Power Automate
        |                  |                  |
        +------------------+------------------+
                           |
                           v
                    Pro-Code Layer
                    Visual Studio Code
                           |
                           v
                  Enterprise Systems
```

## Key Components

### Instruction-Level Extensibility

Controls:

- purpose;
- role;
- constraints;
- action patterns;
- escalation rules.

### Skill and Capability Extensibility

Adds capabilities such as:

- enterprise retrieval;
- actions;
- custom APIs;
- multi-step workflows.

### Integration Extensibility

Allows the agent to interact with:

- Dynamics 365;
- Microsoft 365;
- databases;
- line-of-business applications;
- Power Automate;
- external APIs.

### Pro-Code Extensibility

Useful when the solution needs:

- custom logic;
- reusable components;
- code-based tools;
- custom transformations;
- custom orchestration;
- source control.

## Architectural Patterns

### Modular Agent

```text
Agent
 ├── Instructions
 ├── Knowledge
 ├── Skills
 ├── Actions
 └── Integrations
```

### Multi-Agent

```text
                 Main Agent
                     |
        +------------+------------+
        |            |            |
        v            v            v
   Research      Workflow     Communication
     Agent         Agent          Agent
```

### Domain Context

```text
Agent
  |
  +-- Domain terminology
  +-- Business rules
  +-- Security policies
  +-- Expected outcomes
```

## Example

A finance agent needs to:

- retrieve customer information;
- check credit data;
- calculate a value;
- update a business system.

Rather than putting all logic into one large agent:

```text
Finance Agent
    |
    +--> Retrieval Skill
    |
    +--> Calculation Tool
    |
    +--> Business API
    |
    +--> Approval Workflow
```

## Key Takeaway

Use modular extensibility instead of creating one agent with every possible capability.

## Architecture Questions

- Can the capability be implemented with instructions?
- Does the agent need a new skill?
- Is a connector or API required?
- Is Power Automate appropriate?
- Does the solution justify pro-code development?
- Can the capability be reused by another agent?

---

# 5. Design Extensible Agents Using MCP in Copilot Studio

## Concept

Model Context Protocol (MCP) provides a structured contract for how an agent accesses and interprets context.

The module particularly emphasizes MCP with Dynamics 365 Finance & Operations.

MCP can expose structured business information such as:

- customers;
- vendors;
- products;
- workflows;
- status values;
- approval chains;
- financial dimensions;
- ledger models;
- localization rules;
- taxonomies.

### Easy explanation

Without structured context:

```text
Agent → "I need information about this business process."
```

With MCP:

```text
Agent
  |
  v
 MCP
  |
  +--> Business entities
  +--> Relationships
  +--> Metadata
  +--> Business processes
  +--> Domain models
  |
  v
Reliable business context
```

## Architecture

```text
                 Copilot Studio Agent
                          |
                          v
                         MCP
                          |
       +------------------+------------------+
       |                  |                  |
       v                  v                  v
   Customers           Vendors            Products
       |                  |                  |
       +------------------+------------------+
                          |
                          v
                 Business Process Context
                          |
                          v
                    Agent Reasoning
                          |
                          v
                   Business Action
```

## Key Components

### Purpose Statement

Why does the agent exist?

### Role Definition

What perspective should the agent use?

### Behavior Rules

What must and must not happen?

### Context Consumption

Which MCP data should the agent use?

### Action Boundaries

Which operations are allowed?

## MCP Patterns

### Context-Driven Reasoning

The agent retrieves current business context before reasoning.

Useful for:

- compliance;
- finance;
- procurement;
- vendor management.

### Workflow-Integrated Agent

```text
Business Event
      ↓
Agent
      ↓
MCP Context
      ↓
Business Rule
      ↓
Approval / Escalation
      ↓
Workflow
```

### Multi-Agent Collaboration

```text
HR Agent
    |
    v
   MCP
    |
    +---- Finance Context
    |
    +---- Supply Chain Context
    |
    +---- HR Context
```

## Security

MCP architecture should include:

- identity-based access;
- least privilege;
- context boundaries;
- logging;
- responsible instructions;
- clear business and IT ownership.

## Key Takeaway

Think of MCP as a standardized contract for business context.

## Architecture Questions

- What context does the agent actually need?
- Is that context structured?
- Who is allowed to access it?
- How are business rules represented?
- Are agent actions logged?
- Can multiple agents use the same context consistently?

---

# 6. Design Agents to Automate Tasks in Apps and Websites with Computer Use

## Concept

Computer Use allows an agent to interact with applications and websites using the user interface.

It can:

- click;
- type;
- scroll;
- navigate;
- read screen content;
- perform multi-step UI tasks;
- work across applications.

The important distinction is:

> Computer Use is especially useful when an API or connector isn't available.

Suitable scenarios include:

- legacy systems;
- vendor portals;
- desktop applications;
- repetitive UI workflows;
- multi-application UI tasks.

## Architecture

```text
                  User Request
                       |
                       v
                Copilot Studio
                       |
                       v
                 Agent Reasoning
                       |
                       v
                 Computer Use
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Website      Desktop App   Legacy App
          |            |            |
          +------------+------------+
                       |
                       v
                 Result Validation
                       |
                       v
                     User
```

## How Computer Use Works

```text
User Request
     ↓
Understand Request
     ↓
Analyze UI
     ↓
Create Plan
     ↓
Perform UI Actions
     ↓
Validate Result
     ↓
Report Result
```

## When to Use It

```text
No API
   +
Repetitive UI task
   +
Structured workflow
   =
Computer Use candidate
```

Example:

> Download the latest invoice from a vendor portal and save it to SharePoint.

```text
Agent
  |
  v
Vendor Portal
  |
  +--> Login
  +--> Navigate
  +--> Find Invoice
  +--> Download
  |
  v
SharePoint
```

## Constraints

The agent should have defined:

- allowed applications;
- allowed websites;
- allowed data;
- prohibited actions;
- retry limits;
- time limits.

## Reliability

Computer Use is more fragile than a stable API integration because UI layouts can change.

Therefore:

```text
Computer Use
     |
     +--> Monitoring
     |
     +--> Validation
     |
     +--> Error Handling
     |
     +--> Fallback
     |
     +--> Audit Logging
```

## Key Takeaway

Prefer APIs and connectors when available. Use Computer Use when UI automation is the practical integration path.

## Architecture Questions

- Is an API available?
- Is a connector available?
- Is the UI workflow stable enough?
- What actions should be prohibited?
- What happens when the UI changes?
- How will failed actions be detected?
- How will actions be audited?

---

# 7. Design Agent Behaviors in Copilot Studio

## Concept

An agent's behavior isn't controlled by instructions alone.

Four major behavioral components are:

1. Instructions
2. Knowledge
3. Actions and tools
4. Policies and constraints

Think of it as:

```text
Instructions → What should I do?
Knowledge    → What should I know?
Tools        → What can I do?
Policies     → What am I allowed to do?
```

## Architecture

```text
                 Agent Behavior
                       |
       +---------------+---------------+
       |               |               |
       v               v               v
 Instructions       Knowledge       Tools/Actions
       |               |               |
       +---------------+---------------+
                       |
                       v
              Policies & Constraints
                       |
                       v
                Agent Response
```

## Instruction Structure

Define:

### Purpose

Why does the agent exist?

### Scope

What can it and can't it do?

### Tone and Style

How should it communicate?

### Data Boundaries

Which sources are allowed?

### Quality Expectations

What does a good answer look like?

### Error Handling

What should happen when the agent is unsure?

### Escalation

When should a human become involved?

## Reasoning Modes

### Standard Reasoning

Appropriate for:

- conversation;
- summaries;
- simple calculations;
- basic workflow assistance.

It is designed for fast responses and lower compute usage.

### Deep Reasoning

Useful for:

- multi-step tasks;
- complex business rules;
- analytical processes;
- decision trees;
- scenario planning;
- constraints and trade-offs.

Deep reasoning is identified as preview in the source material.

```text
                 User Request
                      |
                      v
                 Agent
                      |
              Is reasoning
                complex?
                /       \
              No         Yes
              |           |
              v           v
          Standard     Deep Reasoning
          Reasoning      (preview)
              |           |
              +-----+-----+
                    |
                    v
               Agent Result
```

## Voice Mode

Voice agents require different interaction design.

```text
User speaks
     ↓
Interpret intent
     ↓
Confirm / clarify
     ↓
Execute action
     ↓
Short spoken response
```

For important actions, use confirmation:

```text
Recommendation
      |
      v
Confirmation
      |
      v
Action
```

## Example

A field technician says:

> "Show me the service history for this machine and tell me what I should check next."

```text
Voice
  |
  v
Intent
  |
  v
Service History
  |
  v
Knowledge + Business Data
  |
  v
Reasoning
  |
  v
Recommendation
  |
  v
Short Voice Response
```

## Key Takeaway

Agent behavior is an architectural combination of instructions + knowledge + tools + policies.

## Architecture Questions

- What is the agent's role?
- What is outside its scope?
- Which knowledge sources are authoritative?
- Which actions are allowed?
- When is standard reasoning sufficient?
- When is deep reasoning justified?
- Does voice require confirmation before actions?

---

# 8. Optimize Solution Design for Agents in Microsoft 365

## Concept

Copilot Studio agents can operate with:

- Microsoft Teams;
- SharePoint;
- Microsoft Graph;
- Microsoft 365 data.

Agents can answer questions in Teams, summarize conversations, retrieve SharePoint content, trigger workflows, and use Microsoft 365 grounding.

## Architecture

```text
                       User
                        |
             +----------+----------+
             |                     |
             v                     v
           Teams              SharePoint
             |                     |
             +----------+----------+
                        |
                        v
                Microsoft 365 Agent
                        |
             +----------+----------+
             |                     |
             v                     v
      Microsoft Graph       SharePoint Content
             |                     |
             +----------+----------+
                        |
                        v
                  Grounded Context
                        |
                        v
                 Agent Reasoning
                        |
             +----------+----------+
             |                     |
             v                     v
       Answer / Summary       Business Action
```

## SharePoint as Knowledge

Agents can use:

- site pages;
- document libraries;
- lists;
- news posts;
- policies;
- procedures;
- wiki content.

```text
SharePoint Site
      |
      +-- Pages
      +-- Libraries
      +-- Lists
      +-- Policies
      +-- Metadata
      |
      v
SharePoint Agent
      |
      v
Contextual Answer
```

## Teams Agents

Teams agents can:

- answer questions;
- summarize conversations;
- provide recommendations;
- trigger workflows;
- support group collaboration;
- create tasks.

```text
Teams Message
     |
     v
Agent
     |
     +--> Understand message
     |
     +--> Retrieve SharePoint document
     |
     +--> Summarize
     |
     +--> Create task
     |
     v
Team
```

## Microsoft 365 Grounding

A critical concept is permissions.

Microsoft 365 agents should respect user permissions and existing SharePoint/Teams security boundaries.

```text
User
 |
 | Identity
 v
Agent
 |
 v
Microsoft 365 Permissions
 |
 +---- Allowed Content
 |
 +---- Restricted Content
 |
 v
Grounded Response
```

The agent should not become a shortcut around existing security.

## Optimization Areas

### Grounding

Use structured, well-tagged enterprise content.

### Permissions

Respect user access boundaries.

### Prompt and Behavior

Design concise, contextual responses.

### Governance

Use:

- version control;
- monitoring;
- content review;
- AI Center of Excellence governance.

## Common Solution Patterns

### SharePoint Knowledge Assistant

```text
User
 ↓
Agent
 ↓
SharePoint
 ↓
Answer / Summary
```

### Teams Project Assistant

```text
Teams
 ↓
Agent
 ├── Channel summary
 ├── SharePoint documents
 └── Task creation
```

### Organizational Policy Assistant

```text
Employee
 ↓
Agent
 ↓
SharePoint Policies
 ↓
Grounded Answer
```

### Site Owner Support Agent

```text
Site Owner
 ↓
Agent
 ↓
SharePoint
 ├── Draft content
 ├── Metadata suggestions
 ├── Accessibility
 └── Site improvements
```

## Key Takeaway

A Microsoft 365 agent should use Microsoft 365 grounding and existing permissions rather than creating a separate uncontrolled data-access layer.

## Architecture Questions

- What should be grounded in SharePoint?
- What should come from Microsoft Graph?
- Does the user already have permission to the information?
- What should the agent do inside Teams?
- What should the agent do inside SharePoint?
- How will content freshness be maintained?
- How will agent versions be governed?

---

# Module 6 — Complete Architecture

```text
                         BUSINESS REQUIREMENT
                                  |
                                  v
                     +-------------------------+
                     |   AI Solution Design    |
                     +-------------------------+
                                  |
              +-------------------+-------------------+
              |                   |                   |
              v                   v                   v
       Custom Model         Microsoft 365       Copilot Studio
       Microsoft Foundry       Copilot               Agent
              |                   |                   |
              |                   |          +--------+--------+
              |                   |          |        |        |
              |                   |          v        v        v
              |                   |      Skills   Actions    MCP
              |                   |          |        |        |
              |                   |          +--------+--------+
              |                   |                   |
              +-------------------+-------------------+
                                  |
                     +------------+-------------+
                     |                          |
                     v                          v
                Enterprise Data          Enterprise Systems
                     |                          |
                     |                    +-----+------+
                     |                    |            |
                     |                    v            v
                     |                APIs/Connectors Computer Use
                     |                                 |
                     |                                 v
                     |                         Legacy / Web Apps
                     |
                     v
              SharePoint / Graph
                     |
                     v
             Grounded Enterprise
                  Context
                     |
                     v
              Agent Reasoning
                     |
            +--------+---------+
            |                  |
            v                  v
       Standard           Deep Reasoning
       Reasoning             Preview
            |                  |
            +--------+---------+
                     |
                     v
              Business Outcome
                     |
                     v
              Monitoring / Governance
```

# Module 6 — Architecture Decision Model

## Decision 1 — Do I need a custom model?

```text
Specialized domain?
High-impact requirement?
Strict governance?
Unique model behavior?
High-volume inference?

        ↓ YES

Microsoft Foundry custom model
```

## Decision 2 — Do I need an agent?

```text
Business task
      ↓
Needs reasoning + knowledge + actions?
      |
     YES
      ↓
Agent
```

## Decision 3 — How much extensibility?

```text
Simple behavior
      ↓
Instructions

Need knowledge/action
      ↓
Skills

Need enterprise integration
      ↓
Connectors / APIs / Actions

Complex custom behavior
      ↓
Pro-code
```

## Decision 4 — Does the agent need structured business context?

```text
Structured enterprise context?
          |
         YES
          ↓
         MCP
```

## Decision 5 — How should the agent interact with an application?

```text
API available?
   |
   +---- YES ---> API / Connector
   |
   +---- NO ----> Computer Use
```

## Decision 6 — How much reasoning is required?

```text
Simple conversation
Simple workflow
Simple summary
        |
        v
Standard reasoning


Complex multi-step task
Complex rules
Analysis
Trade-offs
        |
        v
Deep reasoning
```

## Decision 7 — Where should the agent operate?

```text
Microsoft 365 users
        |
   +----+----+
   |         |
 Teams   SharePoint
   |         |
   +----+----+
        |
        v
Microsoft 365 Agent
```

# Module 6 — Key Concepts to Remember

| Concept | Remember it as |
|---|---|
| Custom model | Specialized AI capability |
| Microsoft Foundry | Build, evaluate, deploy, monitor custom models |
| Microsoft 365 Copilot Agent | Business-focused agent inside Microsoft 365 |
| Copilot Studio | Extend agents with instructions, skills, integrations and actions |
| MCP | Structured contract for business context |
| Computer Use | UI automation when API/connector isn't available |
| Standard reasoning | Fast, simpler workloads |
| Deep reasoning | Complex multi-step reasoning; preview in the source |
| Voice | Short, confirmed, interruption-aware interaction |
| SharePoint grounding | Enterprise knowledge |
| Microsoft Graph | Microsoft 365 context/retrieval |
| Permissions | Agent should respect user access |
| Modular architecture | Reusable instructions, skills, tools and integrations |
| Multi-agent | Specialized agents with clear responsibility boundaries |

# Module 6 — What You Should Be Able to Design

By the end of this module, you should be able to look at a business requirement and describe an architecture like:

```text
Business Requirement
        |
        v
Choose AI Capability
        |
        +--> Standard AI
        |
        +--> Custom Model
        |
        +--> Microsoft 365 Agent
        |
        +--> Copilot Studio Agent
        |
        +--> MCP Extension
        |
        +--> Computer Use
        |
        +--> Voice
        |
        v
Enterprise Data + Tools
        |
        v
Security + Permissions
        |
        v
Reasoning + Behavior
        |
        v
Business Action
        |
        v
Monitoring + Governance
```

The main AB-100 architectural skill in this module is choosing the appropriate extension point without unnecessarily increasing solution complexity.
