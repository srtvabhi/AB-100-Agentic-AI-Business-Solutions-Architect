# AB-100 Module 2 --- Analyze Requirements for AI-Powered Business Solutions

## Topic 1 --- Introduction

### Concept

Before an organization builds an AI solution, the architect must
understand the business requirement.

The architect should not start by asking:

> Which AI product should we use?

The architect should start with:

> What business problem are we trying to solve?

Then identify:

-   The business process
-   The required AI capability
-   The information the AI needs
-   The systems the AI must interact with
-   The expected business outcome

AI-powered business solutions can support employees by helping them
retrieve information, generate content, automate tasks, analyze data,
and support decisions.

### Architecture Perspective

The architect connects the business requirement to the technical
solution.

The architect should determine:

1.  What business outcome is required?
2.  Which business process needs improvement?
3.  What should the AI actually do?
4.  What information does the AI need?
5.  What systems and data sources are involved?
6.  Where is human involvement required?
7.  How will success be measured?

### Whiteboard Architecture

``` text
Business Goal
     ↓
Business Process
     ↓
AI Requirement
     ↓
Required Data
     ↓
Required Systems
     ↓
AI Solution
     ↓
Business Outcome
```

### Architect Questions

**Q: What should the architect identify before selecting an AI
technology?**

**Expected answer:** The business outcome, process, AI requirement,
data, systems, and constraints.

**Q: Should the architect start with the AI product?**

**Expected answer:** No. Start with the business problem and required
outcome.

**Q: What is the main responsibility of the AI solution architect?**

**Expected answer:** Translate business requirements into a secure,
scalable, and useful AI solution.

**Q: Why is business context important for AI?**

**Expected answer:** AI needs the right business context to produce
useful and relevant results.

------------------------------------------------------------------------

# Topic 2 --- Assess Use of Agents for Task Automation, Data Analytics, and Decision-Making

## 2.1 Agents for Task Automation

### Concept

An AI agent can help perform repetitive business tasks.

Examples:

-   Summarize emails
-   Draft responses
-   Create documents
-   Retrieve information
-   Start workflows
-   Create records
-   Send notifications
-   Perform repetitive business actions

The important question is not:

> Can AI automate this?

The better question is:

> Should AI automate this process, and what business value will it
> provide?

### Architecture Perspective

The architect evaluates:

-   How often the task occurs
-   How repetitive the task is
-   How much manual effort is required
-   What systems are involved
-   What actions the agent must perform
-   Whether human approval is required
-   Risk if the agent makes a mistake
-   Expected business value

### Whiteboard Architecture

``` text
Business Event
      ↓
AI Agent
      ↓
Understand Request
      ↓
Retrieve Information
      ↓
Perform Action
      ↓
Business System
      ↓
Result
```

### Architect Questions

**Q: When is task automation a good AI use case?**

**Expected answer:** When a repeatable task requires significant manual
effort and AI automation provides measurable business value.

**Q: Should every repetitive task be automated with AI?**

**Expected answer:** No. The architect should consider business value,
complexity, risk, and whether AI is actually required.

**Q: When should a human remain involved?**

**Expected answer:** When the action has significant business,
financial, legal, customer, or security impact.

------------------------------------------------------------------------

## 2.2 Agents for Data Analytics

### Concept

AI can help business users understand large amounts of business data.

Instead of asking a user to manually examine reports, the user can ask a
natural-language question.

Example:

> Which products generated the most support cases last quarter?

The AI can help retrieve and analyze the relevant data.

### Architecture Perspective

The architect should identify:

-   Which business data is required
-   Where the data is stored
-   Whether the data is accurate
-   Whether the data is current
-   What analysis is required
-   Who is allowed to access the data
-   Whether the result requires human interpretation

### Whiteboard Architecture

``` text
Business Question
       ↓
     AI Agent
       ↓
   Business Data
       ↓
     Analysis
       ↓
Trends / Patterns / Insights
       ↓
Business User
```

### Architect Questions

**Q: What is the main value of AI for business analytics?**

**Expected answer:** It helps users understand business data and obtain
insights using natural language.

**Q: What must the architect identify before connecting AI to business
data?**

**Expected answer:** The required data, data source, quality, security,
permissions, and analysis requirements.

**Q: Can AI analytics use poor-quality data?**

**Expected answer:** It can, but poor-quality data can produce
unreliable results.

------------------------------------------------------------------------

## 2.3 Agents for Decision-Making

### Concept

AI can help people make decisions by analyzing information and
identifying patterns.

Example:

> Which customers may require additional attention?

The AI can analyze customer information and provide useful signals or
recommendations.

The AI does not automatically need to make the final decision.

### Architecture Perspective

