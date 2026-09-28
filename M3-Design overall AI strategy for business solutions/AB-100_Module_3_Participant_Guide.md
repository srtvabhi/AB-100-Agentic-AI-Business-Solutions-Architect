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

CAF gives the enterprise adoption backbone; the agent lifecycle adds
agent-specific planning, governance, building, and operations. The key
is to turn each phase into a concrete architecture gate.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Use CAF to prevent agent sprawl and architecture drift.
-   Treat landing zones and data foundations as prerequisites, not
    afterthoughts.
-   Define an agent readiness checklist before production.
-   Assign clear RACI ownership across architecture, platform, security,
    and data.
-   Operations must include telemetry, SLOs, cost, incident response,
    and retirement.

### Architecture Diagram

``` text
Strategy → Plan agents → business outcomes, use cases, platform decision, ROI hypothesis, Responsible AI
Plan → Plan agents → skills, starter project, PoC, readiness assessment
Ready → Govern & secure → landing zones, data foundation, identity, governance boundaries
Govern → Govern & secure → policies, approvals, risk controls, audit
Secure → Govern & secure → data/model/endpoint protection
Build → Build agents → templates, evaluation gates, environments, CI/CD
Manage → Operate agents → telemetry, SLOs, cost, incidents, lifecycle
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What should Strategy produce?**\
**Expected answer:** An AI strategy brief and agent technology plan with
prioritized use cases, platform direction, guardrails, and success
measures.

**Q: What should Ready establish?**\
**Expected answer:** Landing zones, resource organization, connectivity,
data foundations, identity, and governance boundaries.

**Q: What is the purpose of the Build phase?**\
**Expected answer:** To standardize how agents are developed, evaluated,
deployed, and governed.

**Q: What belongs in Operate?**\
**Expected answer:** Monitoring, SLOs, cost/usage reporting, incident
response, rollout, tuning, and lifecycle management.

------------------------------------------------------------------------

## Topic 3 --- Design strategy for building AI agents for business solutions

### Concept

AI agent strategy starts with measurable business outcomes and then
selects the least complex technology that satisfies the requirements.
Microsoft Learn describes SaaS/prebuilt, Copilot Studio low-code,
Foundry pro-code, and controlled hosting options.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Start with business outcome and measurable impact.
-   Compare SaaS, low-code, and pro-code against requirements---not
    popularity.
-   Check grounding, permissions, integration, latency, availability,
    and networking.
-   Use Dynamics 365 copilots as a benchmark before building custom
    capabilities.
-   Plan operational ownership and change management before selecting
    the runtime.

### Architecture Diagram

``` text
Business outcome
   ↓
Does SaaS / prebuilt fit?
   ├─ Yes → Use it
   └─ No
        ↓
Can Copilot Studio fit?
   ├─ Yes → Low-code agent
   └─ No
        ↓
Complex orchestration / integration?
   ├─ Yes → Foundry / pro-code
   └─ No
        ↓
Need strict isolation / runtime control?
   └─ Consider controlled hosting
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: When should SaaS/prebuilt be used?**\
**Expected answer:** When it meets the functional requirement with
minimal customization.

**Q: When is Copilot Studio a strong fit?**\
**Expected answer:** For rapid low-code task/retrieval agents,
business-led customization, connectors, and moderate workflow
complexity.

**Q: When is Foundry a stronger fit?**\
**Expected answer:** For complex orchestration, deep integrations,
advanced generative behavior, or sophisticated multi-agent workflows.

**Q: What drives hosting choice?**\
**Expected answer:** Security/isolation, latency, availability,
networking, integration, compliance, and operational requirements.

------------------------------------------------------------------------

## Topic 4 --- Design a multi-agent solution

### Concept

Multi-agent architecture decomposes responsibilities across specialized
agents. Start with one agent unless security boundaries, team ownership,
specialization, future modularity, or multi-workstream dependencies
justify the extra coordination cost.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Define every agent's role, scope, tools, permissions, inputs,
    outputs, and escalation rules.
-   Sequential = staged pipeline; concurrent = parallel independent
    work.
-   Group chat = mediated collaboration; handoff = controlled transfer;
    Magentic = dynamic specialist selection.
-   Account for latency, cost, security surface, observability, and
    failure handling.
-   Many apparent multi-agent requirements can be solved with better
    retrieval, policies, or a single agent.

### Architecture Diagram

