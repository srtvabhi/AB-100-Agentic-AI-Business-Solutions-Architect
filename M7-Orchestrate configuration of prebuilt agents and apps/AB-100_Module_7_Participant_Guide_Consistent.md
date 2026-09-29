# AB-100 Module 7 — Orchestrate Configuration of Prebuilt Agents and Apps

## Module Overview

Module 7 focuses on orchestrating AI across Dynamics 365 Finance & Supply Chain, Dynamics 365 Customer Service, Microsoft 365 Copilot, Power Platform, and interoperable Finance and Operations agents.

The main architecture theme is:

> **Choose the right AI experience → connect the right business data → provide the right knowledge → enable the right actions → enforce security → measure the outcome.**

---

# 1. Introduction

## Concept

Microsoft approaches AI from an enterprise solution architecture perspective.

An organization may have:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain
- Dynamics 365 Customer Service
- Microsoft 365
- Power Platform
- Copilot Studio
- Business-specific data and knowledge

The architect's job is to make these capabilities work together rather than creating disconnected AI solutions.

AI can appear as:

- conversational assistants
- embedded intelligence
- automated agents

The architecture must also account for security, governance, compliance, extensibility, and business outcomes.

## Architecture

```text
                    BUSINESS USER
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
     Conversational   Embedded       Automated
        Copilot          AI            Agent
          │              │              │
          └──────────────┼──────────────┘
                         ▼
              Business Applications
                         │
        ┌────────────────┼────────────────┐
        ▼                ▼                ▼
    Dynamics 365     Microsoft 365    Power Platform
        │                │                │
        └────────────────┼────────────────┘
                         ▼
                Governed Enterprise Data
```

## Key Components

- Dynamics 365 applications
- Microsoft 365
- Power Platform
- Copilot experiences
- Business data
- Enterprise knowledge
- Security and governance

## Example

A business may use Dynamics 365 for customer and financial processes, Microsoft 365 for collaboration, and Power Platform for workflow automation. An AI solution can connect these capabilities so users receive contextual assistance without creating separate disconnected solutions.

## Key Takeaway

**Module 7 is about orchestration, not just configuration.**

## Architecture Questions

1. Where should AI appear in the user's workflow?
2. Is the AI conversational, embedded, or autonomous?
3. Which business application owns the process?
4. What data and knowledge does the AI need?
5. What governance is required?

---

# 2. Orchestrate AI Features in Dynamics 365 Apps for Finance and Supply Chain

## Concept

Dynamics 365 Finance and Supply Chain can use AI through several interaction patterns.

### Sidecar

Copilot appears beside the Finance or Supply Chain application.

Users can:

- ask questions
- get explanations
- summarize workflows
- query business data
- invoke actions

Example:

> "Summarize the approval history for this purchase order."

The architecture must ensure business vocabulary, role-based access, and standardized entity metadata.

### Embedded

AI appears directly inside the business workspace.

Examples:

- purchase order change analysis
- customer collections summaries
- demand planning insights
- supplier communication drafting

The important idea is **context**. The AI should understand what record, page, or workflow the user is currently working with.

### External Orchestration

An external agent works across applications.

```text
Teams
  │
  ▼
AI Agent
  │
  ├── Dynamics 365 Finance
  │
  ├── Dynamics 365 Supply Chain
  │
  ├── Power Automate
  │
  └── Notifications
```

External orchestration is useful when the process crosses applications or needs broader workflow coordination.

## Architecture

```text
                   User
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
       Sidecar   Embedded   External
       Copilot      AI       Agent
          │         │         │
          └─────────┼─────────┘
                    ▼
           Dynamics 365 F&O
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
    Finance      Supply Chain   Procurement
                    │
                    ▼
              Governed APIs
                    │
                    ▼
             Power Automate
```

## Key Components

- Dynamics 365 Finance
- Dynamics 365 Supply Chain
- Embedded AI
- Copilot
- External agents
- APIs and connectors
- Power Automate
- Role-based security

## Example

A procurement manager asks an agent to explain why a purchase order is delayed.

The agent can:

1. Read the purchase order.
2. Retrieve supplier information.
3. Check related workflow status.
4. Review relevant supply-chain data.
5. Summarize the reason.
6. Suggest an action.

## Key Takeaway

Use **embedded AI** when intelligence belongs directly inside an existing business workflow.

Use **external orchestration** when the process crosses applications or requires broader workflow coordination.

## Architecture Questions

1. Should the AI be embedded or external?
2. Which system is the system of record?
3. Does the AI need read-only access or action permissions?
4. Which workflows require Power Automate?
5. How should access be enforced?

