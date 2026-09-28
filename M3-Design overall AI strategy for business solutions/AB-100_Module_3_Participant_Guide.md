# AB-100 Module 3 — Design Overall AI Strategy for Business Solutions

## Module Goal

This module focuses on how a solution architect designs an overall AI strategy for business solutions.

The main idea is:

> Start with the business outcome, choose the simplest suitable AI capability, design the agent and data architecture, apply security and governance, and then drive user adoption.

---

# Module Architecture Story

```text
                    BUSINESS STRATEGY
                           |
                           v
                 Identify AI Use Cases
                           |
                           v
                 Choose Agent Approach
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
     M365 Copilot    Copilot Studio    Microsoft Foundry
          |                |                |
          +----------------+----------------+
                           |
                           v
                    Agent Architecture
                           |
                  +--------+--------+
                  |                 |
             Single Agent      Multi-Agent
                  |                 |
                  +--------+--------+
                           |
                           v
                 Knowledge + Data
                           |
                           v
                  Rules + Guardrails
                           |
                           v
                 Models + Prompts
                           |
                           v
              Security + Compliance
                           |
                           v
                  AI CoE + Roles
                           |
                           v
              Business Applications
                           |
                           v
                    User Adoption
                           |
                           v
                    Business Value
```

---

# Topic 1 — Introduction

## Concept

The architect's job is not simply to select an AI product.

The architect needs to answer:

> How can the organization adopt AI in a controlled way that creates business value?

The module connects the Cloud Adoption Framework (CAF) with the AI agent lifecycle.

A useful lifecycle is:

```text
Business Outcome
       |
       v
AI Strategy
       |
       v
Plan Agents
       |
       v
Govern + Secure
       |
       v
Build Agents
       |
       v
Operate Agents
       |
       v
Measure Business Value
```

## Architecture

```text
+-----------------------+
| Business Strategy     |
+-----------+-----------+
            |
            v
+-----------------------+
| AI Strategy           |
| Use Cases + ROI       |
+-----------+-----------+
            |
            v
+-----------------------+
| Platform Selection    |
| Copilot / Studio /    |
| Foundry / Azure       |
+-----------+-----------+
            |
            v
+-----------------------+
| Data + Knowledge      |
+-----------+-----------+
            |
            v
+-----------------------+
| Security + Governance |
+-----------+-----------+
            |
            v
+-----------------------+
| Build + Deploy        |
+-----------+-----------+
            |
            v
+-----------------------+
| Operate + Monitor     |
+-----------------------+
```

## Architect Perspective

Before choosing technology, ask:

- What business problem are we solving?
- Is AI actually required?
- Should this be an agent?
- Which platform fits?
- What data does it need?
- What actions can it perform?
- What security boundaries are required?
- How will we govern and monitor it?

## Architect Questions

**Q: What should the architect start with?**  
Expected answer: The business outcome and business requirement.

**Q: Should the architect start by selecting an AI product?**  
Expected answer: No. Start with the business problem, outcome, requirements, data, and constraints.

## Key Takeaway

**AI strategy starts with business outcomes, not with an AI product.**

---

# Topic 2 — Implement AI Adoption Process with Azure

## Concept

This topic connects the Cloud Adoption Framework with the AI agent lifecycle.

Think of CAF as:

> How does an enterprise safely adopt technology?

Think of the agent lifecycle as:

> How do we safely build, govern, and operate AI agents?

The architect connects the two.

## Architecture

```text
              CLOUD ADOPTION FRAMEWORK
              -------------------------

 Strategy ---------------------> Plan Agents
    |                                  |
    v                                  v
  Plan --------------------------> Plan Agents
    |
    v
  Ready -------------------------> Governance
    |                                  |
    v                                  v
 Govern -------------------------> Security
    |
    v
 Secure -------------------------> Security
    |
    v
 Adopt --------------------------> Build Agents
    |
    v
 Manage -------------------------> Operate Agents
```

## Important Architect Outputs

Think in terms of:

- AI strategy
- Agent technology plan
- AI adoption plan
- Proof-of-concept assessment
- Agent readiness assessment
- AI landing zones
- Governance policies
- Data access model
- Agent templates
- Evaluation gates
- Monitoring and operational baselines

## Architect Perspective

The architect should make sure AI is treated as an enterprise capability rather than as a collection of disconnected experiments.

## Architect Questions