The architect should determine:

-   What information is required
-   What decision is being supported
-   How risky the decision is
-   Whether AI should recommend or act
-   Where human approval is required
-   How the recommendation will be evaluated

### Whiteboard Architecture

``` text
Business Data
     +
Business Knowledge
     +
Historical Information
        ↓
     AI Agent
        ↓
     Analysis
        ↓
Risk / Pattern / Recommendation
        ↓
Human Decision
```

### Architect Questions

**Q: Should AI automatically make every business decision?**

**Expected answer:** No. The architect must determine where AI supports
the decision and where human approval is required.

**Q: What should determine the level of human involvement?**

**Expected answer:** The business impact, risk, sensitivity, and
consequences of an incorrect decision.

**Q: What is the role of AI in decision support?**

**Expected answer:** AI analyzes information and provides insights or
recommendations that help the human make a decision.

------------------------------------------------------------------------

# Topic 3 --- Review Data for Grounding, Accuracy, Relevance, Timeliness, Cleanliness, and Availability

## 3.1 Grounding

### Concept

Grounding means providing the AI with trusted business information so it
can use relevant organizational context when generating a response.

Without grounding:

``` text
User Question
     ↓
AI Model
     ↓
General Model Knowledge
     ↓
Response
```

With grounding:

``` text
User Question
     ↓
AI Agent
     ↓
Trusted Business Data
     ↓
Relevant Context
     ↓
AI Model
     ↓
Grounded Response
```

Grounding is especially important for business information that changes
over time or is specific to an organization.

### Architecture Perspective

The architect should identify:

-   Which business information the AI needs
-   Which sources are authoritative
-   How the AI retrieves information
-   How access permissions are enforced
-   How information is updated
-   How outdated information is removed

### Whiteboard Architecture

``` text
User Question
      ↓
AI Agent
      ↓
Retrieve Relevant Information
      ↓
Approved Business Knowledge
      ↓
Relevant Context
      ↓
AI Response
```

### Architect Questions

**Q: What is grounding?**

**Expected answer:** Using trusted business data to provide relevant
context to the AI.

**Q: Why is grounding important?**

**Expected answer:** It helps the AI generate responses based on
relevant organizational information.

**Q: Does grounding guarantee a correct answer?**

**Expected answer:** No. The quality of the grounding data and retrieval
process still affects the result.

------------------------------------------------------------------------

# 3.2 Accuracy

### Concept

Accuracy means the information is correct.

Example:

``` text
Old Policy:
Warranty = 12 months

Current Policy:
Warranty = 24 months
```

If the AI uses the old policy, it can provide the wrong answer.

### Architecture Perspective

The architect should identify:

-   Authoritative data sources
-   Data owners
-   Validation processes
-   Conflicting versions
-   Update processes

### Whiteboard Architecture

``` text
Business Data
     ↓
Validate
     ↓
Approved Information
     ↓
AI Knowledge
     ↓
AI Response
```

### Architect Question

**Q: How do we improve data accuracy?**

**Expected answer:** Use trusted, validated, authoritative data and
establish ownership and maintenance processes.

------------------------------------------------------------------------

# 3.3 Relevance

### Concept

Relevance means the information actually applies to the user's question.

Example:

``` text
User:
How do I troubleshoot X200 overheating?

Relevant:
X200 Troubleshooting Guide

Not Relevant:
Employee Holiday Policy
```

### Architecture Perspective

The architect should make sure the AI can retrieve information that
matches the user's request.

### Whiteboard Architecture

``` text
User Question
      ↓
Search / Retrieval
      ↓
Relevant Information
      ↓
AI
      ↓
Response
```

### Architect Question

**Q: Why does relevance matter?**

**Expected answer:** Irrelevant information can lead to an incorrect or
unhelpful AI response.

------------------------------------------------------------------------

# 3.4 Timeliness

### Concept

Timeliness means the data is current enough for the business
requirement.

Example:

``` text
2024 Policy
     ↓
Old

2026 Policy
     ↓
Current
```

An AI solution that uses outdated business policies can provide outdated
answers.

### Architecture Perspective

The architect should determine:

-   How frequently the data changes
-   How quickly AI knowledge must reflect changes
-   Who owns updates
-   How old information is retired
-   Whether the AI should use the latest approved version

### Whiteboard Architecture

``` text
Business Update
      ↓
Update Source
      ↓
Refresh / Reindex
      ↓
AI Knowledge
      ↓
Current Response
```

### Architect Question

**Q: Why is data freshness important?**

**Expected answer:** Because outdated data can cause the AI to provide
outdated business information.

------------------------------------------------------------------------

# 3.5 Cleanliness

### Concept