---

# 3. Design AI Solutions for Dynamics 365 Apps for Customer Experience and Service

## Concept

Dynamics 365 Customer Service provides AI capabilities across:

1. Agent Hub
2. Autonomous service agents
3. Copilot in Contact Center

### Agent Hub

Agent Hub provides a central place for administrators and supervisors to adopt and monitor autonomous AI agents.

### Autonomous Service Agents

Examples include:

- Customer Intent Agent
- Case Management Agent
- Customer Knowledge Management Agent
- Quality Evaluation Agent

The Case Management Agent can automate parts of the case lifecycle such as creating, updating, resolving, and closing cases.

### Copilot in Contact Center

Copilot can assist service representatives with:

- asking questions
- composing email
- summarizing cases
- summarizing conversations

## Architecture

```text
Customer
   │
   ▼
Case / Conversation
   │
   ▼
AI Orchestration
   │
   ├── Case history
   ├── Customer data
   ├── Knowledge
   ├── SLA
   └── Conversation
   │
   ▼
Suggested Action
   │
   ▼
Human Agent
   │
   ▼
Resolution
```

## Key Components

- Customer Service
- Agent Hub
- Autonomous service agents
- Cases
- Customer records
- Conversations
- Knowledge articles
- SLA information
- Copilot
- Human review

## Example

A customer opens a support case.

The AI can:

1. Identify the customer.
2. Read the case history.
3. Retrieve relevant knowledge.
4. Summarize the problem.
5. Suggest a response.
6. Recommend next steps.
7. Allow the service representative to review before sending.

## Key Takeaway

AI recommendations must respect:

- CRM data quality
- security
- privacy
- service policies
- approved workflows

## Architecture Questions

1. What information should the service agent see?
2. Which actions can be autonomous?
3. Which actions require human approval?
4. What knowledge source should ground the response?
5. How should customer data be protected?

---

# 4. Propose Microsoft 365 Agents for Business Scenarios

## Concept

A Microsoft 365 agent is a task-oriented AI assistant that can retrieve information, reason over it, and take actions across Microsoft 365 data and applications.

Treat an agent like a **product**, not just a prompt.

An agent needs:

- mission
- scope
- success criteria
- knowledge
- tools
- identity
- authorization
- guardrails
- telemetry
- lifecycle management

## Architecture

```text
                  Microsoft 365 Agent
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
       Knowledge       Tools          Actions
          │              │              │
     SharePoint       Connectors    Power Automate
     Files            APIs          Business Apps
     Email            Apps
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                  Agent Reasoning
                         │
                         ▼
                  Guardrails / RBAC
                         │
                         ▼
                  Business Outcome
```

## Key Components

- Microsoft 365 Copilot
- Microsoft 365 data
- SharePoint
- Files and documents
- Connectors
- APIs
- Power Automate
- Business applications
- Identity and permissions
- Guardrails
- Telemetry

## Example

An executive briefing agent can:

1. Retrieve approved business documents.
2. Collect relevant Microsoft 365 information.
3. Summarize key developments.
4. Identify risks or changes.
5. Produce a structured briefing.
6. Apply access controls and business rules.

## Key Takeaway

Start with the **business outcome**, then determine whether an agent is appropriate.

## Architecture Questions

1. What job is the agent responsible for?
2. What knowledge does it need?
3. What tools and actions are required?
4. What permissions should it have?
5. What should always require human approval?
6. How will success be measured?

---

# 5. Orchestrate and Configure Microsoft 365 Copilot for Sales and Service

## Concept

This topic connects Microsoft 365, Dynamics 365, and Power Platform.

### Sales

Copilot for Sales can use:

- CRM records
- email
- meetings
- documents
- opportunity information
- account information
- contact information
- activities

The architecture requires synchronized CRM data, standardized fields, correctly labeled documents, and appropriate seller permissions.

### Service

Copilot for Service can be grounded on:

- cases
- customer records
- interaction transcripts
- knowledge articles
- troubleshooting steps
- SLA information
- escalation paths
- agent notes
- historical interactions

## Architecture

```text
Email / Meetings / Documents
          │
          ▼
    Microsoft 365 Copilot
          │
          ▼
       CRM Context
          │
          ├── Account
          ├── Contact
          ├── Opportunity
          └── Activities
          │
          ▼
    Generated Insight
          │
          ▼
     Seller / Service Review
          │
          ▼
     CRM / Customer Outcome
```

## Key Components