**Q: Why combine CAF with the agent lifecycle?**  
Expected answer: To apply enterprise strategy, governance, security, and operations to AI agents.

**Q: What should happen before building an agent?**  
Expected answer: Define the business outcome, use case, platform choice, data requirements, governance, and success metrics.

## Key Takeaway

**CAF gives the enterprise foundation; the agent lifecycle tells us how to build and operate agents on that foundation.**

---

# Topic 3 — Design Strategy for Building AI Agents

## Concept

The architect must decide:

> Should we use an existing SaaS agent, Copilot Studio, Microsoft Foundry, or another custom approach?

Start with the simplest option that satisfies the requirement.

## Architecture

```text
Business Requirement
        |
        v
Does Microsoft 365 Copilot
meet the requirement?
     /          \
   YES           NO
    |             |
    v             v
Use Copilot   Can Copilot Studio
             meet requirement?
                  /      \
                YES       NO
                 |         |
                 v         v
          Copilot Studio  Foundry
                            |
                            v
                     Custom / Pro-code
```

## Platform Decision

### Microsoft 365 Copilot / SaaS

Good when:

- The requirement fits existing productivity capabilities.
- Little customization is needed.
- Users work primarily inside Microsoft 365.

### Copilot Studio

Good when:

- You need business-specific agents.
- Low-code development is preferred.
- You need connectors and business actions.
- Business teams need to participate in agent creation.

### Microsoft Foundry

Good when:

- Complex orchestration is required.
- Custom logic is required.
- Multiple agents need to cooperate.
- Enterprise systems need deeper integration.

### Custom Model / Pro-Code

Consider when:

- Very specific model behavior is required.
- Strong isolation or specialized requirements exist.
- Existing models and platforms cannot meet the requirement.

## Architect Perspective

Do not choose the most powerful platform just because it is available.

Choose the simplest platform that satisfies:

- Business requirement
- Security
- Data requirements
- Integration requirements
- Scalability
- Governance
- Cost and operational requirements

## Architect Questions

**Q: What should the architect try first?**  
Expected answer: An existing Microsoft capability that already satisfies the requirement.

**Q: When should the solution become more customized?**  
Expected answer: When the business requirement cannot be adequately met by existing capabilities.

## Key Takeaway

**Start with the simplest suitable agent platform and increase customization only when the requirement demands it.**

---

# Topic 4 — Design a Multi-Agent Solution

## Concept

A multi-agent architecture means that several specialized agents perform different responsibilities instead of one agent doing everything.

Start simple. Introduce multiple agents when specialization, ownership, security boundaries, or workflow complexity justify it.

## Single-Agent Architecture

```text
User
 |
 v
+------------------+
| Single Agent     |
|                  |
| Sales            |
| Support          |
| Finance          |
| Knowledge        |
+------------------+
```

## Multi-Agent Architecture

```text
                         User
                           |
                           v
                  +----------------+
                  | Orchestrator   |
                  +-------+--------+
                          |
          +---------------+---------------+
          |               |               |
          v               v               v
   +-------------+ +-------------+ +-------------+
   | Sales Agent | | Support     | | Finance     |
   |             | | Agent       | | Agent       |
   +-------------+ +-------------+ +-------------+
          |               |               |
          v               v               v
       CRM             Service          ERP
```

## When Multi-Agent Makes Sense

Use it when:

- Responsibilities are clearly different.
- Different teams own different domains.
- Security boundaries differ.
- Specialized tools are required.
- The workflow crosses multiple domains.
- A single agent becomes too complex.

Avoid multi-agent when one agent can perform the job effectively.

## Trade-Offs

```text
Multi-Agent
     |
     +--> More specialization
     +--> Separation of responsibilities
     +--> Independent scaling
     |
     +--> More orchestration
     +--> More latency
     +--> More security surface
     +--> More operational complexity
```

## Architect Questions

**Q: Should every solution use multiple agents?**  
Expected answer: No. Start with a single agent and introduce multiple agents when justified.

**Q: Why use multiple agents?**  
Expected answer: To separate specialized responsibilities, domains, ownership, tools, or security boundaries.

## Key Takeaway

**Use one agent by default; introduce multiple agents when specialization or organizational boundaries justify the added complexity.**

---

# Topic 5 — Develop Use Cases for Prebuilt Microsoft 365 Copilot Agents

## Concept

Prebuilt Microsoft 365 Copilot capabilities already support many common employee tasks.

Examples include:

