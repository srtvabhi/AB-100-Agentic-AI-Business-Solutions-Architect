# AB-100 Module 1 — Introduction to Agentic AI Business Solution Architecture

## Module Overview

The purpose of Module 1 is to establish the mindset of an **AI Solution Architect**.

The key idea is:

> **AI architecture starts with a business problem and ends with measurable business value.**

An architect must understand the business objective, identify where AI can help, select the right Microsoft AI technology, integrate it with business data and systems, and ensure the solution is secure, responsible, scalable, and measurable.

### The overall AI transformation journey

```text
Business Goals
      ↓
AI Strategy
      ↓
Architecture Design
      ↓
Implementation
      ↓
Monitoring & Optimization
```

---

# 1. Introduction

## What is AI Business Solution Architecture?

AI transformation is more than implementing a new technology. It can change:

- Business processes
- Employees' work
- Organizational culture
- Data usage
- Existing applications
- Security and governance
- Business outcomes

The AI architect connects **business strategy** with **technical implementation**.

### Simple explanation

If a company says:

> "We want AI."

That is not yet an architecture requirement.

The architect needs to understand:

> What business problem are we solving, where can AI help, what data and systems are involved, and how will we measure success?

For example:

> "We want to reduce customer-service resolution time by using an AI agent that can retrieve approved company information and help employees resolve customer issues."

Now we have a business requirement that can be architected.

---

## Architect Discovery Questions

### What is the business goal?

→ Define the measurable business outcome the organization wants to achieve, such as improving productivity, reducing cost, or increasing customer satisfaction.

### 1. What process needs improvement?

→ Identify the specific business workflow or task where AI can improve speed, quality, productivity, or decision-making.

### 2. What does AI need to do?

→ Define the required AI capability, such as answering questions, generating content, summarizing information, recommending actions, or performing tasks.

### 3. What data does it need?

→ Identify the trusted business data and knowledge sources required to provide accurate and relevant AI responses.

### 4. What systems must it connect to?

→ Identify the applications and services the AI solution needs to read from or interact with, such as Microsoft 365, Dynamics 365, Dataverse, or external systems.

### 5. What security/governance is required?

→ Define the required identity, access, privacy, compliance, data protection, responsible-AI, and governance controls.

### 6. How will we measure success?

→ Define measurable KPIs such as productivity improvement, cost reduction, response time, accuracy, adoption, or customer satisfaction.

---

## AI Architect Responsibilities

### Vision and Roadmap

The architect defines the organization's AI adoption strategy and roadmap.

```text
Current Business
      ↓
Identify AI Opportunities
      ↓
AI Strategy
      ↓
AI Roadmap
      ↓
Future State
```

**Expected answer:**  
→ The roadmap defines where the organization wants to go with AI and how AI initiatives support business priorities.

### Data Architecture

The architect ensures that the required data is available, usable, governed, and secure.

```text
              AI
               │
               ▼
          AI Context
               │
       ┌───────┼────────┐
       ▼       ▼        ▼
 SharePoint Dataverse Dynamics
       │       │        │
       └───────┼────────┘
               ▼
          Business Data
```

**Expected answer:**  
→ Ensure the AI solution has access to trusted, relevant, governed, and secure data.

### Integration

AI normally needs to interact with existing business applications.

```text
                 AI Agent
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
   Microsoft 365  Dynamics 365  External
                                Systems
        │           │           │
        └───────────┼───────────┘
                    ▼
             Business Process
```

**Expected answer:**  
→ Integrate AI with enterprise applications and workflows so AI can access information and perform required business actions.

### Security and Responsible AI

AI solutions must consider:

- Security
- Privacy
- Fairness
- Transparency
- Accountability
- Compliance

**Expected answer:**  
→ Protect data and users while ensuring AI operates responsibly, securely, transparently, and within organizational policies.

### Performance Monitoring

The architect must establish KPIs and monitor whether the solution is delivering the expected value.

```text
AI Solution
     ↓
Business KPI
     ↓
Measure
     ↓
Analyze
     ↓
Improve
```

**Expected answer:**  
→ Define measurable KPIs and continuously monitor the AI solution to verify that it delivers the expected business outcome.

---

# 2. Drive AI Transformation with Architect Strategies

This topic focuses specifically on the **role of the AI architect**.

