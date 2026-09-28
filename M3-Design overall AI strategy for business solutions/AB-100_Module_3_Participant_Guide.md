# AB-100 Module 3 --- Design Overall AI Strategy for Business Solutions

## Purpose

This participant guide converts the Microsoft Learn Module 3 content
into architect-focused teaching material. The source module focuses on
enterprise AI strategy, Cloud Adoption Framework alignment, agent
platform choices, multi-agent architecture, knowledge, prompts, models,
roles, compliance, AI Center of Excellence, Dynamics 365 integration,
and user adoption. Microsoft Learn currently identifies this as an
advanced Solution Architect module and lists Microsoft 365 Copilot,
Microsoft 365 Copilot Chat, Power Platform, Copilot Studio, and Dynamics
365 as relevant technologies. citeturn1search0

## Architecture Lens

Use this decision chain throughout the module:

``` text
Business Outcomes
      ↓
AI Use Cases
      ↓
Adoption Strategy
      ↓
Platform / Agent Choice
      ↓
Data + Knowledge
      ↓
Rules + Constraints
      ↓
Models + Prompts
      ↓
Security + Compliance
      ↓
Operating Model + AI CoE
      ↓
User Adoption
      ↓
Measured Business Outcome
```

------------------------------------------------------------------------

## Topic 1 --- Introduction

### Concept

Designing an overall AI strategy means connecting business outcomes, AI
use cases, technology choices, data, governance, people, and adoption
into one enterprise direction.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 2 --- Implement AI adoption process with Azure

### Concept

Use the Cloud Adoption Framework (CAF) AI adoption phases---Strategy,
Plan, Ready, Govern, Secure, Manage---and align them with the AI agent
lifecycle: Plan agents, Govern & secure agents, Build agents, and
Operate agents.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 3 --- Design strategy for building AI agents for business solutions

### Concept

Start with measurable business outcomes, then choose the least complex
agent approach that meets the requirement: prebuilt/SaaS, low-code
Copilot Studio, or pro-code Microsoft Foundry/custom hosting.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 4 --- Design a multi-agent solution

### Concept

Start with a single agent. Introduce multiple agents when separation of
security/compliance, team ownership, modular specialization, or
multi-workstream dependencies justify the added orchestration, latency,
cost, and security surface.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 5 --- Develop use cases for prebuilt Microsoft 365 Copilot agents

### Concept

Use prebuilt agents when the business process fits existing Microsoft
365 capabilities and the organization needs fast value with limited
customization.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 6 --- Define solution rules and constraints for AI components

### Concept

Define explicit boundaries for data, tools, actions, behavior,
networking, environments, operations, and human approval before an AI
component moves into production.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 7 --- Determine generative AI knowledge sources for agents built in Copilot Studio

### Concept

Choose knowledge sources according to the information the agent must
retrieve, the source's authority and freshness, authentication,
retrieval behavior, and governance requirements.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 8 --- Determine when to build custom agents or extend Microsoft 365 Copilot

### Concept

Extend Microsoft 365 Copilot when the scenario is mainly Microsoft 365
productivity and the required customization is simple. Build a custom
agent when specialized workflows, complex orchestration, external
systems, autonomy, or multi-agent behavior are required.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 9 --- Determine when custom AI models should be created

### Concept

Treat custom model development as a strategic exception. First test
prebuilt/catalog models, prompting, retrieval, and other available
options; move to custom models only when business, model, data, cost,
and operational fit justify it.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 10 --- Provide guidelines for creating a prompt library

### Concept

A prompt library is a governed collection of tested, reusable prompts.
It improves consistency, efficiency, quality, and organizational
scalability.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 11 --- Develop use cases for customized small language models

### Concept

Customized SLMs can fit focused domain tasks where latency, cost, memory
footprint, offline/edge operation, or specialized behavior matters. They
are not automatically safer or more accurate than larger models.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 12 --- Provide prompt engineering guidelines and techniques

### Concept

Design prompts with clear tasks, context, audience, constraints,
reference material, and expected output. Evaluate prompts against
accuracy, clarity, consistency, safety, and business outcomes.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 13 --- Identify key business user roles for AI workloads