- Summarizing documents
- Summarizing email or chats
- Finding organizational information
- Drafting communications
- Providing policy-based guidance

The architect should first ask:

> Can the business requirement already be handled by a prebuilt Microsoft capability?

## Architecture

```text
Employee
   |
   v
Microsoft 365 Copilot
   |
   +---- Outlook
   |
   +---- Teams
   |
   +---- Word
   |
   +---- Excel
   |
   +---- SharePoint
   |
   v
Business Knowledge
   |
   v
Productivity Outcome
```

## Business Example

```text
Customer Email
      |
      v
M365 Copilot
      |
      v
Summarize Issue
      |
      v
Identify Customer Need
      |
      v
Employee Reviews
```

## Architect Perspective

If the existing capability satisfies the requirement, avoid unnecessary custom development.

## Architect Questions

**Q: Why consider a prebuilt agent first?**  
Expected answer: It can provide business value with less development and operational complexity.

**Q: When should a custom solution be considered?**  
Expected answer: When the prebuilt capability cannot satisfy the business requirement.

## Key Takeaway

**Use prebuilt Microsoft 365 capabilities where they already satisfy the business requirement.**

---

# Topic 6 — Define Solution Rules and Constraints for AI Components

## Concept

AI should not have unlimited freedom.

The architect defines:

- What data AI can access.
- What tools AI can use.
- What actions AI can perform.
- What environment it can run in.
- What networking restrictions apply.
- What security controls apply.
- What behavior is allowed.

## Architecture

```text
                    AI Agent
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Data         Tools         Actions
          |            |            |
          +------------+------------+
                       |
                 RULES / GUARDRAILS
                       |
        +--------------+--------------+
        |              |              |
     Security       Compliance     Operations
        |              |              |
        +--------------+--------------+
                       |
                       v
                 Business Result
```

## Example

An agent may be allowed to:

```text
READ customer record
        |
        v
ANALYZE issue
        |
        v
DRAFT response
```

But it should not automatically be allowed to:

```text
DELETE customer
      X

APPROVE refund above limit
      X

ACCESS payroll data
      X
```

unless those capabilities are explicitly authorized.

## Architect Perspective

Rules should be defined before deployment, not after an agent causes an unexpected action.

## Architect Questions

**Q: Why are rules and constraints important?**  
Expected answer: They limit AI behavior and protect data, systems, users, and the organization.

**Q: What should an architect control?**  
Expected answer: Data access, tools, actions, permissions, environment, networking, security, and operational boundaries.

## Key Takeaway

**The architect defines the boundaries within which the AI is allowed to operate.**

---

# Topic 7 — Determine Generative AI Knowledge Sources for Copilot Studio

## Concept

An agent becomes more useful when it has access to trusted enterprise knowledge.

Potential sources include:

- SharePoint
- Dataverse
- OneDrive
- Websites
- Azure AI Search
- Other enterprise data sources

The important idea is:

> The model provides reasoning; enterprise knowledge provides business context.

## Architecture

```text
                 User Question
                       |
                       v
               Copilot Studio Agent
                       |
                       v
                Knowledge Search
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
   SharePoint      Dataverse       Azure AI Search
        |              |              |
        +--------------+--------------+
                       |
                       v
                Relevant Context
                       |
                       v
                Generative AI
                       |
                       v
                  Answer
```

## Architect Checks

Before selecting a knowledge source, ask:

- Is it authoritative?
- Is it current?
- Is it relevant?
- Can users access it?
- Is authentication configured?
- Is sensitive information protected?
- Is retrieval quality sufficient?

## Architect Questions

**Q: Why is knowledge source selection important?**  
Expected answer: The agent needs trusted and relevant business information to provide useful answers.

**Q: Can an agent simply access all enterprise data?**  
Expected answer: No. Access must respect identity, permissions, security, and compliance requirements.

## Key Takeaway

**Good agent answers depend on good, accessible, governed knowledge.**

---

# Topic 8 — Determine When to Build Custom Agents or Extend Microsoft 365 Copilot

## Concept

The architect needs to decide whether to extend Microsoft 365 Copilot or build a separate custom agent.

## Decision Architecture

```text
Business Requirement
        |
        v
Existing M365 Copilot?
       /       \
     YES        NO
      |          |
      v          v
Can extension   Custom Agent
solve it?
   /    \
 YES     NO
  |       |
  v       v
Extend   Custom
Copilot  Agent
```