Microsoft describes the architect as the bridge between business strategy and technical implementation. The major responsibilities are strategic alignment, solution design, governance/compliance, and scalability.

## Strategic Alignment

The AI solution must support organizational objectives.

```text
Business Strategy
       ↓
Business Goals
       ↓
AI Opportunities
       ↓
AI Strategy
       ↓
AI Solution
```

### Question

**Why must AI initiatives be aligned with business strategy?**

**Expected answer:**  
→ Because AI should solve meaningful business problems and produce measurable business value rather than being implemented simply because the technology is available.

---

## Solution Design

The architect designs how AI integrates into existing systems.

```text
                AI Solution
                     │
       ┌─────────────┼─────────────┐
       ▼             ▼             ▼
      Data          AI          Business Apps
       │             │             │
       └─────────────┼─────────────┘
                     ▼
              Business Process
```

### Question

**What is the architect responsible for in solution design?**

**Expected answer:**  
→ Design an architecture that connects AI capabilities, data, applications, and business workflows into a complete solution.

---

## Governance and Compliance

AI needs governance from the beginning.

```text
                  AI Solution
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Security      Privacy     Compliance
          │            │            │
          └────────────┼────────────┘
                       ▼
                Responsible AI
```

### Question

**Why is governance important for AI solutions?**

**Expected answer:**  
→ Governance ensures AI is used securely, responsibly, legally, and consistently with organizational policies.

---

## Scalability

The architecture should support growth.

```text
Pilot
  ↓
Standardize
  ↓
Automate
  ↓
Scale
  ↓
Monitor
  ↓
Improve
```

### Question

**How do you scale AI across an organization?**

**Expected answer:**  
→ Use standardization, automation, reusable components, continuous improvement, and user enablement.

---

## Architect Best Practices

### Start with business outcomes

**Expected answer:**  
→ Define the measurable business result before selecting the AI technology.

### Use modular design

**Expected answer:**  
→ Build reusable and flexible components so the solution can evolve and scale.

### Prioritize Responsible AI

**Expected answer:**  
→ Design fairness, transparency, accountability, safety, privacy, and security into the solution.

### Collaborate across teams

**Expected answer:**  
→ Bring business leaders, developers, data professionals, security teams, and other stakeholders into the architecture process.

### Use appropriate Microsoft AI services

**Expected answer:**  
→ Select Microsoft AI capabilities that provide the required functionality while supporting enterprise reliability and scalability.

---
<div align="center">

### 📘 Case Study 1 — Customer Service AI Transformation

