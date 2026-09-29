# AB-100 Module 5 — Design AI Agents for Business Solutions

## Module Overview

This module focuses on designing AI agents for business solutions using Microsoft Copilot, Microsoft Copilot Studio, Dynamics 365, Microsoft Power Platform, and Microsoft Foundry.

The module covers responsible AI, Dynamics 365 customization and integration, task and autonomous agents, prompt-driven agents, grounding, Power Apps, agent flows, prompt actions, and success criteria.

---

## 1. Introduction

### Concept

AI agents are designed around business needs. The solution can combine Dynamics 365, Microsoft Copilot, Copilot Studio, Power Platform, and other Microsoft services.

The design starts with the business requirement and then identifies the appropriate agent type, data, actions, integrations, and controls.

### Architecture

```text
Business Requirement
        |
        v
   AI Use Case
        |
        v
+----------------------+
| Agent Experience     |
| Copilot / Agent      |
+----------+-----------+
           |
     +-----+-----+
     |           |
     v           v
 Knowledge     Actions
     |           |
     v           v
Dataverse /   Connectors /
SharePoint    Dynamics 365 /
              Power Platform
           |
           v
     Business Outcome
```

### Key Components

- Business requirement
- AI agent
- Microsoft Copilot
- Copilot Studio
- Dynamics 365
- Power Platform
- Business knowledge
- Actions and integrations

### Example

A customer service solution can use an AI agent to summarize a case, retrieve relevant knowledge, and help an agent respond to the customer.

---

## 2. Define Core Tenets of Responsible AI Guidelines

### Concept

Responsible AI is part of the agent design. Microsoft identifies six core principles:

1. Fairness
2. Reliability and safety
3. Privacy and security
4. Inclusiveness
5. Transparency
6. Accountability

These principles influence how data, models, prompts, outputs, access, and human oversight are designed.

### Architecture

```text
                 AI Solution
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
   Data Access    AI Behavior   User Experience
       |             |             |
       +-------------+-------------+
                     |
                     v
              Responsible AI
                     |
   +--------+--------+--------+--------+
   |        |        |        |        |
Fairness Reliability Privacy Inclusiveness
          & Safety   & Security
   |
Transparency
   |
Accountability
```

### Key Components

- Fairness
- Reliability and safety
- Privacy and security
- Inclusiveness
- Transparency
- Accountability
- Human oversight
- Appropriate data access

### Example

A service agent that provides customer recommendations should use appropriate data access and should have controls for reviewing important outputs.

---

## 3. Design Business Terms for Copilot in Dynamics 365 Customer Service

### Concept

Business terms give Copilot the vocabulary used by the organization.

Business terminology can be represented through Dataverse fields, option sets, and classification metadata. Customer Service summaries can include information such as the customer issue, actions taken, pending items, next steps, and resolution status.

### Architecture

```text
Organization Vocabulary
          |
          v
+-----------------------+
| Dataverse Definitions |
| Fields / Option Sets  |
| Classification Data   |
+-----------+-----------+
            |
            v
 Dynamics 365 Customer Service
            |
            v
          Copilot
            |
            v
   Consistent Business Language
```

### Key Components

- Business terminology
- Dataverse
- Fields
- Option sets
- Classification metadata
- Customer Service
- Copilot summaries

### Example

An organization may use a specific term for a customer escalation. Defining that terminology in the business data model helps Copilot work with the organization's vocabulary.

---

## 4. Design Customizations for Copilot in Dynamics 365 Apps

### Concept

Copilot can be customized around business terminology, prompt and output behavior, data scope, and where the Copilot experience appears.

Customization should reflect real business workflows and should keep the data available to the AI within the required scope.

### Architecture

```text
Business Workflow
       |
       v
Customization Requirements
       |
 +-----+------+------+
 |            |      |
 v            v      v
Terminology  Prompts Data Scope
 |            |      |
 +------------+------+
              |
              v
       Dynamics 365 Copilot
              |
              v
        Business Output
              |
              v
       Human Review / Use
```

