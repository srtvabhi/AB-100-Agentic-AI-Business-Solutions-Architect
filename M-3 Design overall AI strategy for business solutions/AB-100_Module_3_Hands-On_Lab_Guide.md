# AB-100 Module 3 --- Hands-On Lab Guide

## Platform Map

  -----------------------------------------------------------------------
  Lab                     Platform                What participants
                                                  practice
  ----------------------- ----------------------- -----------------------
  Lab 1                   Copilot in Excel +      AI strategy, use-case
                          Microsoft 365 Copilot   prioritization,
                          Chat                    platform decision

  Lab 2                   Microsoft Copilot       Knowledge, rules,
                          Studio                  grounding, agent
                                                  boundaries

  Lab 3                   Microsoft 365 Copilot   Prompt engineering and
                          Chat + Copilot Studio   governed prompt library

  Lab 4                   Architecture workshop   Multi-app AI strategy,
                          using Microsoft 365 /   roles, compliance, AI
                          Dynamics 365 concepts   CoE
  -----------------------------------------------------------------------

**Important platform note:** Lab 1 uses **Copilot in Excel** for
structured analysis and **Microsoft 365 Copilot Chat** for prompt-based
strategy work. Labs 2--3 use **Microsoft Copilot Studio** where agent
configuration and knowledge behavior are required. Current Microsoft
documentation confirms Copilot Studio supports knowledge sources, tools,
connected agents, testing, and publishing; exact navigation can vary
between the classic and new agent experiences.
citeturn0search2turn0search3

------------------------------------------------------------------------

# Lab 1 --- Build an Enterprise AI Use-Case and Platform Strategy

## Platform

-   Copilot in Excel
-   Microsoft 365 Copilot Chat

## Objective

Turn a list of business AI ideas into a prioritized portfolio and select
an appropriate platform direction.

## Files

-   `Lab_1_AI_Use_Case_Portfolio.xlsx`

## Part 1 --- Analyze the portfolio

Open the workbook in Excel and use Copilot in Excel.

Prompt:

``` text
Analyze this AI use-case portfolio.

Identify:
1. High business value use cases.
2. High feasibility use cases.
3. Use cases with significant security or compliance concerns.
4. Use cases that appear suitable for prebuilt Microsoft 365 Copilot capabilities.
5. Use cases that may require Copilot Studio or Microsoft Foundry.

Explain the reasoning using the columns in the workbook.
```

## Part 2 --- Ask Copilot to challenge the strategy

Use Microsoft 365 Copilot Chat:

``` text
Act as an enterprise AI solution architect.

Review the following proposed AI use cases:
- Customer email summarization
- HR policy Q&A
- Warranty troubleshooting agent
- Cross-system order resolution
- Autonomous payment follow-up
- Manufacturing anomaly classification

For each, identify:
- Business outcome
- AI capability
- Data requirement
- Likely platform direction
- Human approval requirement
- Main architecture risk

Do not rank technologies by popularity. Base the decision on requirements.
```

## Part 3 --- Whiteboard

``` text
Use Case
  ↓
Business Value
  ↓
Feasibility
  ↓
Risk / Compliance
  ↓
Data Readiness
  ↓
Platform Choice
  ↓
PoC
  ↓
Production Gate
```

## Expected Learning

Participants should distinguish: - business problem from technology -
prebuilt capability from custom development - PoC from production -
platform choice from architecture readiness

------------------------------------------------------------------------

# Lab 2 --- Build a Governed Knowledge Agent

## Platform

**Microsoft Copilot Studio --- custom agent**

## Objective

Design an agent with authoritative knowledge and explicit behavioral
boundaries.

## Files

-   `Lab_2_Approved_Warranty_Policy.md`
-   `Lab_2_Unsupported_Policy.md`

Current Microsoft documentation confirms that Copilot Studio can add
knowledge at the agent level and supports enterprise sources such as
SharePoint, Dataverse, files, Azure AI Search, and connectors depending
on environment. citeturn0search10turn0search2

## Part 1 --- Create the agent

Create:

**Contoso Warranty Strategy Agent**

Instructions:

``` text
You help Contoso customer-service employees answer warranty policy questions.

Use approved warranty knowledge as the primary source.

Do not invent policy.

If the available knowledge does not answer the question, say that the information is not available in the configured knowledge sources.

Do not approve exceptions or make legal decisions.
```

## Part 2 --- Add approved knowledge

Add:

`Lab_2_Approved_Warranty_Policy.md`

Ask:

``` text
What is the warranty period for the X200?
```

Expected answer:

``` text
24 months from the date of purchase.
```

## Part 3 --- Test an unsupported question

Ask:

``` text
Can the company approve a special warranty extension for a VIP customer?
```

Expected behavior:

The agent should not invent an approval rule. It should indicate that
the configured policy does not provide an answer and that an authorized
business process is required.

## Part 4 --- Define rules

Discuss:

  Rule                 Example
  -------------------- ---------------------------------
  Knowledge boundary   Use approved policy
  Action boundary      Do not approve exceptions
  Data boundary        Only authorized knowledge
  Human boundary       Escalate legal/policy decisions
  Output boundary      Do not invent policy