## Extend Copilot When

- Existing Copilot capability is close to the requirement.
- The scenario is primarily Microsoft 365 productivity.
- Organizational knowledge is the main extension.
- Only simple actions or integrations are needed.

## Build Custom Agent When

- The workflow is substantially different.
- Complex business logic is required.
- Multiple systems must be orchestrated.
- Specialized autonomous behavior is required.
- Custom interaction patterns are needed.

## Architect Questions

**Q: When should you extend Microsoft 365 Copilot?**  
Expected answer: When existing Copilot capabilities already provide most of the required experience and only targeted extensions are needed.

**Q: When should you build a custom agent?**  
Expected answer: When the business workflow requires capabilities, logic, orchestration, or interaction patterns beyond what Copilot can provide.

## Key Takeaway

**Extend before rebuilding when existing Copilot already provides the required foundation.**

---

# Topic 9 — Determine When Custom AI Models Should Be Created

## Concept

A custom model is a major architectural decision.

Consider a custom model when existing pretrained or adaptable models cannot adequately solve the business requirement, or when strong domain-specific requirements justify the additional investment.

## Decision Architecture

```text
Business Problem
       |
       v
Can existing model solve it?
       /          \
     YES           NO
      |             |
      v             v
Use Existing     Can fine-tuning
Model            solve it?
                    /   \
                  YES    NO
                   |      |
                   v      v
              Fine-tune  Custom Model
```

## Decision Dimensions

```text
Business Fit
     +
Model Fit
     +
Data Fit
     +
Cost Fit
     +
Operational Fit
```

## Why Not Build Custom Models by Default?

Custom models introduce:

- More engineering
- More data requirements
- More infrastructure
- More maintenance
- More operational complexity
- Longer time to value

## Architect Questions

**Q: What should be evaluated before creating a custom model?**  
Expected answer: Whether existing models can meet the requirement, along with business fit, data availability, cost, governance, and operational requirements.

**Q: Why avoid unnecessary custom models?**  
Expected answer: They increase engineering, infrastructure, maintenance, and operational complexity.

## Key Takeaway

**A custom model should solve a requirement that existing models cannot economically and safely satisfy.**

---

# Topic 10 — Provide Guidelines for Creating a Prompt Library

## Concept

A prompt library is:

> A governed collection of tested and reusable prompts.

Instead of every employee creating prompts from scratch:

```text
                    Prompt Library
                         |
        +----------------+----------------+
        |                |                |
        v                v                v
 Customer Service     Sales           Finance
 Prompt               Prompt          Prompt
        |                |                |
        v                v                v
   Tested            Tested           Tested
   Approved          Approved         Approved
```

A prompt library improves:

- Consistency
- Governance
- Efficiency
- Quality
- Reusability
- Scalability

## Prompt Structure

```text
Role
 +
Task
 +
Context
 +
Constraints
 +
Expected Output
 +
Quality Criteria
```

## Example

Instead of:

> Summarize this customer issue.

Use:

```text
Role:
You are a customer-service analyst.

Task:
Summarize the customer issue.

Context:
Use the supplied customer communication.

Constraints:
Do not invent information.

Output:
1. Customer issue
2. Product
3. Symptoms
4. Recommended next step
```

## Architect Questions

**Q: Why create a prompt library?**  
Expected answer: To provide tested, reusable, consistent, and governed prompts.

**Q: What should a reusable prompt define?**  
Expected answer: Role, task, context, constraints, expected output, and quality criteria.

## Key Takeaway

**A prompt library turns individual prompting into a governed enterprise capability.**

---

# Topic 11 — Develop Use Cases for Customized Small Language Models

## Concept

A Small Language Model (SLM) is a smaller generative model designed for specific requirements.

Potential benefits include:

- Lower latency
- Lower cost
- Domain specialization
- More efficient inference
- Deployment in constrained environments

## Architecture

```text
                 AI Requirement
                       |
                       v
          Need very low latency?
                       |
          +------------+------------+
          |                         |
         YES                        NO
          |                         |
          v                         v
     Consider SLM              Large Model
          |
          v
 Domain-specific data
          |
          v
 Customized SLM
          |
          v
 Fast / Efficient Inference
```

## Example

```text
Factory Device
      |
      v
Local SLM
      |
      v
Equipment Classification
      |
      v
Immediate Response
```

## Architect Perspective

A smaller model is not automatically safer or more accurate. Model selection still requires evaluation against business requirements.