### Concept

Define accountable business and technical roles such as executive
sponsor, AI CoE lead, AI product owner, architect, data owner,
security/compliance, and operations so AI workloads have clear
ownership.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 14 --- Evaluate regional and local AI data regulation compliance requirements

### Concept

Evaluate privacy, AI-specific, industry, cross-border, retention,
transparency, human-oversight, and documentation requirements for every
jurisdiction in scope.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 15 --- Include elements in a Microsoft AI Center of Excellence

### Concept

An AI CoE provides leadership, governance, standards, expert capability,
reusable assets, skills, portfolio oversight, and operational guidance
to scale AI responsibly.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 16 --- Design AI solutions using multiple Dynamics 365 apps

### Concept

Design for shared business context, process continuity, data
interoperability, long-lived business objects, and governed sources when
AI crosses Sales, Customer Service, Finance, Field Service, or other
Dynamics workloads.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 17 --- Design user prompt training for AI solution adoption

### Concept

Train different user personas on prompting, validation, responsible use,
accessibility, and workflow integration. Adoption is a
people-and-process change, not only a technology deployment.

### Architecture Perspective

Ask these questions before choosing a technology:

1.  What business outcome must improve?
2.  What part of the process should AI perform?
3.  What data and knowledge are required?
4.  What platform provides the required capability with the least
    unnecessary complexity?
5.  What actions can the AI perform, and which actions require human
    approval?
6.  What security, compliance, and regional constraints apply?
7.  How will the workload be monitored, operated, and improved?

### Whiteboard Architecture

``` text
Business Need
    ↓
Use Case + Success Measure
    ↓
AI Capability
    ↓
Platform / Agent Pattern
    ↓
Knowledge + Data + Tools
    ↓
Rules / Guardrails / Identity
    ↓
AI Response or Business Action
    ↓
Human / Business Process
    ↓
Monitoring + Improvement
```

### Architect Questions

**Q: What should the architect decide first?**\
Expected answer: The business outcome and the use case, before selecting
the AI technology.

**Q: What is the main architecture risk?**\
Expected answer: Choosing technology before defining business, data,
security, and operational requirements.

## Topic 2 --- CAF and AI Agent Lifecycle Mapping

### Whiteboard

``` text
CAF                         Agent Lifecycle
────────────────────        ─────────────────────
Strategy       ───────────→ Plan agents
Plan           ───────────→ Plan agents
Ready          ───────────→ Govern & secure
Govern         ───────────→ Govern & secure
Secure         ───────────→ Govern & secure
Manage         ───────────→ Operate agents

                 Build agents
                    ↓
              Production
                    ↓
              Operate + Improve
```

The Microsoft Learn unit maps CAF phases to the agent lifecycle and
emphasizes landing zones, data, security, governance, standardized build
processes, monitoring, cost controls, and operational readiness.
citeturn2view0

**Q: Why use CAF for AI?**\
Expected answer: It provides an enterprise adoption and operating
backbone for strategy, readiness, governance, security, and management.

**Q: What should come out of the strategy phase?**\
Expected answer: Business outcomes, prioritized use cases, technology
choices, data and Responsible AI direction, and an agent technology
plan.

------------------------------------------------------------------------

## Topic 3 --- Agent Technology Decision

### Decision Tree

``` text
Does an existing SaaS / prebuilt agent meet the requirement?
          │
      Yes ├────────→ Use it
          │
          No
          ↓
Can Copilot Studio meet the workflow with low-code customization?
          │
      Yes ├────────→ Build low-code agent
          │
          No
          ↓
Is complex orchestration / custom logic / deep integration required?
          │
      Yes ├────────→ Consider Microsoft Foundry / pro-code
          │
          ↓
Do compliance or isolation requirements require full model/runtime control?
          └────────→ Consider custom hosting / containers
```

Microsoft Learn describes SaaS, low-code, pro-code, and controlled
hosting options and recommends starting with the simplest approach that
meets functional requirements. citeturn2view1

------------------------------------------------------------------------