- Microsoft 365 Copilot
- Copilot for Sales
- Copilot for Service
- Dynamics 365 CRM
- Email
- Meetings
- Documents
- Cases
- Knowledge articles
- Power Automate
- Connectors
- DLP
- RBAC
- Audit

## Example

A seller receives an inbound customer email.

The solution can:

1. Summarize the email.
2. Find the related CRM opportunity.
3. Retrieve account and contact context.
4. Draft a response or proposal content.
5. Let the seller review it.
6. Update the CRM after approval.

## Power Platform Connection

Power Platform can provide:

- CRM connectors
- approvals
- notifications
- escalation
- pre-processing
- post-processing
- Power Automate workflows

AI Builder can support classification, extraction, prediction, and multi-step workflows.

## Governance

```text
Sensitivity Labels
        +
DLP
        +
RBAC
        +
Audit
        +
Data Residency
        +
Human Review
        +
Telemetry
```

## Key Takeaway

Microsoft 365 Copilot becomes more valuable when it is grounded in authoritative business context and connected to governed business workflows.

## Architecture Questions

1. What CRM context is required?
2. Which information comes from Microsoft 365?
3. Which information comes from Dynamics 365?
4. Which actions require Power Automate?
5. Where is human review required?
6. How are DLP and permissions enforced?

---

# 6. Propose Microsoft Power Platform AI Features and AI Hub

## Concept

The key skill is selecting the correct Power Platform AI capability for the requirement.

### AI Hub

AI Hub provides a centralized Power Platform experience for managing, discovering, and orchestrating AI capabilities.

### AI Builder

AI Builder is useful for:

- document processing
- object detection
- classification
- sentiment analysis
- payment detection
- invoice and receipt extraction
- prediction
- entity extraction

### Copilot in Power Apps

Can help with:

- generating screens
- creating Dataverse tables and fields
- generating sample data
- adding logic
- UI modernization

### Copilot in Power Automate

Can:

- generate flows from business intent
- suggest triggers
- suggest actions
- suggest connectors
- explain workflow logic

### Copilot in Power Pages

Can help generate:

- pages
- forms
- data models
- automation

### Copilot Studio

Use Copilot Studio when a custom conversational agent requires:

- multi-turn reasoning
- external data
- APIs
- connectors
- Microsoft 365, Teams, or web deployment
- enterprise security and DLP

## Architecture

```text
                    AI Hub
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
  Power Apps    Power Automate   Copilot Studio
       │              │              │
       └──────────────┼──────────────┘
                      ▼
              Governed AI Platform
```

## Key Components

- AI Hub
- AI Builder
- Power Apps
- Power Automate
- Power Pages
- Copilot Studio
- Dataverse
- Connectors
- DLP
- Environment governance

## Example

A business receives invoices by email.

A Power Platform solution can:

1. Receive the invoice.
2. Use AI Builder to extract invoice information.
3. Validate required fields.
4. Store the structured information.
5. Trigger a Power Automate workflow.
6. Route exceptions for human review.

## Model Lifecycle

```text
Data
 ↓
Label
 ↓
Train
 ↓
Validate
 ↓
Deploy
 ↓
Monitor
 ↓
Retrain / Retire
```

Monitoring should include model drift and accuracy, with defined retraining or retirement triggers.

## Feature Selection

| Requirement | Primary Capability |
|---|---|
| Text generation | Copilot |
| Prediction | AI Builder |
| Document extraction | AI Builder |
| Conversational agent | Copilot Studio |
| Automation creation | Copilot / Power Automate |
| Central AI governance/orchestration | AI Hub |

## Key Takeaway

Choose the Power Platform AI capability based on the business requirement instead of starting with a product.

## Architecture Questions

1. Is the requirement generation, prediction, extraction, conversation, or automation?
2. Does the solution need an agent?
3. Does it need custom data?
4. Does it need workflow automation?
5. What governance is required?

---

# 7. Design Interoperability for Finance and Operations Agent Chats and Sources

## Concept

Finance and Operations contains important business data, but F&O may not contain everything an agent needs.

For example:

```text
Question:
"What is the vendor's current credit limit?"
             ↓
        F&O Data

Question:
"What is the vendor's latest compliance certificate?"
             ↓
        SharePoint

Question:
"Update the vendor's payment terms."
             ↓
       Plugin Action
```

## Architecture