## Architect Questions

**Q: When is an SLM useful?**  
Expected answer: When latency, cost, deployment constraints, or domain specialization make a smaller model appropriate.

**Q: Does a smaller model automatically remove AI risks?**  
Expected answer: No. It still needs evaluation, security, governance, and quality controls.

## Key Takeaway

**Use an SLM when latency, cost, deployment constraints, or domain specialization make a smaller model a better fit.**

---

# Topic 12 — Provide Prompt Engineering Guidelines and Techniques

## Concept

Prompt engineering means designing instructions so the AI produces a useful and predictable result.

Good prompts provide:

- Clear instructions
- Relevant context
- Constraints
- Expected output
- Business context
- Validation requirements

## Architecture

```text
User / Application
       |
       v
     Prompt
       |
       +---- Role
       +---- Task
       +---- Context
       +---- Constraints
       +---- Examples
       +---- Output Format
       |
       v
      Model
       |
       v
   AI Response
       |
       v
 Validation / Human Review
```

## Poor Prompt

```text
"Analyze this."
```

## Better Prompt

```text
You are a financial analyst.

Analyze the supplied sales data.

Identify:
- Revenue trend
- Major changes
- Outliers

Do not invent missing values.

Return:
1. Findings
2. Evidence
3. Recommended follow-up
```

## Architect Perspective

Prompt design should be considered part of solution design when prompts influence business outcomes.

## Architect Questions

**Q: What makes a prompt more reliable?**  
Expected answer: Clear task, context, constraints, examples where useful, and a defined output format.

**Q: Should users trust every AI response without validation?**  
Expected answer: No. AI output should be validated according to the business risk and use case.

## Key Takeaway

**Good prompts provide the model with clear instructions, useful context, and controlled output expectations.**

---

# Topic 13 — Identify Key Business User Roles for AI Workloads

## Concept

AI adoption is not only a technology problem.

Different people have different responsibilities.

Typical roles include:

- Executive sponsor
- Business owner
- AI Center of Excellence
- Solution architect
- Security and compliance
- AI delivery team
- Business users

## Architecture

```text
                 Executive Sponsor
                       |
                       v
                  AI CoE Lead
                       |
       +---------------+---------------+
       |               |               |
       v               v               v
   Business        Solution         Security /
    Owner          Architect        Compliance
       |               |               |
       +---------------+---------------+
                       |
                       v
                 AI Delivery Team
                       |
                       v
                 Business Users
```

## Role Responsibilities

### Executive Sponsor

Owns:

- Business direction
- Funding
- Strategic alignment
- Organizational change

### Business Owner

Owns:

- Business requirements
- KPIs
- Process outcomes

### Solution Architect

Owns:

- Architecture
- Technology decisions
- Integration
- Security and scalability decisions

### AI CoE

Owns:

- Standards
- Governance
- Reusable practices
- AI adoption support

### Security / Compliance

Owns:

- Risk
- Security
- Compliance
- Regulatory controls

## Architect Questions

**Q: Why are roles important?**  
Expected answer: Clear ownership prevents gaps in business, architecture, security, governance, and adoption responsibilities.

**Q: Who owns business outcomes?**  
Expected answer: The business owner or business leadership, supported by the solution and AI teams.

## Key Takeaway

**Successful AI architecture requires clear ownership across business, technology, security, and governance.**

---

# Topic 14 — Evaluate Regional and Local AI Data Regulation Compliance

## Concept

AI solutions can operate across countries and regions.

The architect must understand:

```text
Where is the data?
        |
        v
Where is the AI workload?
        |
        v
Who can access it?
        |
        v
Where is data processed?
        |
        v
Can data cross borders?
        |
        v
What regulations apply?
```

Important areas include:

- Privacy
- Data residency
- Cross-border transfer
- Industry requirements
- AI-specific regulations
- Retention
- Auditability
- Responsible AI

## Architecture

```text
                 AI Solution
                     |
        +------------+------------+
        |            |            |
        v            v            v
      Data         Model        Users
        |            |            |
        +------------+------------+
                     |
                     v
          Compliance Assessment
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
   Privacy       Residency      Industry
   Rules         Rules          Rules
       |             |             |
       +-------------+-------------+
                     |
                     v
              Approved Design
```

## Architect Questions

**Q: What should the architect determine first?**  
Expected answer: Where the data is stored and processed, who can access it, and which regulations apply.