``` text
User
 ↓
Orchestrator
 ├── Customer Agent → customer data
 ├── Finance Agent → finance data
 └── Field Service Agent → field data
        ↓
Context / results combined
        ↓
Human or business action
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: When should a single agent remain the default?**\
**Expected answer:** When the domain is bounded and decomposition is not
required by security, ownership, or workflow complexity.

**Q: What justifies multiple agents?**\
**Expected answer:** Security/compliance boundaries, distinct team
ownership, modular specialization, future expansion, or dependent
workstreams.

**Q: What is concurrent orchestration?**\
**Expected answer:** Independent subtasks run in parallel and their
results are aggregated.

**Q: What is handoff orchestration?**\
**Expected answer:** Context and control move to a specialist agent or
human when a rule or threshold is reached.

------------------------------------------------------------------------

## Topic 5 --- Develop use cases for prebuilt Microsoft 365 Copilot agents

### Concept

Prebuilt Microsoft 365 Copilot agents are strong candidates for
repetitive, high-frequency, knowledge-heavy work where users already
operate in Microsoft 365. Architects should connect the use case to
measurable KPIs.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Measure task frequency per user or team.
-   Measure knowledge intensity and search effort.
-   Identify delays, errors, bottlenecks, and manual drafting.
-   Tie the use case to hours saved, cycle time, ticket volume, or
    another KPI.
-   Validate permissions and organizational knowledge before adoption.

### Architecture Diagram

``` text
Task frequency
     +
Knowledge intensity
     +
Pain point
     +
Microsoft 365 context
     +
Measurable KPI
     ↓
Prebuilt Copilot agent
     ↓
Retrieval / drafting / guidance
     ↓
Productivity outcome
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What is a strong prebuilt-agent use case?**\
**Expected answer:** A repetitive, knowledge-heavy task with measurable
value that fits existing Microsoft 365 workflows.

**Q: Why measure frequency?**\
**Expected answer:** High-frequency tasks provide more opportunity for
measurable productivity gains.

**Q: Why measure knowledge intensity?**\
**Expected answer:** Knowledge-heavy tasks benefit from fast retrieval
and synthesis.

**Q: What must be validated before adoption?**\
**Expected answer:** Business fit, knowledge access, permissions,
expected KPI impact, and limitations.

------------------------------------------------------------------------

## Topic 6 --- Define solution rules and constraints for AI components

### Concept

Rules and constraints define what an AI component may know, do, access,
and decide. Copilot Studio provides managed low-code boundaries; Foundry
provides more control and therefore requires stronger explicit
governance.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Define data, tool, behavior, environment, and operational
    boundaries.
-   Separate knowledge access from action permission.
-   Require approval for high-impact decisions/actions.
-   Scope connectors and identities using least privilege.
-   Apply evaluation, monitoring, and audit requirements before
    production.

### Architecture Diagram

``` text
AI component
 ├─ Data boundaries
 ├─ Tool/action permissions
 ├─ Behavior rules
 ├─ Human approval
 ├─ Identity/access
 ├─ Environment/network
 ├─ Evaluation
 └─ Operations
        ↓
   Bounded AI behavior
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: Why define constraints?**\
**Expected answer:** To make AI behavior secure, compliant, predictable,
and bounded.

**Q: What should tool permissions control?**\
**Expected answer:** Which actions the agent can invoke, against which
systems, with which identity and approval model.

**Q: Why is Foundry governance heavier?**\
**Expected answer:** Greater control also creates greater responsibility
for models, tools, memory, evaluation, monitoring, and scaling.

**Q: Give an example of a human-approval rule.**\
**Expected answer:** An agent may recommend a refund but an authorized
employee must approve the actual financial action.

------------------------------------------------------------------------

## Topic 7 --- Determine generative AI knowledge sources for agents built in Copilot Studio

### Concept

Copilot Studio generative AI can combine foundation-model reasoning with
enterprise knowledge retrieval. The architect must select authoritative
sources, control access, understand orchestration, and test retrieval
quality.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Evaluate authority, relevance, freshness, ownership, and permissions
    of every source.
-   Typical sources include SharePoint, Dataverse, OneDrive, websites,
    files, Azure AI Search, and connectors depending on environment.
-   Understand classic topic routing versus generative orchestration.
-   Test both in-domain and out-of-domain questions.
-   Knowledge retrieval must never become a permissions bypass.

### Architecture Diagram

``` text
User question
   ↓
Copilot Studio
   ↓
Generative orchestration
   ↓
Knowledge selection
   ↓
Permissions / authentication
   ↓
Relevant retrieval
   ↓