### Key Components

- Business terminology
- Prompts
- Output behavior
- Data scope
- Copilot location
- Human review
- Workflow context

### Example

A Customer Service Copilot experience can be customized to use the organization's terminology and provide responses based on the data required for that service workflow.

---

## 5. Design Connectors for Copilot in Dynamics 365 Sales

### Concept

Connectors allow Copilot and Power Platform solutions to interact with external or organizational services.

Custom connectors can expose APIs and actions. Authentication can use Microsoft Entra ID with OAuth 2.0. Connector actions can then be used by Copilot Studio and Power Platform solutions.

### Architecture

```text
Dynamics 365 Sales
        |
        v
   Copilot / Agent
        |
        v
 Custom Connector
        |
        v
 Microsoft Entra ID
     OAuth 2.0
        |
        v
 External / Business API
        |
        v
      Result
```

### Key Components

- Custom connector
- API
- Microsoft Entra ID
- OAuth 2.0
- Connector actions
- Copilot Studio
- Power Apps / Power Automate

### Example

A Sales agent can use a custom connector to retrieve information from an external business system while maintaining authenticated access.

---

## 6. Design AI Agents for Dynamics 365 Contact Center

### Concept

Dynamics 365 Contact Center can connect AI experiences with customer service channels such as voice, live chat, and digital messaging.

The agent can use customer and interaction context such as identity, case history, channel, transcript, routing queues, priority, skills, and preferences.

### Architecture

```text
Customer
   |
   +-------------------------------+
   |        Contact Channels       |
   | Voice | Live Chat | Messaging |
   +---------------+---------------+
                   |
                   v
          Dynamics 365 Contact Center
                   |
          +--------+--------+
          |                 |
          v                 v
     Customer Context    AI Agent
          |                 |
          +--------+--------+
                   |
                   v
          Service Experience
```

### Key Components

- Voice
- Live chat
- Digital messaging
- Customer identity
- Case history
- Transcript
- Routing queues
- Priority
- Skills
- Customer preferences

### Example

A customer starts a live chat. The service experience can use the customer's case history and current conversation context to support the interaction.

---

## 7. Design Task Agents in Microsoft Copilot Studio

### Concept

A task agent is designed for a specific business task.

The design identifies the goal, required skills, actions, knowledge, context, and safety rules needed to complete that task.

### Architecture

```text
Business Task
     |
     v
 Task Goal
     |
 +---+---+---+
 |   |   |   |
 v   v   v   v
Goal Skills Actions Knowledge
 |       |      |
 +-------+------+ 
         |
         v
   Copilot Studio
         |
         v
     Task Result
```

### Key Components

- Goal
- Skills
- Actions
- Knowledge
- Context
- Safety rules

### Example

A task agent can be designed to help complete a specific service operation by retrieving information and performing the required business action.

---

## 8. Design Autonomous Agents in Copilot Studio

### Concept

Autonomous agents can act when an event or condition occurs rather than waiting only for a direct conversational request.

Triggers can include user input, system changes, or scheduled prompts.

### Architecture

```text
Trigger
  |
  +------------------+
  |        |         |
  v        v         v
User     System    Schedule
Input     Event      Prompt
  |        |         |
  +--------+---------+
           |
           v
    Autonomous Agent
           |
     +-----+-----+
     |           |
     v           v
  Knowledge    Actions
     |           |
     +-----+-----+
           |
           v
      Business Result
```

### Key Components

- Trigger
- Goal
- Knowledge
- Actions
- Business rules
- Testing and refinement

### Example

A scheduled trigger can start an agent process that checks business information and performs an approved action.

---

## 9. Design Prompt-Driven Agents Using Copilot Studio

### Concept

Prompt-driven agents use natural language interactions and can combine NLU, topics, conditions, triggers, knowledge, and generative answers.