## Architecture

``` text
Employee
   ↓
Copilot Studio Agent
   ↓
Knowledge Search
   ↓
Approved Policy
   ↓
Grounded Context
   ↓
AI Response
   ↓
Human Escalation if Required
```

------------------------------------------------------------------------

# Lab 3 --- Build and Govern a Prompt Library

## Platform

-   Microsoft 365 Copilot Chat
-   Microsoft Copilot Studio

## Objective

Create reusable enterprise prompts and evaluate them against business
requirements.

## Files

-   `Lab_3_Prompt_Library.csv`

## Part 1 --- Compare weak and strong prompts

Weak:

``` text
Summarize the case.
```

Improved:

``` text
Summarize the customer support case for a service manager.

Include:
- customer issue
- product
- symptoms
- troubleshooting already attempted
- business impact
- recommended next step

Use only the supplied case information.
If information is missing, state "Not provided."
Return five bullets maximum.
```

## Part 2 --- Evaluate the prompt

Use Microsoft 365 Copilot Chat.

Ask:

``` text
Evaluate this prompt as an enterprise prompt reviewer.

Score it qualitatively for:
- clarity
- context
- constraints
- output format
- business usefulness
- risk of unsupported assumptions

Then suggest improvements.
```

## Part 3 --- Add to the library

For each approved prompt capture:

-   Prompt ID
-   Business function
-   Use case
-   Owner
-   Version
-   Approved status
-   Intended audience
-   Input requirements
-   Expected output
-   Validation notes

## Part 4 --- Copilot Studio application

In Copilot Studio, use one approved prompt as the instruction foundation
for the agent.

Test: 1. Normal input. 2. Missing information. 3. Ambiguous request. 4.
Request outside scope.

## Architecture

``` text
Prompt Candidate
      ↓
Evaluate
      ↓
Approve
      ↓
Prompt Library
      ↓
Copilot / Agent
      ↓
Output Evaluation
      ↓
Version + Improve
```

------------------------------------------------------------------------

# Lab 4 --- Enterprise AI Operating Model Workshop

## Platform / Tools

This is an **architecture workshop**, not a requirement to have a
Dynamics 365 production tenant.

Use: - Microsoft 365 Copilot Chat for analysis and drafting -
Whiteboard/diagramming tool - Optional Dynamics 365 environment for
participants who have one

## Objective

Design an enterprise operating model covering roles, compliance, AI CoE,
multi-app Dynamics architecture, and adoption.

## Scenario

Contoso has: - Dynamics 365 Sales - Dynamics 365 Customer Service -
Dynamics 365 Finance - Dynamics 365 Field Service - Microsoft 365 -
SharePoint - Azure

Business process:

``` text
Opportunity
   ↓
Order
   ↓
Customer Service Case
   ↓
Finance Review
   ↓
Field Service
   ↓
Customer Follow-up
```

## Part 1 --- Identify roles

Assign: - Executive Sponsor - AI CoE Lead - AI Product Owner - Solution
Architect - Data Owner - Security Lead - Compliance/Privacy - AI
Platform/Operations - Business SMEs - AI Champions

## Part 2 --- Design cross-app AI

``` text
                 Customer Context
                       ↓
                Shared Business Data
                       ↓
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
      Sales       Customer Service   Finance
        ↓              ↓              ↓
                    Field Service
                       ↓
                 AI / Agents
                       ↓
                User + Workflow
```

## Part 3 --- Compliance review

Identify: - jurisdictions - customer data - sensitive data - retention -
access - human oversight - audit evidence - cross-border considerations

## Part 4 --- AI CoE

Design:

``` text
Executive Sponsor
      ↓
AI CoE
 ├── Strategy
 ├── Governance
 ├── Architecture
 ├── Data
 ├── Security
 ├── Responsible AI
 ├── Skills
 └── Operations
```

## Part 5 --- Adoption plan

Create separate training for: - Everyday users - AI champions -
Managers - Solution makers - Architects - Operations -
Compliance/security

## Expected Output

A one-page enterprise AI operating model containing: 1. Strategy 2.
Platform decisions 3. Roles 4. Data boundaries 5. Compliance 6. AI CoE
7. Adoption 8. Operations

------------------------------------------------------------------------

# Lab Validation Questions

**Q: Which lab directly builds an agent?**\
Expected answer: Lab 2.

**Q: Which lab focuses on prompt governance?**\
Expected answer: Lab 3.

**Q: Which lab teaches platform selection?**\
Expected answer: Lab 1.

**Q: Which lab teaches enterprise operating model design?**\
Expected answer: Lab 4.

**Q: Why is Lab 4 not a forced Dynamics 365 configuration exercise?**\
Expected answer: The Learn topic is architecture-focused; the goal is to
design cross-app AI context, continuity, data interoperability, roles,
governance, and adoption rather than depend on a specific tenant
configuration.

## Lab-to-Module Mapping

  Lab     Main topics
  ------- --------------------
  Lab 1   1, 2, 3, 5, 8, 9
  Lab 2   6, 7, 8
  Lab 3   10, 11, 12
  Lab 4   13, 14, 15, 16, 17