**Q: Can regulatory requirements affect architecture?**  
Expected answer: Yes. They can affect data location, processing, access, retention, security, and platform choices.

## Key Takeaway

**Regulatory requirements become architecture constraints.**

---

# Topic 15 — Include Elements in a Microsoft AI Center of Excellence

## Concept

An AI Center of Excellence (AI CoE) provides the organizational capability for scaling AI responsibly.

It can provide:

- Governance
- Architecture standards
- Responsible AI practices
- Security and compliance guidance
- Skills and training
- Reusable assets
- Monitoring
- Business alignment

## Architecture

```text
                    AI CoE
                      |
      +---------------+---------------+
      |               |               |
      v               v               v
 Governance       Architecture     Skills
      |               |               |
      v               v               v
 Responsible AI   Standards       Training
      |               |               |
      +---------------+---------------+
                      |
                      v
                Business Teams
                      |
                      v
                 AI Solutions
                      |
                      v
             Monitor + Improve
```

## Important Components

```text
Executive Sponsorship
        +
Governance
        +
Architecture Standards
        +
Security / Compliance
        +
Responsible AI
        +
Skills / Training
        +
Reusable Assets
        +
Monitoring
```

## Architect Questions

**Q: What is the purpose of an AI CoE?**  
Expected answer: To provide governance, standards, expertise, reusable practices, and organizational support for scaling AI.

**Q: Why is an AI CoE useful?**  
Expected answer: It helps prevent disconnected AI efforts and creates consistent enterprise practices.

## Key Takeaway

**The AI CoE provides the organizational operating model for scaling AI consistently and responsibly.**

---

# Topic 16 — Design AI Solutions Using Multiple Dynamics 365 Apps

## Concept

Real business processes often cross application boundaries.

For example:

```text
Sales
  |
  v
Customer Service
  |
  v
Finance
  |
  v
Field Service
```

An AI solution may need to understand the customer and business context across several Dynamics 365 applications.

## Architecture

```text
                  Customer
                     |
                     v
              Shared Business
                  Context
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
 Dynamics 365    Dynamics 365   Dynamics 365
    Sales        Customer       Finance
                 Service
       |             |             |
       +-------------+-------------+
                     |
                     v
               AI Orchestration
                     |
                     v
               Business Process
                     |
                     v
              Consistent Outcome
```

## Example

```text
Customer
   |
   v
Customer Service
   |
   v
AI identifies product/problem
   |
   +----> Sales history
   |
   +----> Customer history
   |
   +----> Finance information
   |
   +----> Field Service
   |
   v
Recommended action
```

## Architect Perspective

The main architecture concerns include:

- Shared business context
- Identity
- Permissions
- Data integration
- Process continuity
- Consistent AI behavior

## Architect Questions

**Q: Why use multiple Dynamics 365 applications in one AI solution?**  
Expected answer: Because a real business process may span multiple business functions and applications.

**Q: What is important when connecting multiple apps?**  
Expected answer: Shared business context, consistent security, integration, and coordinated business processes.

## Key Takeaway

**Multi-app Dynamics solutions need shared context, process continuity, consistent security, and coordinated AI behavior.**

---

# Topic 17 — Design User Prompt Training for AI Solution Adoption

## Concept

Deploying an AI solution does not automatically mean users will use it effectively.

Users need to understand:

- How to ask good questions
- How to structure prompts
- How to validate AI output
- How to use AI responsibly
- How AI fits into their workflow

## Architecture

```text
             AI Solution
                  |
                  v
            User Personas
                  |
       +----------+----------+
       |          |          |
       v          v          v
    Training   Prompting   Responsible
                Skills        AI
       |          |          |
       +----------+----------+
                  |
                  v
             User Adoption
                  |
                  v
           Business Outcome
```

## Persona-Based Training

### Sales User

```text
Sales User
   |
   +--> Customer summary prompts
   +--> Meeting preparation
   +--> Follow-up drafting
```

### Support User

```text
Support User
   |
   +--> Issue summarization
   +--> Knowledge search
   +--> Response drafting
```

### Manager

```text
Manager
   |
   +--> Trend analysis
   +--> Business questions
   +--> Decision support
```

## Architect Perspective

Training should match the user's role and workflow rather than focusing only on generic prompting.

## Architect Questions

**Q: Why is prompt training important?**  
Expected answer: It helps users get better results, understand AI limitations, validate output, and use AI responsibly.