Knowledge can come from sources such as SharePoint, Dataverse, enterprise connectors, and custom data flows.

### Architecture

```text
User Message
     |
     v
Natural Language Understanding
     |
     v
Topic / Condition / Trigger
     |
     +-------------------+
     |                   |
     v                   v
  Knowledge        Generative Answer
     |                   |
     +---------+---------+
               |
               v
        Agent Response
```

### Key Components

- Natural language understanding
- Topics
- Conditions
- Triggers
- Knowledge
- Generative answers
- SharePoint
- Dataverse
- Enterprise connectors

### Example

A user asks a service question in natural language. The agent identifies the relevant interaction path and uses approved knowledge to produce a response.

---

## 10. Propose Foundry Tools Given a Requirement

### Concept

Microsoft Foundry provides tools that can support different agent requirements.

The tool should match the requirement. Examples include retrieval and grounding, data and application connectors, workflow and action tools, reasoning and planning, and specialized tools.

### Architecture

```text
Business Requirement
        |
        v
   Requirement Type
        |
 +------+------+------+------+
 |      |      |      |      |
 v      v      v      v      v
Retrieve Connect Workflow Reasoning Specialized
/Ground  Data    /Action  /Planning   Tools
        |
        v
     AI Agent
        |
        v
    Business Task
```

### Key Components

- Retrieval and grounding
- Data connectors
- Application connectors
- Workflow/action tools
- Reasoning/planning
- Specialized tools
- Agent

### Example

If an agent must retrieve enterprise information, a retrieval or grounding capability is relevant. If it must execute a business process, an action or workflow capability is relevant.

---

## 11. Propose Code-First Generative Pages and Agent Feed Applications

### Concept

Generative Pages can create pages from natural-language descriptions using Dataverse data. Code-first extensions can provide additional application capabilities.

Agent Feed can present summaries, recommendations, anomalies, contextual insights, and guided actions.

### Architecture

```text
Business Requirement
        |
        +-------------------+
        |                   |
        v                   v
 Generative Page        Agent Feed
        |                   |
        v                   v
 Dataverse Data       Business Context
        |                   |
        +---------+---------+
                  |
                  v
          User Experience
```

### Key Components

- Generative Pages
- Dataverse
- Code-first extensions
- Agent Feed
- Summaries
- Recommendations
- Anomalies
- Contextual insights
- Guided actions

### Example

A business application can present a Dataverse-based page with AI-generated business information and an agent feed containing recommendations and relevant actions.

---

## 12. Design Topics for Copilot Studio, Including Fallback

### Concept

A topic represents a conversational path in Copilot Studio. It can include a trigger, message, question, condition, and action.

Fallback handles situations where the agent does not recognize the user's intent, encounters unexpected phrasing, or does not have appropriate topic coverage.

### Architecture

```text
User Message
     |
     v
   Trigger
     |
     v
    Topic
     |
 +---+---+---+
 |   |   |   |
 v   v   v   v
Msg Question Condition Action
     |
     v
  Response

If intent/topic is not covered
     |
     v
   Fallback
```

### Key Components

- Trigger
- Message
- Question
- Condition
- Action
- Topic
- Fallback

### Example

If a user asks something outside the configured topics, the fallback behavior provides the defined response or handling path.

---

## 13. Design Data Processing Workflows for Grounded AI

### Concept

Grounded AI uses enterprise data to improve the relevance and accuracy of AI responses.

A grounding pipeline can include ingestion, preparation, indexing, and retrieval. Data preparation can include chunking, embeddings, schema handling, indexing, freshness, and provenance.

Hybrid retrieval can combine vector search, keyword search, and semantic ranking.

Security and access controls must be preserved when grounding data is used.

### Architecture

```text
Enterprise Data
      |
      v
   Ingestion
      |
      v
 Data Preparation
(chunking / embeddings /
 schema / metadata)
      |
      v
    Indexing
      |
      v
    Retrieval
  +---+---+---+
  |   |   |   |
Vector Keyword Semantic
Search  Search  Ranking
  |      |       |
  +------+------+ 
         |
         v
     AI Model
         |
         v
 Grounded Response
```