## Topic 4 --- Single-Agent vs Multi-Agent

### Decision

``` text
                    Start
                      ↓
              Single agent works?
                /           \
              Yes            No
               ↓              ↓
          Keep simple    Identify complexity
                              ↓
        ┌─────────────────────┼────────────────────┐
        ↓                     ↓                    ↓
 Security boundary     Team ownership       Multi-step dependencies
        ↓                     ↓                    ↓
        └─────────────────────┼────────────────────┘
                              ↓
                       Multi-agent design
```

Multi-agent architecture adds coordination, latency, cost, and security
surface. Use it when separation of concerns, security boundaries,
independent ownership, or multi-workstream dependencies justify the
complexity. Microsoft Learn also describes sequential, concurrent,
group-chat, handoff, and Magentic orchestration patterns.
citeturn2view2

**Q: What is the default starting point?**\
Expected answer: Start with a single agent and add agents only when
evidence shows that decomposition is useful.

------------------------------------------------------------------------

## Topic 5 --- Prebuilt Microsoft 365 Copilot Agents

Prebuilt agents are useful for repetitive, high-frequency,
knowledge-heavy work such as summarization, knowledge retrieval,
drafting, policy guidance, and routine workflows. Use case selection
should consider task frequency, knowledge intensity, pain points, and
measurable business KPIs. citeturn4view0

### Whiteboard

``` text
Microsoft 365 Work
 Outlook / Teams / Word / SharePoint
              ↓
     Prebuilt Copilot Agent
              ↓
     Knowledge + Context
              ↓
       User Productivity
```

**Q: When should an architect consider a prebuilt agent first?**\
Expected answer: When existing capabilities already satisfy the business
requirement with little customization.

------------------------------------------------------------------------

## Topic 6 --- Rules and Constraints

### Constraint Layers

``` text
AI Component
   │
   ├── Behavior rules
   ├── Data boundaries
   ├── Tool/action permissions
   ├── Human approval rules
   ├── Identity/access rules
   ├── Environment/network rules
   ├── Evaluation requirements
   └── Operational limits
```

Copilot Studio is positioned for governed low-code task/retrieval
scenarios, while Foundry supports higher-complexity orchestration and
requires stronger explicit governance around tools, models, memory,
evaluation, and operations. citeturn4view1

**Q: Why define rules before production?**\
Expected answer: To make AI behavior predictable, secure, compliant, and
bounded.

------------------------------------------------------------------------

## Topic 7 --- Knowledge Sources in Copilot Studio

### Knowledge Decision

``` text
Business Question
      ↓
What information is required?
      ↓
Authoritative source
      ↓
SharePoint / Dataverse / Files / Website /
Azure AI Search / Connector
      ↓
Authentication + Permissions
      ↓
Retrieval
      ↓
Grounded Answer
```

Copilot Studio supports enterprise knowledge sources and generative
orchestration that can combine topics, tools, connected agents, and
knowledge. Current Microsoft documentation lists sources such as
SharePoint, uploaded files, Dataverse, Azure AI Search, OneDrive, and
connectors, depending on the environment. citeturn3view2turn0search2

**Q: What makes a knowledge source architecturally suitable?**\
Expected answer: It is authoritative, relevant, sufficiently current,
accessible to the intended users, and governed.

------------------------------------------------------------------------

## Topic 8 --- Extend Microsoft 365 Copilot or Build Custom?

  Requirement                                  Typical direction
  -------------------------------------------- ------------------------------
  Microsoft 365 productivity workflow          Extend Microsoft 365 Copilot
  Organization-specific knowledge              Extend when simple
  Simple connector/plugin requirement          Extend
  Complex multi-step workflow                  Custom agent
  External system integration                  Custom agent
  Multi-agent collaboration                    Custom agent
  Operational autonomy outside Microsoft 365   Custom agent

Microsoft Learn describes extension when core Copilot capabilities
already fit the workflow and custom agents when specialized workflows,
complex orchestration, external systems, autonomy, or multi-agent
behavior are required. citeturn4view3

------------------------------------------------------------------------

## Topic 9 --- Custom AI Models