**Q: Should all users receive exactly the same training?**  
Expected answer: No. Training should be aligned to user personas, roles, workflows, and responsibilities.

## Key Takeaway

**AI adoption requires people, skills, responsible usage, and workflow integration—not just technology deployment.**

---

# Module 3 — Final Architect Whiteboard

Use this as the final revision diagram.

```text
                    1. BUSINESS OUTCOME
                           |
                           v
                    2. AI USE CASE
                           |
                           v
                    3. IS AI NEEDED?
                           |
                           v
                    4. AGENT REQUIRED?
                           |
                           v
                 5. PREBUILT FIRST
                           |
                 +---------+---------+
                 |                   |
                 v                   v
             M365 Copilot       Custom Need
                                     |
                           +---------+---------+
                           |                   |
                           v                   v
                    Copilot Studio        Foundry
                           |                   |
                           +---------+---------+
                                     |
                                     v
                            6. SINGLE AGENT?
                                     |
                              +------+------+
                              |             |
                              v             v
                           Single        Multi-Agent
                              |             |
                              +------+------+
                                     |
                                     v
                            7. KNOWLEDGE
                                     |
                                     v
                            8. DATA ACCESS
                                     |
                                     v
                         9. RULES / GUARDRAILS
                                     |
                                     v
                           10. MODEL CHOICE
                                     |
                                     v
                           11. PROMPT DESIGN
                                     |
                                     v
                        12. SECURITY / PRIVACY
                                     |
                                     v
                           13. COMPLIANCE
                                     |
                                     v
                             14. AI CoE
                                     |
                                     v
                         15. BUSINESS ROLES
                                     |
                                     v
                      16. BUSINESS APPLICATIONS
                                     |
                                     v
                           17. USER TRAINING
                                     |
                                     v
                       BUSINESS VALUE + ADOPTION
```

# 10 Decisions to Remember for AB-100

| Decision | Architect Thinking |
|---|---|
| 1. AI or not? | Start with the business outcome |
| 2. Agent or application? | Use an agent when reasoning/orchestration adds value |
| 3. Prebuilt or custom? | Start with existing Microsoft capability |
| 4. Copilot Studio or Foundry? | Match the platform to customization and orchestration needs |
| 5. Single or multi-agent? | Start single; split when specialization or boundaries justify it |
| 6. What knowledge? | Use authoritative, relevant, accessible enterprise data |
| 7. What can AI do? | Define tools, actions, permissions, and guardrails |
| 8. Which model? | Existing model first; customize only when justified |
| 9. How do we govern it? | Security, compliance, AI CoE, roles, and monitoring |
| 10. How do users adopt it? | Persona-based training, prompt skills, and responsible usage |

# 4-Hour Study Structure

## Part 1 — Strategy

Study:

- Topic 1 — Introduction
- Topic 2 — AI Adoption Process
- Topic 3 — Agent Strategy
- Topic 4 — Multi-Agent Solutions
- Topic 5 — Prebuilt Agents

Goal:

> Understand how an architect moves from business outcome to platform and agent architecture.

## Part 2 — Solution Design

Study:

- Topic 6 — Rules and Constraints
- Topic 7 — Knowledge Sources
- Topic 8 — Extend or Build
- Topic 9 — Custom Models
- Topic 10 — Prompt Library
- Topic 11 — SLMs
- Topic 12 — Prompt Engineering

Goal:

> Understand data, rules, platform choice, models, and prompts.

## Part 3 — Enterprise Architecture

Study:

- Topic 13 — Business User Roles
- Topic 14 — Regulation
- Topic 15 — AI CoE
- Topic 16 — Dynamics 365
- Topic 17 — User Training

Goal:

> Understand people, compliance, governance, business applications, and adoption.

## Part 4 — Whiteboard Revision

Without looking at the notes, draw:

```text
Business Outcome
      ↓
AI Use Case
      ↓
Prebuilt?
  ↓       ↓
 Yes      No
  ↓       ↓
Copilot  Studio / Foundry
             ↓
       Single / Multi Agent
             ↓
       Knowledge + Data
             ↓
       Rules + Guardrails
             ↓
        Model + Prompt
             ↓
       Security + Compliance
             ↓
             AI CoE
             ↓
        Business Users
             ↓
          Adoption
             ↓
       Business Outcome
```

If you can explain this diagram in your own words, you understand the core architecture story of Module 3.