Grounded context
   ↓
Generated answer
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What is the purpose of a knowledge source?**\
**Expected answer:** To provide authoritative context that grounds the
agent's answer.

**Q: What makes a source suitable?**\
**Expected answer:** It is authoritative, relevant, sufficiently
current, accessible to intended users, and governed.

**Q: What does generative orchestration do?**\
**Expected answer:** It can dynamically select relevant topics, tools,
connected agents, and knowledge based on the request.

**Q: What is the main security principle?**\
**Expected answer:** Retrieval must respect identity and authorization
boundaries.

------------------------------------------------------------------------

## Topic 8 --- Determine when to build custom agents or extend Microsoft 365 Copilot

### Concept

Extend Microsoft 365 Copilot when most required capability already
exists in the Microsoft 365 productivity experience and customization is
simple. Build a custom agent when specialized workflows, complex
orchestration, external systems, autonomy, or multi-agent behavior are
required.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Inventory existing Copilot capability first.
-   Identify the exact gap: knowledge, connector, action, orchestration,
    autonomy, or external execution.
-   Compare complexity and lifecycle cost, not just development speed.
-   Keep productivity scenarios in the M365 experience when practical.
-   Document the boundary where custom runtime/control becomes
    necessary.

### Architecture Diagram

``` text
Business requirement
      ↓
Does M365 Copilot solve most of it?
 ├─ Yes → Extend
 │        ├─ knowledge
 │        ├─ connector/plugin
 │        └─ simple behavior
 └─ No
      ↓
Custom workflow / external system / autonomy?
      ↓
Custom agent
      ↓
Copilot Studio or Foundry
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: When should you extend Copilot?**\
**Expected answer:** When the scenario is mainly Microsoft 365
productivity and only simple customization is required.

**Q: When should you build custom?**\
**Expected answer:** When specialized workflows, complex orchestration,
external systems, autonomy, or multi-agent behavior are required.

**Q: Why not custom-build everything?**\
**Expected answer:** Custom solutions add complexity, cost, security
responsibility, and lifecycle overhead.

**Q: What is the key decision question?**\
**Expected answer:** Can the required business capability remain within
the Microsoft 365 Copilot and extension model?

------------------------------------------------------------------------

## Topic 9 --- Determine when custom AI models should be created

### Concept

Custom model development is a strategic exception. First test catalog
models, prompting, retrieval, and other available options. Consider
custom models when domain specificity, high accuracy, predictability,
strict governance, or high-volume economics justify the investment.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Use the five-fit test: business, model, data, cost, operational.
-   Measure actual accuracy gaps instead of assuming customization is
    better.
-   Check prompt engineering, retrieval tuning, stronger catalog models,
    and fine-tuning first.
-   Custom models require curated data, evaluation, deployment
    pipelines, monitoring, and skills.
-   Use ROI to justify long-term engineering and operating cost.

### Architecture Diagram

``` text
Requirement
   ↓
Catalog model
   ↓
Prompting + RAG + evaluation
   ↓
Meets target?
 ├─ Yes → Keep existing approach
 └─ No
      ↓
Business + Model + Data + Cost + Operations fit
      ↓
Custom model decision
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: When is a custom model justified?**\
**Expected answer:** When existing approaches cannot meet the
requirement and the business, data, governance, cost, and operational
case supports customization.

**Q: What should be tried first?**\
**Expected answer:** Catalog models, prompt engineering, retrieval, and
other available customization.

**Q: What data is needed?**\
**Expected answer:** High-quality curated domain data plus repeatable
training, evaluation, and deployment processes.

**Q: What five dimensions should be balanced?**\
**Expected answer:** Business fit, model fit, data fit, cost fit, and
operational fit.

------------------------------------------------------------------------

## Topic 10 --- Provide guidelines for creating a prompt library

### Concept

A prompt library is a curated and governed collection of reusable
prompts. Microsoft Learn emphasizes clarity, context, constraints, and
output format, plus metadata, review, testing, versioning, and lifecycle
management.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Capture purpose, owner, version, update date, applicable systems,
    risk classification, and required grounding sources.
-   Use patterns such as instruction + context + output, few-shot
    examples, role prompting, and multi-step prompts.
-   Test multiple inputs, edge cases, and model versions.
-   Review with domain experts and security/compliance where
    appropriate.
-   Retire prompts when business rules or models change.

### Architecture Diagram