👉 **[Click here to read the case study](https://github.com/srtvabhi/AB-100-Agentic-AI-Business-Solutions-Architect/blob/main/M1-Introduction%20to%20agentic%20AI%20business%20solutions/AB-100_Case_Study_1_Customer_Service_AI_Transformation.md)**

</div>


# 3. Explore Microsoft AI Technologies for Business

This topic introduces the major Microsoft AI technology categories and their purpose.

Don't memorize the products as a list. Understand **what problem each category solves**.

## Azure AI Services

These provide prebuilt AI capabilities such as:

- Vision
- Speech
- Language
- Decision

```text
Application
     │
     ▼
Azure AI Services
     │
 ┌───┼────┬──────┐
 ▼   ▼    ▼      ▼
Vision Speech Language Decision
```

### Question

**When would you use Azure AI Services?**

**Expected answer:**  
→ When an application needs a prebuilt AI capability such as vision, speech, language understanding, or decision-making.

---

# Azure Machine Learning

Azure Machine Learning supports building, training, and deploying machine-learning models.

```text
Training Data
     ↓
Build / Train Model
     ↓
Evaluate
     ↓
Deploy
     ↓
Prediction
```

### Question

**When would you use Azure Machine Learning?**

**Expected answer:**  
→ When an organization needs to build, train, evaluate, deploy, and manage its own machine-learning models.

---

# Azure OpenAI Service

Azure OpenAI provides access to generative AI models for natural-language and creative tasks.

```text
User / Application
        ↓
Azure OpenAI
        ↓
Generative AI Model
        ↓
Generated Response
```

### Question

**When would you use Azure OpenAI Service?**

**Expected answer:**  
→ When an application needs generative AI capabilities such as text generation, summarization, natural-language interaction, or creative content generation.

---

# Azure Foundry

Azure Foundry is a platform for developing, deploying, and managing AI applications and agents.

```text
             AI Application
                   │
                   ▼
             Azure Foundry
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
      Models      Agents     Tools
        │          │          │
        └──────────┼──────────┘
                   ▼
              AI Solution
```

### Question

**What is the architectural role of Azure Foundry?**

**Expected answer:**  
→ It provides a platform for developing, deploying, and managing AI applications and agents.

---

# Tools, SDKs, APIs and CLI

Microsoft also introduces development and integration tools:

- Azure Machine Learning Studio
- SDKs
- APIs
- CLI
- REST APIs

The important architectural idea is **integration**.

```text
Business Application
        │
        ▼
      API / SDK
        │
        ▼
    AI Capability
        │
        ▼
     AI Result
        │
        ▼
Business Application
```

### Question

**Why are APIs and SDKs important to an AI architect?**

**Expected answer:**  
→ They allow AI capabilities to be integrated into applications, workflows, and enterprise systems.

---

# Microsoft Copilot Solutions

Copilot solutions embed AI into Microsoft 365 and Dynamics 365 to automate repetitive tasks, generate content, provide insights, and improve productivity.

```text
                USER
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     Word       Teams      Outlook
       │          │          │
       └──────────┼──────────┘
                  ▼
               Copilot
                  │
                  ▼
          Business Context
                  │
                  ▼
           Business Value
```

### Question

**What is the business purpose of Copilot solutions?**

**Expected answer:**  
→ To embed AI into everyday business applications so users can automate tasks, generate content, gain insights, and improve productivity.

---

# 4. Identify Microsoft AI Technologies for Business Solutions

This topic focuses on how Microsoft AI technologies create **business value**.

The important idea is:

> Technology is valuable only when it improves a business outcome.

---

## Automate

AI can automate repetitive work.

```text
Manual Task
    ↓
    AI
    ↓
Automated Task
```

Example:

> Summarize incoming customer requests and route them to the appropriate team.

### Question

**How does AI automation create business value?**

**Expected answer:**  
→ It reduces repetitive manual work, saves employee time, and improves process efficiency.

---

# Generate

Generative AI can create content and insights.

```text
Business Context
       +
     Prompt
       ↓
      AI
       ↓
Content / Insight
```

Examples:

- Draft emails
- Summarize documents
- Create reports
- Generate proposals
- Generate meeting summaries

### Question

**How does generative AI improve productivity?**

**Expected answer:**  
→ It helps employees quickly create, summarize, transform, and analyze business content.

---

# Collaborate

AI can improve collaboration across teams.

```text
Employees
    │
    ├── Teams
    ├── Outlook
    ├── Word
    └── SharePoint
          │
          ▼
        Copilot
          │
          ▼
   Better Collaboration
```

### Question

**How can AI improve collaboration?**

**Expected answer:**  
→ AI can summarize information, surface relevant knowledge, assist communication, and help employees work more efficiently.

---

# Business Value Architecture

Put the three concepts together:

```text
                    AI
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
    Automate      Generate    Collaborate
       │            │            │
       ▼            ▼            ▼
   Less manual   Better       Better
      work       content      teamwork
       │            │            │
       └────────────┼────────────┘
                    ▼
              Business Value
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
 Productivity     Quality       Cost
 Improvement     Improvement   Reduction
```

---

# Responsible AI

Microsoft identifies these Responsible AI principles:

- Fairness
- Reliability and safety
- Privacy and security
- Inclusiveness
- Transparency
- Accountability

### Question

**What is Responsible AI?**

**Expected answer:**  
→ Designing and operating AI so it is fair, safe, secure, inclusive, transparent, and accountable.

### Question

**Why should Responsible AI be considered during architecture?**

**Expected answer:**  
→ Because security, privacy, safety, fairness, and compliance need to be designed into the solution rather than added after deployment.

---

# Business Value Decision

An architect should think:

```text
AI Technology
     ↓
Business Process
     ↓
Productivity / Automation
     ↓
Business KPI
     ↓
Measurable Value
```

### Question

**What should an architect ask before selecting an AI technology?**

**Expected answer:**  
→ Identify the business outcome first and then select the AI capability that can deliver that outcome responsibly and at enterprise scale.

---
> [!NOTE]
> ### 📘 Case Study 2 — Choosing the Right Microsoft AI Technology
>
> 👉 **[Click here to read the case study](https://github.com/srtvabhi/AB-100-Agentic-AI-Business-Solutions-Architect/blob/main/M1-Introduction%20to%20agentic%20AI%20business%20solutions/AB-100_Case_Study_2_Choosing_the_Right_Microsoft_AI_Technology.md)**

# 5. Identify Out-of-Box Microsoft AI Agent Resources

This topic introduces Microsoft's **out-of-the-box AI agent resources**.

## What does OOB mean?

OOB means **Out-of-Box**.

In simple language:

> Microsoft has already created part of the solution, so you don't need to start from zero.

Instead of:

```text
Requirement
     ↓
Design
     ↓
Develop Everything
     ↓
Test
     ↓
Deploy
```

You can use:

```text
Requirement
     ↓
Find OOB Capability
     ↓
Configure
     ↓
Customize if needed
     ↓
Deploy
```

---

# OOB AI Agent Resources

## Prebuilt AI Agents

Prebuilt agents are designed for common scenarios such as:

- Customer service
- Sales automation
- Workflow optimization

### Question

**Why use a prebuilt agent?**

**Expected answer:**  
→ It provides a faster starting point for common business scenarios and reduces the amount of custom development required.

---

# Copilot Studio

Copilot Studio can be used to customize and deploy AI agents.

```text
             Copilot Studio
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
   Configure     Knowledge      Actions
       │            │             │
       └────────────┼─────────────┘
                    ▼
                 Agent
                    │
                    ▼
              Business Process
```

### Question

**What is the role of Copilot Studio?**

**Expected answer:**  
→ It provides capabilities for creating, customizing, and deploying agents for business scenarios.

---

# Azure AI Services

Azure AI Services provide capabilities such as:

- Vision
- Speech
- Language
- Decision

### Question

**Why might an agent need Azure AI Services?**

**Expected answer:**  
→ The agent can use specialized AI capabilities such as speech, vision, language understanding, or decision capabilities as part of its solution.

---

# Templates

Templates provide a ready-made starting point for building a solution.

```text
Microsoft Template
       ↓
Customize
       ↓
Business-specific Agent
```

### Question

**What is the benefit of an AI template?**

**Expected answer:**  
→ It provides a reusable starting point that reduces development effort and accelerates solution delivery.

---

# Scenario Libraries

Scenario libraries help organizations identify business scenarios and adoption approaches.

### Question

**Why are scenario libraries useful to an architect?**

**Expected answer:**  
→ They help identify practical AI use cases and provide guidance for adopting AI in business processes.

---

# OOB Resource Architecture

```text
                Business Requirement
                         │
                         ▼
                Find OOB Resources
                         │
             ┌───────────┼───────────┐
             ▼           ▼           ▼
         Prebuilt     Templates    Scenario
          Agents                   Library
             │           │           │
             └───────────┼───────────┘
                         ▼
                   Copilot Studio
                         │
                         ▼
                 Configure / Extend
                         │
                         ▼
                    AI Solution
```

---

# Architect Decision — Reuse Before Build

This is an important pattern to remember:

```text
          BUSINESS REQUIREMENT
                   │
                   ▼
          Is OOB available?
              /         \
            YES          NO
             │            │
             ▼            ▼
         Configure     Extend
             │            │
             ▼            ▼
          Customize     Build
             │            │
             └──────┬─────┘
                    ▼
              AI Solution
```

### Question

**What should an architect do before building a custom AI solution?**

**Expected answer:**  
→ First evaluate available Microsoft OOB agents, templates, Copilot capabilities, and other reusable resources.

---

# 6. Identify Out-of-Box Microsoft AI Agents

This topic focuses specifically on **OOB AI agents**.

Microsoft describes OOB agents as prebuilt AI agents and templates available through Microsoft Copilot Studio and Microsoft 365 for common business scenarios.

Examples include:

- Customer service automation
- Workflow optimization
- Data-driven decision-making

---

# What is an OOB AI Agent?

Simple explanation:

> An OOB AI agent is a prebuilt agent that provides a starting point for a common business scenario.

Instead of building:

```text
                  YOU
                   │
                   ▼
            Build Everything
                   │
          ┌────────┼─────────┐
          ▼        ▼         ▼
       Logic    Knowledge   Actions
```

You start with:

```text
             Microsoft
                 │
                 ▼
          Prebuilt Agent
                 │
        ┌────────┼────────┐
        ▼        ▼        ▼
      Logic   Knowledge  Actions
                 │
                 ▼
          Customize for
          Your Business
```

---

# Benefits of OOB Agents

## Faster Deployment

Ready-to-use capabilities reduce development time.

**Expected answer:**  
→ OOB agents accelerate delivery because much of the functionality is already available.

---

## Scalability

OOB agents can integrate with Microsoft business platforms such as Microsoft 365 and Dynamics 365.

**Expected answer:**  
→ OOB agents provide a platform-based approach that can be integrated and scaled across Microsoft business environments.

---

## Compliance / Responsible AI

Microsoft positions these capabilities around its Responsible AI principles.

**Expected answer:**  
→ OOB solutions provide a starting point aligned with Microsoft's responsible-AI practices and enterprise controls.

---

# Copilot Studio

Copilot Studio can be used to explore prebuilt agents and customize them.

### Question

**What can you do with an OOB agent in Copilot Studio?**

**Expected answer:**  
→ You can use the existing agent as a starting point and customize it for the organization's specific business requirements.

---

# Templates

Templates provide reusable fundamentals for creating tailored AI solutions.

### Question

**Why would an architect choose a template?**

**Expected answer:**  
→ A template provides a proven starting structure that can be customized instead of developing the solution from scratch.

---

# Scenario Library

The Microsoft Adoption Scenario Library provides business scenarios and adoption guidance.

### Question

**How does a scenario library help an organization?**

**Expected answer:**  
→ It helps identify practical AI opportunities and provides guidance for adopting AI in real business scenarios.

---

# OOB Agent Decision Architecture

```text
                    BUSINESS NEED
                         │
                         ▼
                Is there an OOB
                     agent?
                   /       \
                 YES        NO
                  │          │
                  ▼          ▼
             Use / Configure
                             │
                             ▼
                       Can we extend
                       an existing
                       capability?
                        /       \
                      YES        NO
                       │          │
                       ▼          ▼
                    EXTEND      BUILD
                       │          │
                       └────┬─────┘
                            ▼
                      AI SOLUTION
```

The architectural principle is:

> **Reuse → Configure → Extend → Build**

---

# Topic 5 vs. Topic 6

## Topic 5 — OOB AI Agent Resources

The question is:

> **"What resources does Microsoft provide to help us build AI solutions?"**

Think:

```text
OOB Resources
    │
    ├── Prebuilt Agents
    ├── Copilot Studio
    ├── Azure AI Services
    ├── Templates
    └── Scenario Libraries
```

---

## Topic 6 — OOB AI Agents

The question is:

> **"Is there already an agent that can address my business scenario?"**

Think:

```text
Business Requirement
        │
        ▼
Existing Agent?
    /       \
  YES        NO
   │          │
   ▼          ▼
Configure   Extend / Build
```

---

# Complete Module 1 Architecture

Connect everything from all six topics:

```text
                         BUSINESS
                            │
                            ▼
                  ┌──────────────────┐
                  │  BUSINESS GOAL   │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ AI OPPORTUNITY   │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │   AI STRATEGY    │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ AI ARCHITECTURE │
                  └────────┬─────────┘
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
          COPILOT       AI SERVICES    AI MODELS
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                  ┌──────────────────┐
                  │  OOB AVAILABLE?  │
                  └────────┬─────────┘
                       YES │ NO
                           │
                ┌──────────┴──────────┐
                ▼                     ▼
             CONFIGURE            EXTEND / BUILD
                │                     │
                └──────────┬──────────┘
                           ▼
                  ┌──────────────────┐
                  │   AI SOLUTION    │
                  └────────┬─────────┘
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
            DATA          AGENT       BUSINESS
                                      SYSTEMS
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                  ┌──────────────────┐
                  │ BUSINESS OUTCOME │
                  └────────┬─────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │ MONITOR & OPTIMIZE│
                  └────────┬─────────┘
                           │
                           ▼
                         SCALE
```

---
> [!NOTE]
> ### 📘 Case Study 3 — Build, Extend, or Use an OOB Agent?
>
> 👉 **[Click here to read the case study](https://github.com/srtvabhi/AB-100-Agentic-AI-Business-Solutions-Architect/blob/main/M1-Introduction%20to%20agentic%20AI%20business%20solutions/AB-100_Case_Study_3_Build_Extend_or_Use_an_OOB_Agent.md)**

# Module 1 — Architect Questions & Expected Answers

| Architect Question | Expected Answer |
|---|---|
| **What is the business goal?** | Define the measurable business outcome the organization wants to achieve. |
| **What process needs improvement?** | Identify the business workflow where AI can improve productivity, quality, speed, or decision-making. |
| **What does AI need to do?** | Define the required AI capability, such as generating, summarizing, reasoning, recommending, or acting. |
| **What data does it need?** | Identify the trusted and relevant data required to provide accurate AI responses. |
| **What systems must it connect to?** | Identify the business applications and services AI must access or interact with. |
| **What security/governance is required?** | Define identity, access, privacy, security, compliance, governance, and Responsible AI requirements. |
| **How will we measure success?** | Define measurable KPIs that demonstrate business value. |
| **Why does an AI architect need a roadmap?** | To align AI adoption with business priorities and define the path from current to future state. |
| **Why is data architecture important?** | AI requires trusted, relevant, available, and governed data. |
| **Why is integration important?** | AI needs to work with existing business applications and processes. |
| **Why is Responsible AI important?** | AI must operate safely, fairly, transparently, securely, and accountably. |
| **How do we scale AI?** | Use standardization, automation, reusable components, continuous learning, and user enablement. |
| **When would you use Azure AI Services?** | When you need prebuilt AI capabilities such as vision, speech, language, or decision APIs. |
| **When would you use Azure Machine Learning?** | When you need to build, train, evaluate, deploy, and manage ML models. |
| **When would you use Azure OpenAI Service?** | When applications need generative AI capabilities for natural-language and creative tasks. |
| **What is the role of Azure Foundry?** | It provides a platform for developing, deploying, and managing AI applications and agents. |
| **Why are APIs and SDKs important?** | They allow AI capabilities to be integrated into applications and enterprise workflows. |
| **What is the business purpose of Copilot?** | To embed AI into business applications to improve productivity, automate work, generate content, and provide insights. |
| **How does AI create business value?** | By automating work, generating content/insights, improving collaboration, and producing measurable business outcomes. |
| **What should an architect do before building custom AI?** | Evaluate existing Microsoft capabilities, OOB agents, templates, and reusable resources. |
| **What is an OOB agent?** | A prebuilt AI agent designed to address a common business scenario. |
| **Why use an OOB agent?** | It can reduce development effort and accelerate deployment. |
| **What is the role of Copilot Studio?** | To create, customize, and deploy AI agents. |
| **What is the purpose of templates?** | To provide reusable starting points for AI solutions. |
| **What is the purpose of scenario libraries?** | To help identify AI opportunities and provide adoption guidance. |
| **What is the preferred architecture decision sequence?** | Reuse → Configure → Extend → Build. |

---

# Module 1 — Final Mental Model

If students remember only one thing, teach them this:

```text
             BUSINESS PROBLEM
                    │
                    ▼
             BUSINESS OUTCOME
                    │
                    ▼
              AI OPPORTUNITY
                    │
                    ▼
          WHAT DOES AI NEED TO DO?
                    │
                    ▼
             WHAT DATA IS NEEDED?
                    │
                    ▼
          WHAT SYSTEMS ARE NEEDED?
                    │
                    ▼
          OOB CAPABILITY AVAILABLE?
                /          \
              YES           NO
               │             │
               ▼             ▼
           CONFIGURE      EXTEND / BUILD
               │             │
               └──────┬──────┘
                      ▼
                AI SOLUTION
                      │
             ┌────────┼────────┐
             ▼        ▼        ▼
           DATA      AGENT    SYSTEMS
             │        │        │
             └────────┼────────┘
                      ▼
              BUSINESS VALUE
                      │
                      ▼
             MEASURE & MONITOR
                      │
                      ▼
                    SCALE
```

## The AB-100 Architect Mindset

> **Don't start with "Which Microsoft product should I use?"**

Start with:

> **"What business outcome are we trying to achieve?"**

Then determine:

**Business → Process → AI capability → Data → Systems → OOB capability → Architecture → Security/Governance → Business Value → Monitoring → Scale**