```text
                       User
                        │
                        ▼
                   F&O Copilot
                        │
                  Intent Detection
                        │
       ┌────────────────┼────────────────┐
       ▼                ▼                ▼
   F&O Data        Knowledge Source    Plugin
       │                │                │
       │           SharePoint            │
       │           Policies              │
       │           Vendor Docs           │
       │                                 │
       └────────────────┼────────────────┘
                        ▼
                Grounded Response
                        │
                        ▼
                 Optional Action
                        │
                        ▼
                  F&O / Workflow
```

## Key Components

- Finance and Operations
- F&O Copilot
- Knowledge sources
- SharePoint
- Plugins
- Connectors
- Business workflows
- Security roles
- Logging and audit

## Example

A procurement user asks:

> "Show the vendor's current credit information and tell me whether the compliance certificate is current."

The agent can:

1. Retrieve vendor information from F&O.
2. Retrieve the compliance document from an approved knowledge source.
3. Compare the information.
4. Produce a grounded response.
5. Invoke an action only if the user has permission and the action is allowed.

## What Plugins Can Do

Plugins can:

- retrieve data
- perform actions
- trigger workflows
- integrate external systems
- enforce business logic
- return structured responses
- support multi-step workflows

## Architecture Decision Questions

1. What is missing from F&O?
2. Where does that information live?
3. Is it read-only or an action?
4. What business rules apply?
5. What validation is required?
6. What permissions are required?

## Governance

Plugins must respect:

- F&O security roles
- external source permissions
- sensitive-data restrictions
- logging requirements
- responsible AI requirements

## Key Takeaway

Use interoperability when the agent needs trusted information or actions outside the core Finance and Operations data boundary.

## Architecture Questions

1. Which source owns each required piece of information?
2. Should the source be read-only or actionable?
3. What permissions should the agent inherit?
4. How are plugin actions validated?
5. How are actions audited?

---

# 8. Process Knowledge Sources for Dynamics 365 Finance and Supply Chain Management

## Concept

This topic is about grounding Copilot with controlled business knowledge.

Good knowledge sources include:

- validated PDF documents
- RTF/Word files
- knowledge articles
- task guides
- Finance procedures
- Supply Chain procedures

## Architecture

```text
1. Prepare Knowledge
        ↓
2. Add Knowledge in Copilot Studio
        ↓
3. Test Knowledge Behavior
        ↓
4. Publish
        ↓
5. Govern + Maintain
```

## Key Components

- Knowledge documents
- Knowledge articles
- Task guides
- Copilot Studio
- Finance procedures
- Supply Chain procedures
- Security labels
- DLP
- Version control
- Knowledge lifecycle

## Example

A finance team wants an agent to answer questions about an internal payment procedure.

The team can:

1. Validate the procedure document.
2. Standardize terminology.
3. Apply appropriate sensitivity labels.
4. Add the document as agent knowledge.
5. Test realistic questions.
6. Publish the agent after validation.
7. Review the source when the business process changes.

## Knowledge Processing

### Prepare

Before ingestion:

- validate accuracy
- ensure connection to Finance/Supply Chain tasks
- standardize terminology
- apply sensitivity labels

### Ingest

```text
Environment
    ↓
Agent
    ↓
Knowledge
    ↓
Add Knowledge
    ↓
Upload Files
    ↓
Wait for Ready
```

### Test

Check:

- Does the answer come from the intended source?
- Is unrelated knowledge affecting the answer?
- Does the answer reflect the actual process?
- Does the source need correction?

### Publish

After successful testing, publish the knowledge.

Refreshed knowledge may require existing Copilot sessions to be reopened before the updated behavior becomes active.

### Govern

Maintain:

- version control
- security labels
- DLP
- review cadence
- testing after Dynamics 365 release waves

## General Knowledge Decision

### Enable broader general knowledge when:

- broader natural-language explanation provides value
- risks are understood and mitigated

### Restrict general knowledge when:

- precision is critical
- regulatory or financial workflows are involved
- only controlled knowledge should influence the answer

## Knowledge Architecture

```text
             Business User
                  │
                  ▼
              Copilot
                  │
                  ▼
          Knowledge Retrieval
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     SOPs      Task Guides   Articles
       │          │          │
       └──────────┼──────────┘
                  ▼
           Grounded Answer
                  │
                  ▼
             User Action
                  │
                  ▼
          Feedback / Review
                  │
                  ▼
          Knowledge Lifecycle
```

## Key Takeaway

Knowledge quality, scope, security, freshness, and governance directly affect the quality of AI responses.

## Architecture Questions

1. Which sources are authoritative?
2. Should general knowledge be allowed?
3. How often should knowledge be reviewed?
4. How are sensitive documents protected?
5. How will knowledge changes be tested?

---