Clean data is organized and does not contain unnecessary duplicates,
conflicting versions, or excessive noise.

Poor example:

``` text
Warranty-final.docx
Warranty-final2.docx
Warranty-final-NEW.docx
Warranty-old.docx
Warranty-copy.docx
```

Better:

``` text
Warranty Policy
Version: 2026
Status: Approved
Owner: Legal
```

### Architecture Perspective

The architect should consider:

-   Duplicate documents
-   Conflicting versions
-   Inconsistent naming
-   Unnecessary content
-   Metadata
-   Ownership
-   Document lifecycle

### Whiteboard Architecture

``` text
Raw Business Data
       ↓
Remove Duplicates
       ↓
Resolve Conflicts
       ↓
Organize
       ↓
Approved Data
       ↓
AI Knowledge
```

### Architect Question

**Q: Why does clean data matter for AI?**

**Expected answer:** Clean and well-organized data improves the ability
of AI systems to retrieve useful information.

------------------------------------------------------------------------

# 3.6 Availability

### Concept

Availability means the required information can be accessed by the
solution while respecting security and permissions.

Example:

``` text
HR Confidential Data
       ↓
HR Employees Only
```

A general employee should not receive confidential HR information simply
because an AI system can technically access it.

### Architecture Perspective

The architect must consider:

-   Identity
-   Access control
-   Permissions
-   Data location
-   Connectivity
-   Availability of the source
-   Security boundaries

### Whiteboard Architecture

``` text
User
 ↓
Identity
 ↓
Permissions
 ↓
AI Agent
 ↓
Allowed Business Data
 ↓
Response
```

### Architect Questions

**Q: What does data availability mean for AI?**

**Expected answer:** The required data must be accessible to the AI
solution while respecting user permissions.

**Q: Can an AI agent access all enterprise information?**

**Expected answer:** No. Access must follow the user's authorized
permissions and security controls.

------------------------------------------------------------------------

# Topic 4 --- Organize Business Solution Data for AI Systems

## 4.1 Business Data Sources

### Concept

Business information normally exists in many systems.

Examples:

-   SharePoint
-   OneDrive
-   Dataverse
-   CRM
-   ERP
-   Databases
-   Azure Storage
-   APIs
-   Business applications

The architect must determine which data the AI solution actually needs.

### Architecture Perspective

Do not connect every enterprise data source just because it is
available.

The architect should identify:

-   Required data
-   Source system
-   Data owner
-   Data quality
-   Security
-   Update frequency
-   Integration method
-   AI access requirement

### Whiteboard Architecture

``` text
SharePoint ───────┐
CRM ──────────────┤
ERP ──────────────┤
Database ─────────┤
Business Apps ────┘
        ↓
   Required Data
        ↓
   AI Solution
```

### Architect Questions

**Q: Should every enterprise data source be connected to the AI
solution?**

**Expected answer:** No. Connect only the data required for the business
scenario.

**Q: What should determine which data is included?**

**Expected answer:** The business requirement, AI capability, security,
data quality, and required context.

------------------------------------------------------------------------

# 4.2 Organize and Prepare Data

### Concept

AI-ready data should be:

-   Relevant
-   Accurate
-   Current
-   Clean
-   Accessible
-   Governed

The basic flow is:

``` text
Source Data
    ↓
Clean
    ↓
Organize
    ↓
Govern
    ↓
Index / Search
    ↓
AI
```

### Architecture Perspective

The architect should design the data flow before designing the agent.

The agent depends on the data architecture underneath it.

### Whiteboard Architecture

``` text
              BUSINESS DATA
                    ↓
           Clean / Transform
                    ↓
            Govern / Secure
                    ↓
             Index / Search
                    ↓
            Retrieve Context
                    ↓
              AI / Agent
                    ↓
             Business User
```

### Architect Questions

**Q: Why should the architect consider data architecture before the
agent?**

**Expected answer:** The agent depends on reliable, accessible, secure,
and relevant data.

**Q: What is the basic data preparation flow?**

**Expected answer:** Collect, clean, organize, govern, index, retrieve,
and provide the required context to AI.

------------------------------------------------------------------------

# 4.3 Data Access and Security

### Concept

AI should not bypass existing business security.

If an employee cannot access a document normally, the AI solution should
not expose that document to the employee.

### Architecture Perspective

The architect should consider:

-   Identity
-   Authentication
-   Authorization
-   Role-based access
-   Data permissions
-   Sensitive information
-   Compliance
-   Audit requirements

### Whiteboard Architecture

``` text
Employee
   ↓
Identity
   ↓
Authorization
   ↓
Approved Data
   ↓
AI Retrieval
   ↓
Response
```