### Key Components

- Ingestion
- Data preparation
- Chunking
- Embeddings
- Schema
- Indexing
- Retrieval
- Vector search
- Keyword search
- Semantic ranking
- Freshness
- Provenance
- Security and access controls

### Example

A service agent can retrieve information from approved enterprise documents and use that information as grounding for an AI response.

---

## 14. Design Business Processes with AI in Power Apps Canvas Apps

### Concept

AI can be integrated into Power Apps canvas app business processes.

The process can identify where AI adds value, design the Copilot interaction, and integrate AI into the application workflow.

Examples include customer summaries, creating records from documents, guiding form entry, recommending values, and validating information.

### Architecture

```text
Business Process
       |
       v
Power Apps Canvas App
       |
       +-------------------+
       |                   |
       v                   v
   User Input          AI Capability
                           |
                 +---------+---------+
                 |         |         |
                 v         v         v
             Summary    Recommend  Validate
                 |         |         |
                 +---------+---------+
                           |
                           v
                    App Business Data
```

### Key Components

- Business process
- Power Apps canvas app
- User interaction
- AI capability
- Dataverse/business data
- Summary
- Recommendations
- Validation

### Example

A canvas app can use AI to summarize customer information and help a user complete a business form.

---

## 15. Apply the Microsoft Power Platform Well-Architected Framework to Intelligent Application Workloads

### Concept

The Microsoft Power Platform Well-Architected Framework provides architecture considerations for intelligent applications.

The five areas are:

- Reliability
- Security
- Operational Excellence
- Performance Efficiency
- Experience Optimization

### Architecture

```text
                 Intelligent Application
                         |
      +------------------+------------------+
      |         |        |        |         |
      v         v        v        v         v
 Reliability Security Operational Performance Experience
                       Excellence  Efficiency Optimization
      |         |        |        |         |
      +---------+--------+--------+---------+
                         |
                         v
                Business Application
```

### Key Components

- Reliability
- Security
- Operational Excellence
- Performance Efficiency
- Experience Optimization

### Example

An AI-enabled Power Platform application should be designed with security, reliable operation, performance, operational management, and user experience in mind.

---

## 16. Determine the Use of Standard Natural Language Processing

### Concept

The language-processing approach should match the requirement.

- Standard NLU is appropriate for predictable commands.
- Azure Conversational Language Understanding (CLU) can be used for variable language with bounded intents and entities.
- Generative AI orchestration is appropriate for open-ended reasoning, knowledge use, summarization, and multi-turn interactions.

### Architecture

```text
User Language Requirement
          |
          v
     Determine Need
          |
   +------+--------+----------------+
   |               |                |
   v               v                v
Predictable     Bounded          Open-ended
Commands        Intents/Entities Reasoning
   |               |                |
   v               v                v
Standard NLU       CLU       Generative AI
   |               |                |
   +---------------+----------------+
                   |
                   v
             Agent Experience
```

### Key Components

- Standard NLU
- Intents
- Entities
- Azure CLU
- Generative AI
- Open-ended reasoning
- Multi-turn interaction

### Example

A fixed command with predictable wording can use standard NLU, while a business scenario with varied language and defined intents may use CLU.

---

## 17. Design Agents and Agent Flows with Copilot Studio

### Concept

An agent provides intelligence, while an agent flow automates execution.

Agent flows can connect systems, trigger business logic, and execute actions inside Copilot Studio.

Triggers can include user messages, scheduled events, system events, or another agent. Actions can include sending email, updating data, retrieving information, interacting with CRM systems, and sending notifications.

### Architecture