``` text
Prompt candidate
   ↓
Domain review
   ↓
Security / Responsible AI review
   ↓
Test + evaluate
   ↓
Approve
   ↓
Prompt library
   ↓
Version / monitor / retire
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What are the four core prompt pillars?**\
**Expected answer:** Clarity, context, constraints, and output format.

**Q: What metadata belongs in the library?**\
**Expected answer:** Purpose, owner, version, update date, systems, risk
classification, and grounding sources.

**Q: Why version prompts?**\
**Expected answer:** Prompt behavior changes as business rules, models,
and workflows change.

**Q: What makes a prompt an enterprise asset?**\
**Expected answer:** Ownership, governance, testing, versioning, reuse,
and lifecycle management.

------------------------------------------------------------------------

## Topic 11 --- Develop use cases for customized small language models

### Concept

Customized Small Language Models can fit focused workloads where low
latency, lower cost, small footprint, edge deployment, or specialized
behavior matters. They are not automatically safer or more accurate than
larger models.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Consider manufacturing troubleshooting, focused classification,
    compliance analysis, and edge/IoT workloads.
-   Customization can target domain knowledge, behavior, or a specific
    task.
-   Use SLMs where high-volume inference makes cost and latency
    important.
-   Avoid an SLM when RAG over a general model already satisfies the
    requirement.
-   Evaluate overfitting, edge cases, safety, drift, and data-curation
    effort.

### Architecture Diagram

``` text
Focused task
   ↓
Curated domain data
   ↓
Customized SLM
   ↓
Safety + evaluation
   ↓
Business app / agent / edge device
   ↓
Accuracy + latency + cost + safety + drift
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: When is an SLM a strong candidate?**\
**Expected answer:** When a specialized workload benefits from low
latency, low cost, small footprint, edge deployment, or domain-specific
behavior.

**Q: What is a key anti-pattern?**\
**Expected answer:** Building a custom SLM when RAG over a general model
would be sufficient.

**Q: Does an SLM automatically reduce incorrect information?**\
**Expected answer:** No; it still requires good data, grounding,
evaluation, and governance.

**Q: What metrics matter?**\
**Expected answer:** Task accuracy, latency, cost per 1,000 requests,
safety incidents, and drift.

------------------------------------------------------------------------

## Topic 12 --- Provide prompt engineering guidelines and techniques

### Concept

Prompt engineering is deliberate instruction design that guides AI
toward reliable, safe, business-aligned outputs. In enterprise
solutions, prompt design affects downstream process quality and
governance.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Use clear, specific, actionable instructions.
-   Provide purpose, audience, source/reference material, and
    exclusions.
-   Specify tables, bullets, JSON, or other output formats when needed.
-   Use constraints to reduce unsafe or unsupported behavior.
-   Refine prompts iteratively and measure accuracy, completeness,
    consistency, and compliance.

### Architecture Diagram

``` text
Role / purpose
      +
Task
      +
Business context
      +
Reference data
      +
Constraints
      +
Output format
      +
Validation
      ↓
AI output
      ↓
Review → refine → retest
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What is prompt engineering?**\
**Expected answer:** Deliberate design of instructions that guide an AI
model toward a required business output.

**Q: Why specify output format?**\
**Expected answer:** It improves consistency and reduces downstream
editing.

**Q: Why include constraints?**\
**Expected answer:** They keep the model within business, data, and
compliance boundaries.

**Q: How should production prompts improve?**\
**Expected answer:** Use an iterative review, refine, retest, and KPI
evaluation cycle.

------------------------------------------------------------------------

## Topic 13 --- Identify key business user roles for AI workloads

### Concept

AI workloads require clear business and technical accountability.
Microsoft Learn highlights executive sponsor, AI CoE lead, and AI
product owner roles, supported by architecture, data, security,
compliance, engineering, operations, and business SMEs.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   The executive sponsor provides strategic direction, funding, and
    organizational support.
-   The AI CoE lead coordinates strategy, governance, standards, and
    cross-functional alignment.
-   The product owner owns the business outcome, roadmap, budget, and
    acceptance criteria.
-   Assign data and knowledge ownership explicitly.
-   Assign operational ownership before production.

### Architecture Diagram

``` text
Executive Sponsor
      ↓
AI CoE Lead
      ↓
AI Product Owner
      ↓
Architect ─ Data ─ Security/Compliance
      ↓
Engineering / Operations
      ↓
SMEs / Users / AI Champions
      ↓
Business outcome
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: Who owns the business outcome?**\
**Expected answer:** The accountable AI product owner or business owner.