# Module 7 — Complete Architecture

```text
                         BUSINESS OUTCOME
                                │
                                ▼
                    ┌─────────────────────┐
                    │  AI EXPERIENCE      │
                    │                     │
                    │ Dynamics 365        │
                    │ Microsoft 365       │
                    │ Power Platform      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ DATA + KNOWLEDGE    │
                    │                     │
                    │ F&O                 │
                    │ Dynamics 365        │
                    │ Dataverse           │
                    │ SharePoint          │
                    │ Documents           │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ ORCHESTRATION       │
                    │                     │
                    │ Agents              │
                    │ Plugins             │
                    │ Connectors           │
                    │ Power Automate       │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ GOVERNANCE          │
                    │                     │
                    │ Identity            │
                    │ RBAC                │
                    │ DLP                 │
                    │ Audit               │
                    │ Human Review        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ MEASURED OUTCOME    │
                    └─────────────────────┘
```

---

# Module 7 — Architecture Decision Model

## Decision 1 — Where should the AI experience run?

```text
Inside Dynamics 365?
        ↓
Embedded / Sidecar AI

Across Microsoft 365?
        ↓
Microsoft 365 Agent / Copilot

Across business systems?
        ↓
External Agent + Connectors / Plugins

Document prediction/extraction?
        ↓
AI Builder
```

## Decision 2 — What business application owns the process?

Identify the system of record.

Examples:

- Finance → Dynamics 365 Finance
- Supply Chain → Dynamics 365 Supply Chain
- Customer Service → Dynamics 365 Customer Service
- Collaboration → Microsoft 365
- Workflow → Power Platform

## Decision 3 — What knowledge and data are required?

Prefer authoritative sources:

```text
Dynamics 365
Dataverse
SharePoint
Approved documents
Knowledge articles
Business systems
```

Do not assume that general LLM knowledge is sufficient for a controlled business process.

## Decision 4 — Does the agent need actions or plugins?

If it only answers:

```text
Knowledge → Retrieval → Response
```

If it needs to change something:

```text
Knowledge
    ↓
Reasoning
    ↓
Business Rule
    ↓
Plugin / Connector / Flow
    ↓
Validation
    ↓
Action
    ↓
Audit
```

## Decision 5 — Does the solution cross business systems?

If yes, think interoperability.

```text
F&O
 │
 ├── SharePoint
 │
 ├── CRM
 │
 ├── Procurement
 │
 ├── Power Automate
 │
 └── External APIs
```

Plugins, connectors, APIs, and Power Automate become architectural components.

## Decision 6 — How controlled should the knowledge be?

For normal productivity:

```text
Controlled Knowledge
        +
General Knowledge
```

may be appropriate.

For regulated financial or business processes:

```text
Controlled + Validated Knowledge
                 │
                 ▼
           Restricted Scope
```

is more appropriate.

## Decision 7 — What governance is required?

Consider:

- identity
- role-based access
- DLP
- sensitivity labels
- audit
- human review
- data residency
- telemetry
- knowledge lifecycle
- model lifecycle

---

# Module 7 — Key Concepts to Remember

1. **Orchestration** connects AI capabilities to business workflows.
2. **Embedded AI** is useful when intelligence belongs inside an existing application workflow.
3. **Microsoft 365 agents** should be designed around a defined business job.
4. **Dynamics 365 Customer Service AI** can support both human representatives and autonomous service processes.
5. **Power Platform AI** should be selected according to the type of requirement.
6. **AI Builder** is useful for prediction, extraction, classification, and other focused AI capabilities.
7. **Plugins and connectors** enable interoperability between agents and business systems.
8. **Grounding** connects agents to authoritative business knowledge.
9. **Knowledge governance** includes accuracy, security, freshness, testing, and lifecycle management.
10. **Security and governance** are part of the architecture, not an afterthought.

---

# Module 7 — What You Should Be Able to Design

After completing this module, you should be able to design an architecture that:

- selects an appropriate AI experience for a business scenario
- uses Dynamics 365 AI capabilities appropriately
- proposes Microsoft 365 agents for business tasks
- connects Microsoft 365 Copilot with Dynamics 365 Sales and Service
- selects Power Platform AI capabilities
- uses AI Builder for focused AI workloads
- connects Finance and Operations agents to external knowledge and actions
- designs plugin and connector interoperability
- processes and governs enterprise knowledge sources
- applies permissions and security controls
- separates read-only knowledge retrieval from business actions
- includes human review where required
- defines monitoring, audit, and lifecycle requirements
- measures the resulting business outcome