### Decision

``` text
Prebuilt / Catalog Model
        ↓
Prompting + Retrieval + Evaluation
        ↓
Does it meet the requirement?
      /       \
    Yes        No
     ↓          ↓
Use it     Investigate customization
                ↓
       Business + Model + Data
       + Cost + Operations fit
                ↓
          Custom model
```

Microsoft Learn advises considering custom models only when existing
models cannot meet accuracy, domain, compliance, or predictability needs
and ROI supports the additional engineering and operational cost.
citeturn4view4

**Q: What should happen before custom model development?**\
Expected answer: Evaluate prebuilt/catalog models, prompting, retrieval,
and other available approaches.

------------------------------------------------------------------------

## Topic 10 --- Prompt Library

A prompt library is a governed collection of reusable and tested
prompts. It supports consistency, quality, efficiency, governance, and
scale. citeturn3view5

### Whiteboard

``` text
Prompt Candidate
      ↓
Test
      ↓
Evaluate
      ↓
Approve
      ↓
Publish to Library
      ↓
Version + Owner + Scope
      ↓
Monitor + Improve
```

**Q: What turns a prompt into an enterprise asset?**\
Expected answer: Testing, ownership, governance, versioning, reuse, and
measurable quality.

------------------------------------------------------------------------

## Topic 11 --- Customized Small Language Models

Customized SLMs are useful when focused domain behavior, low latency,
lower inference cost, smaller memory footprint, edge/offline operation,
or task specialization matters. They are not automatically safer or more
accurate than larger models. citeturn4view5

### Architecture

``` text
Focused Business Task
        ↓
Curated Domain Data
        ↓
Customized SLM
        ↓
Low-latency Inference
        ↓
Business Application / Device
```

**Q: Why choose an SLM?**\
Expected answer: Because the workload benefits from focused capability,
cost, latency, footprint, or deployment constraints.

------------------------------------------------------------------------

## Topic 12 --- Prompt Engineering

### Enterprise Prompt Pattern

``` text
Role / Context
      +
Task
      +
Reference Data
      +
Constraints
      +
Expected Output
      +
Validation Criteria
```

Microsoft Learn emphasizes clarity, context, constraints, accuracy,
consistency, governance, and business alignment. citeturn4view6

**Q: Why is context important?**\
Expected answer: It tells the model the business purpose, audience,
source material, and boundaries needed for a useful response.

------------------------------------------------------------------------

## Topic 13 --- Business User Roles

### Operating Model

``` text
Executive Sponsor
       ↓
AI CoE Lead
       ↓
AI Product Owner ─── Solution Architect
       ↓                    ↓
Business SMEs         Data / Security / Compliance
       ↓                    ↓
Users / Champions ─── AI Platform / Operations
```

Microsoft Learn identifies roles including executive sponsor, AI CoE
lead, and AI product owner, with responsibilities covering strategy,
governance, business outcomes, roadmap, budget, and lifecycle ownership.
citeturn4view7

**Q: Who owns the business outcome?**\
Expected answer: The AI product owner or accountable business owner, not
the AI model itself.

------------------------------------------------------------------------

## Topic 14 --- Regional and Local AI Regulation

### Compliance Architecture

``` text
Business Use Case
      ↓
Data Classification
      ↓
Jurisdictions
      ↓
Applicable Regulations
      ↓
Platform / Data Location / Access Controls
      ↓
Retention + Privacy + Human Oversight
      ↓
Evidence + Audit
```

Relevant domains include data privacy, AI-specific regulation, industry
requirements, cross-border transfer, responsible AI, retention,
transparency, and human oversight. Microsoft Learn specifically
references examples including the EU AI Act, India DPDP Act, CCPA/CPRA,
LGPD, and other regional frameworks. citeturn4view8

**Q: Should an architect assume one global AI compliance model is
enough?**\
Expected answer: No; requirements must be evaluated for the
jurisdictions and data involved.

------------------------------------------------------------------------

## Topic 15 --- AI Center of Excellence

### AI CoE Architecture