**Q: What does the executive sponsor provide?**\
**Expected answer:** Strategic direction, funding, organizational
support, and governance/risk sponsorship.

**Q: What does the AI CoE lead coordinate?**\
**Expected answer:** AI strategy, governance, standards, collaboration,
and maturity.

**Q: Why define roles early?**\
**Expected answer:** To prevent fragmented solutions, unclear
accountability, stalled adoption, and lifecycle gaps.

------------------------------------------------------------------------

## Topic 14 --- Evaluate regional and local AI data regulation compliance requirements

### Concept

AI workloads can be affected by privacy, AI-specific, industry,
cross-border, transparency, human-oversight, and documentation
requirements. The architect must identify jurisdictions and map
confirmed requirements to technical controls.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Identify where users, data, systems, and processing occur.
-   Classify data and determine applicable privacy/lawful-processing
    requirements.
-   Evaluate cross-border transfer and residency constraints.
-   Assess AI-specific risk classification, transparency, human
    oversight, documentation, and safety.
-   Work with legal/privacy/security stakeholders; translate
    requirements into architecture controls.

### Architecture Diagram

``` text
Business use case
   ↓
Data classification
   ↓
Jurisdictions
   ↓
Applicable requirements
   ↓
Technical / governance controls
 ├─ data location
 ├─ access
 ├─ retention
 ├─ human oversight
 ├─ transparency
 └─ audit evidence
   ↓
Compliance readiness decision
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: Why evaluate regulation early?**\
**Expected answer:** Regulatory requirements can change data, platform,
hosting, access, and workflow architecture.

**Q: What should be identified first?**\
**Expected answer:** Jurisdictions, data types, processing activities,
users, and business impact.

**Q: What domains should be evaluated?**\
**Expected answer:** Privacy, AI-specific regulation, industry
compliance, cross-border transfer, transparency, human oversight, and
documentation.

**Q: Can one global control set always be assumed?**\
**Expected answer:** No; regional and local requirements must be
evaluated for the actual workload.

------------------------------------------------------------------------

## Topic 15 --- Include elements in a Microsoft AI Center of Excellence

### Concept

An AI Center of Excellence is an organizational capability that
accelerates responsible AI adoption, standardizes practices, provides
expertise, and governs the portfolio. It should enable teams rather than
become a bottleneck.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Secure executive sponsorship and a clear mandate.
-   Assign accountable CoE leadership.
-   Include AI strategy, data, engineering, governance, security,
    operations, and business expertise.
-   Maintain reusable standards, templates, reference architectures,
    prompts, and evaluation patterns.
-   Use portfolio oversight to reduce duplication and ungoverned
    adoption.

### Architecture Diagram

``` text
Executive leadership
      ↓
     AI CoE
 ┌────┼────┬────┬────┐
 ↓    ↓    ↓    ↓    ↓
Strategy Data Security Governance Operations
      ↓
Standards + reusable assets
      ↓
AI portfolio
      ↓
Delivery + operations
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What is the purpose of an AI CoE?**\
**Expected answer:** To scale AI responsibly through governance,
standards, expertise, reusable assets, and business alignment.

**Q: Why is executive sponsorship important?**\
**Expected answer:** It provides funding, strategic direction,
authority, and organizational support.

**Q: Who belongs in the multidisciplinary team?**\
**Expected answer:** Strategy, data, AI/ML engineering, governance,
security, operations, and business SMEs.

**Q: How does the CoE reduce duplication?**\
**Expected answer:** Through shared standards, reusable assets,
architecture guidance, and portfolio oversight.

------------------------------------------------------------------------

## Topic 16 --- Design AI solutions using multiple Dynamics 365 apps

### Concept

AI across Dynamics 365 applications must preserve shared business
context and process continuity. Architects should design around governed
business objects, consistent schemas, integration boundaries, events,
and persistent context.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Identify the long-lived business object carrying context.
-   Use harmonized Dataverse tables and consistent entity schemas where
    applicable.
-   Use clean integration boundaries and event-driven flows for state
    changes.
-   Design for users continuing work across application surfaces.
-   Ground AI on authoritative sources to prevent cross-app drift.

### Architecture Diagram