### Architect Questions

**Q: What is the key security principle for enterprise AI data?**

**Expected answer:** AI access should respect existing identity,
authorization, and data permissions.

**Q: Why is permission-aware retrieval important?**

**Expected answer:** It prevents users from receiving information they
are not authorized to access.

------------------------------------------------------------------------

# 4.4 RAG --- Retrieval-Augmented Generation

### Concept

RAG means the AI retrieves relevant business information before
generating the answer.

Think of it as:

> Search first, then answer.

### Basic RAG Architecture

``` text
User Question
      ↓
AI Agent
      ↓
Retrieve Relevant Data
      ↓
Business Knowledge
      ↓
Relevant Context
      ↓
Generative AI
      ↓
Answer
```

### Architecture Perspective

The architect should consider:

-   What data should be retrieved?
-   Where is it stored?
-   How is it indexed?
-   How is relevance determined?
-   How are permissions enforced?
-   How often is the index updated?
-   How is retrieval quality tested?

### Architect Questions

**Q: What is RAG?**

**Expected answer:** A pattern where relevant business information is
retrieved and provided as context to generative AI before it produces a
response.

**Q: Why use RAG for enterprise AI?**

**Expected answer:** To provide the AI with relevant organizational
information without relying only on general model knowledge.

**Q: What is critical for a RAG solution?**

**Expected answer:** Good source data, effective retrieval, current
information, and proper security.

------------------------------------------------------------------------

# 4.5 Overall AI Data Architecture

### Concept

A business AI solution normally has several layers.

``` text
                BUSINESS SYSTEMS
                       │
       ┌───────────────┼───────────────┐
       ↓               ↓               ↓
   Documents        Databases       Business Apps
       │               │               │
       └───────────────┼───────────────┘
                       ↓
                 DATA LAYER
                       ↓
              Clean / Organize
                       ↓
              Govern / Secure
                       ↓
               Search / Index
                       ↓
               Retrieve Context
                       ↓
                 AI / Agent
                       ↓
              Business Solution
```

### Architecture Perspective

The architect must design the complete path from business data to AI
response.

The agent is not the whole solution.

### Architect Questions

**Q: What is the architect designing beyond the AI agent?**

**Expected answer:** The complete data, security, integration,
retrieval, AI, and business-process architecture.

**Q: Why is the data layer important?**

**Expected answer:** Because the quality, availability, security, and
organization of the data directly affect the usefulness of the AI
solution.

------------------------------------------------------------------------

# Module 2 --- Final Whiteboard

Final Module 2 Architecture

``` text
                    BUSINESS REQUIREMENT
                            ↓
                   What needs to improve?
                            ↓
             ┌──────────────┼──────────────┐
             ↓              ↓              ↓
         AUTOMATE        ANALYZE        SUPPORT
         TASKS           DATA           DECISIONS
             └──────────────┼──────────────┘
                            ↓
                       AI / AGENT
                            ↓
                      REQUIRED DATA
                            ↓
              Is the data good enough?
                            ↓
       ┌──────────┬──────────┬──────────┬──────────┬──────────┐
       ↓          ↓          ↓          ↓          ↓
   Accurate   Relevant   Timely     Clean    Available
       └──────────┴──────────┴──────────┴──────────┴──────────┘
                            ↓
                    ORGANIZE DATA
                            ↓
                 Govern / Secure / Index
                            ↓
                     Search / RAG
                            ↓
                     AI SOLUTION
                            ↓
                    BUSINESS OUTCOME
```

# Module 2 --- Final Architect Questions

**Q: What should come first in an AI solution?**

**Expected answer:** The business requirement and desired business
outcome.

**Q: What are the three major agent use areas covered in this module?**

**Expected answer:** Task automation, data analytics, and decision
support.

**Q: What is grounding?**

**Expected answer:** Providing trusted business information as context
for the AI.

**Q: What five data qualities should the architect review?**

**Expected answer:** Accuracy, relevance, timeliness, cleanliness, and
availability.

**Q: Why does data quality matter for AI?**

**Expected answer:** Poor data can produce unreliable or irrelevant AI
results.

**Q: What is RAG?**

**Expected answer:** Retrieve relevant business information and use it
as context when generating the AI response.

**Q: Should AI have unrestricted access to enterprise data?**

**Expected answer:** No. AI must respect identity, permissions,
security, and governance.

**Q: What should the architect connect to the AI solution?**

**Expected answer:** Only the data and systems required to satisfy the
business requirement.

**Q: What is the key architectural lesson from Module 2?**

**Expected answer:** Define the AI requirement first, then ensure the
required business data is accurate, relevant, current, clean, available,
secure, and organized for AI consumption.