``` text
Executive Leadership
        ↓
AI CoE
 ┌──────┼────────┬────────┐
 ↓      ↓        ↓        ↓
Strategy Governance Skills Reuse
 ↓      ↓        ↓        ↓
Portfolio → Standards → Delivery → Operations
```

An AI CoE provides leadership, governance, standardized practices,
cross-functional alignment, expert support, and a mechanism to reduce
duplication and ungoverned adoption. citeturn4view9

**Q: What is the main purpose of an AI CoE?**\
Expected answer: To help the organization scale AI responsibly and
consistently while aligning technology with business value.

------------------------------------------------------------------------

## Topic 16 --- Multiple Dynamics 365 Apps

### Cross-App Architecture

``` text
Customer / Product / Case / Order
              ↓
        Shared Business Context
              ↓
 ┌────────────┼────────────┐
 ↓            ↓            ↓
Sales     Customer Service  Finance
 ↓            ↓            ↓
        Field Service
              ↓
        AI / Agents
              ↓
      Consistent Process
```

Cross-app AI requires shared business context, process continuity,
harmonized data, clean integration boundaries, and authoritative
sources. Microsoft Learn highlights Sales → Customer Service → Finance →
Field Service as an example of a process that may span applications.
citeturn4view10

**Q: What is the biggest architectural concern?**\
Expected answer: Maintaining consistent business context and governed
data across application boundaries.

------------------------------------------------------------------------

## Topic 17 --- User Prompt Training and Adoption

### Adoption Architecture

``` text
User Persona
    ↓
Role-specific AI Training
    ↓
Prompt Skills
    ↓
Output Validation
    ↓
Responsible Use
    ↓
Workflow Integration
    ↓
Usage + Outcome Measurement
    ↓
Continuous Improvement
```

Microsoft Learn emphasizes that adoption requires skilling,
accessibility, governance, prompt fluency, validation, and responsible
use---not simply deploying technology. citeturn4view11

**Q: Should every user receive the same AI training?**\
Expected answer: No; training should reflect persona, workflow,
responsibility, and AI maturity.

------------------------------------------------------------------------

# Module 3 --- Final Architect Whiteboard

``` text
                     ENTERPRISE AI STRATEGY
                              │
             ┌────────────────┴────────────────┐
             ↓                                 ↓
       Business Outcomes                 AI Use Cases
             │                                 │
             └──────────────┬──────────────────┘
                            ↓
                   Adoption Strategy
                            ↓
             ┌──────────────┼──────────────┐
             ↓              ↓              ↓
        Prebuilt SaaS   Copilot Studio   Foundry / Custom
             │              │              │
             └──────────────┼──────────────┘
                            ↓
                    Data + Knowledge
                            ↓
                 Rules + Guardrails
                            ↓
            Models + Prompts + Tools
                            ↓
             Security + Compliance
                            ↓
                  AI CoE + Roles
                            ↓
              Dynamics / Business Apps
                            ↓
                  User Adoption
                            ↓
                 Operate + Measure
                            ↓
                    Business Value
```

## Final Architect Questions

**Q: What is the overall strategy sequence?**\
Expected answer: Business outcomes → use cases → adoption → platform →
data → guardrails → operations → adoption measurement.

**Q: When should an architect choose a prebuilt solution?**\
Expected answer: When it already meets the business requirement with
acceptable customization and governance.

**Q: When is multi-agent architecture justified?**\
Expected answer: When security boundaries, independent ownership,
modular specialization, or multi-workstream dependencies justify the
added complexity.

**Q: What should be governed centrally?**\
Expected answer: AI portfolio, standards, security, data access,
responsible AI, evaluation, prompts, roles, compliance, and operational
practices.

**Q: What makes an AI strategy enterprise-ready?**\
Expected answer: Clear business value, appropriate technology choices,
governed data, explicit constraints, accountable roles, compliance,
operations, and user adoption.

## Source Alignment

Primary source: Microsoft Learn, **Design overall AI strategy for
business solutions**. The module currently lists 19 units and learning
objectives covering CAF alignment, enterprise agent operating model,
Microsoft platform selection, and transition from proof of concept to
production. citeturn1search0