``` text
Customer / Opportunity
       ↓
     Sales
       ↓
     Order
       ↓
Customer Service
       ↓
    Finance
       ↓
 Field Service
       ↓
 Shared AI context
       ↓
Consistent user experience
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: What is the key requirement?**\
**Expected answer:** Consistent and authoritative business context
across application boundaries.

**Q: Why are harmonized schemas important?**\
**Expected answer:** They let applications and AI interpret business
entities consistently.

**Q: Why does process continuity matter?**\
**Expected answer:** Users should continue work across applications
without losing relevant context.

**Q: What should anchor long-lived context?**\
**Expected answer:** Governed business objects such as customer,
opportunity, order, case, asset, or work order.

------------------------------------------------------------------------

## Topic 17 --- Design user prompt training for AI solution adoption

### Concept

AI adoption succeeds when users know how to prompt, validate outputs,
use AI responsibly, and integrate it into their workflow. Training
should be persona-based and include accessibility and governance.

### Architecture Perspective

The architect must translate this topic into an explicit design
decision. The question is not only "Can the technology do it?" but also
"What business, data, security, governance, operating, and adoption
conditions make the design appropriate?"

### Architect Pointers

-   Identify personas before designing training.
-   Teach everyday users basic prompting, validation, limitations, and
    responsible use.
-   Teach AI champions advanced prompts, reusable templates, workflows,
    and peer coaching.
-   Teach managers how to review AI insights and monitor
    outcomes/governance.
-   Include accessibility and inclusive design in training.

### Architecture Diagram

``` text
User persona
      ↓
Role-specific training
 ├─ Everyday user → basic prompting + validation
 ├─ AI champion → advanced prompts + coaching
 ├─ Manager → review + governance + outcomes
 └─ Accessibility-focused user → inclusive AI features
      ↓
Workflow adoption
      ↓
Usage + outcome measurement
      ↓
Continuous improvement
```

### Decision Points

-   Identify the business requirement and measurable outcome.
-   Identify the data, knowledge, tools, and integrations required.
-   Identify security, compliance, ownership, and human-approval
    boundaries.
-   Select the simplest Microsoft capability that satisfies the
    requirement.
-   Define evaluation and operational measures before production.

### Architect Questions and Expected Answers

**Q: Why is prompt training part of adoption?**\
**Expected answer:** Because user behavior directly affects quality,
productivity, responsible use, and business outcomes.

**Q: Should every user receive the same training?**\
**Expected answer:** No; training should match persona, workflow,
responsibility, and AI maturity.

**Q: What should managers learn?**\
**Expected answer:** Output review, governance boundaries, usage
monitoring, and outcome measurement.

**Q: What should AI champions learn?**\
**Expected answer:** Advanced prompting, reusable templates, multi-step
workflows, and peer coaching.

------------------------------------------------------------------------

# Module 3 --- Final Architect Whiteboard

``` text
Business Outcomes
      ↓
AI Use Cases
      ↓
CAF / AI Adoption Plan
      ↓
Agent Technology Decision
      ↓
Prebuilt / Copilot Studio / Foundry / Custom
      ↓
Data + Knowledge
      ↓
Rules + Guardrails
      ↓
Prompts + Models + Tools
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
**Expected answer:** Business outcome → use case → adoption → platform →
data → guardrails → operations → adoption measurement.

**Q: When should an architect choose a prebuilt solution?**\
**Expected answer:** When it already meets the business requirement with
acceptable customization, governance, and operational fit.

**Q: When is multi-agent architecture justified?**\
**Expected answer:** When security boundaries, independent ownership,
modular specialization, or dependent workstreams justify the added
complexity.

**Q: When should custom models be considered?**\
**Expected answer:** When existing approaches cannot meet the
requirement and business, data, cost, governance, and operational fit
justify customization.

**Q: What makes a prompt an enterprise asset?**\
**Expected answer:** Ownership, versioning, risk classification,
grounding requirements, testing, approval, and lifecycle management.

**Q: What makes an AI CoE effective?**\
**Expected answer:** Executive sponsorship, accountable leadership,
multidisciplinary expertise, governance, standards, reusable assets,
portfolio oversight, and operational support.

**Q: What makes an AI strategy enterprise-ready?**\
**Expected answer:** Clear business value, appropriate technology,
governed data, explicit constraints, accountable roles, compliance,
operations, and user adoption.

## Microsoft Learn Alignment

The current Microsoft Learn module contains 19 units: 17 learning topics
plus assessment and summary. Its stated objectives include mapping CAF
AI adoption phases to the AI agent lifecycle, designing an
enterprise-ready operating model, selecting Microsoft AI platforms, and
transitioning AI workloads from proof of concept to production.
citeturn0search0

Primary module:\
https://learn.microsoft.com/en-us/training/modules/design-overall-ai-strategy-business-solutions/