```text
Trigger
  |
  +----------------+----------------+----------------+
  |                |                |                |
User Message   Schedule       System Event      Another Agent
  |                |                |                |
  +----------------+----------------+----------------+
                   |
                   v
                 Agent
                   |
                   v
               Agent Flow
                   |
        +----------+----------+
        |          |          |
        v          v          v
    Retrieve    Update      Notify
    Data        Data        Users
        |          |          |
        +----------+----------+
                   |
                   v
             Business Result
```

### Key Components

- Agent
- Agent flow
- Triggers
- Business logic
- Connectors
- Actions
- Data retrieval
- Notifications

### Example

A user asks an agent to perform a business operation. The agent flow can retrieve the required information, update business data, and send a notification.

---

## 18. Design Prompt Actions in Copilot Studio

### Concept

Prompt actions are reusable instruction blocks that can be used within an agent solution.

A prompt can be structured with:

- Goal
- Context
- Instructions or rules
- Examples
- Output format

Prompt Coach can support the creation of this structure.

### Architecture

```text
Business Task
     |
     v
Prompt Action
     |
 +---+----------------------+
 |   |          |      |    |
 v   v          v      v    v
Goal Context Instructions Examples Output
                 /Rules      |      Format
     |            |          |        |
     +------------+----------+--------+
                  |
                  v
              AI Response
```

### Key Components

- Goal
- Context
- Instructions
- Rules
- Examples
- Output format
- Prompt action
- Prompt Coach

### Example

A prompt action can define that an AI response must use specific business context, follow defined rules, and return information in a consistent format.

---

## 19. Define Success Criteria and Adoption Goals for AI Business Solutions

### Concept

Success criteria should connect the AI solution to measurable business outcomes.

Useful categories include:

- Business value
- Operational efficiency
- User experience
- Quality and accuracy
- Risk and compliance
- Scalability

Readiness includes organizational, data, technical, and user-adoption considerations.

### Architecture

```text
Business Goal
     |
     v
Success Criteria
     |
 +---+---+---+---+---+---+
 |   |   |   |   |   |   |
 v   v   v   v   v   v
Value Efficiency UX Quality Risk Scale
 |       |       |    |      |    |
 +-------+-------+----+------+----+
                 |
                 v
             AI Solution
                 |
                 v
          Adoption & Outcomes
```

### Key Components

- Business value
- Operational efficiency
- User experience
- Quality and accuracy
- Risk and compliance
- Scalability
- Organizational readiness
- Data readiness
- Technical readiness
- User adoption

### Example

A customer service AI solution can define measurable outcomes around service efficiency, response quality, user experience, and compliance.

---

# Module Architecture

The topics in this module connect into an end-to-end AI agent design:

```text
                         Business Requirement
                                  |
                                  v
                         Success Criteria
                                  |
                                  v
                       Responsible AI Principles
                                  |
                                  v
                         Agent Design Pattern
                                  |
              +-------------------+-------------------+
              |                   |                   |
              v                   v                   v
        Task Agent          Autonomous Agent   Prompt-Driven Agent
              |                   |                   |
              +-------------------+-------------------+
                                  |
                                  v
                          Knowledge + Grounding
                                  |
                 +----------------+----------------+
                 |                                 |
                 v                                 v
          Dataverse / D365                 SharePoint / Other
                 |                                 |
                 +----------------+----------------+
                                  |
                                  v
                         Actions + Connectors
                                  |
                 +----------------+----------------+
                 |                                 |
                 v                                 v
          Agent Flows                      Dynamics 365
                 |                                 |
                 +----------------+----------------+
                                  |
                                  v
                         Power Platform Apps
                                  |
                                  v
                 Well-Architected Application Design
                                  |
                                  v
                       Adoption and Measurement
                                  |
                                  v
                         Business Outcome
```

## Microsoft Learn Source

- [Design AI agents for business solutions](https://learn.microsoft.com/en-us/training/modules/design-ai-agents-business-solutions/)

The current Microsoft Learn module lists 21 units: 19 instructional topics followed by the module assessment and summary.
