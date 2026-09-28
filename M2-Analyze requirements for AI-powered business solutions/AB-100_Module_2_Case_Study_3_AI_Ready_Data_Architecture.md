# AB-100 Module 2 --- Case Study 3: Designing an AI-Ready Data Architecture

## Scenario

Contoso is a manufacturing company with a large customer-support team.

Customer-service employees receive questions about:

-   Product troubleshooting
-   Warranty policies
-   Customer history
-   Previous support cases
-   Current product and operational information

Today, employees have to search multiple systems to answer a customer
question.

### Current Process

``` text
Customer Question
       ↓
Support Employee
       ↓
Search SharePoint
       ↓
Search CRM
       ↓
Search Support Database
       ↓
Check Operational Data
       ↓
Understand Information
       ↓
Write Customer Response
```

This process takes time because the required information is distributed
across different business systems.

Contoso wants to provide an AI customer-support agent that can retrieve
relevant business information and help employees answer customer
questions.

The agent should also be able to perform selected business actions, such
as creating a support case.

------------------------------------------------------------------------

## Business Requirement

The AI solution should help support employees:

-   Find product information
-   Find troubleshooting information
-   Check warranty information
-   Understand customer history
-   Review previous support cases
-   Create support cases when required

The AI solution must use approved business information and respect
existing security and permissions.

------------------------------------------------------------------------

## Architect's Challenge

The architect must determine:

1.  Which business data is actually required.
2.  Where the required data currently exists.
3.  Whether the data is accurate, relevant, current, clean, and
    available.
4.  How the data should be organized for AI consumption.
5.  How security and permissions should be maintained.
6.  How the AI can retrieve relevant information.
7.  How the AI can perform approved business actions.

### Current Data Sources

``` text
Product Manuals       → SharePoint
Warranty Policies     → SharePoint
Customer Information  → CRM
Support Cases         → Database
Operational Data      → Azure SQL
```

The architect must design how this information becomes available to the
AI solution.

------------------------------------------------------------------------

# Step 1 --- Identify Required Data

The business requirement is:

> Help support employees answer customer questions and create support
> cases.

The architect identifies the information required by the AI solution.

  Requirement                   Data Source
  ----------------------------- -------------
  Product information           SharePoint
  Troubleshooting information   SharePoint
  Warranty information          SharePoint
  Customer information          CRM
  Previous support cases        Database
  Operational information       Azure SQL

The architect should not assume that every available enterprise data
source is required.

The data should be selected based on the business scenario.

### Architecture Decision

``` text
Enterprise Data
      ↓
Business Requirement
      ↓
Required Data
      ↓
AI Data Sources
```

------------------------------------------------------------------------

# Step 2 --- Do Not Connect Everything Automatically

Contoso has many enterprise systems, but the architect should not
connect every system to the AI solution.

For each potential data source, the architect asks:

-   Is this data required?
-   Is the data relevant?
-   Is the data accurate?
-   Who owns the data?
-   Who can access the data?
-   How often does it change?
-   How will the AI retrieve it?
-   Does the data contain sensitive information?

### Example

Suppose Contoso has an internal employee-holiday system.

The customer-support agent does not need employee holiday information.

Therefore:

``` text
Employee Holiday System
          ↓
Not required
          ↓
Do not include in AI data scope
```

### Architecture Decision

``` text
Enterprise Data
      ↓
Business Requirement
      ↓
Required Data
      ↓
AI Data Sources
```

------------------------------------------------------------------------

# Step 3 --- Review Data Quality

Before connecting the selected data to the AI solution, the architect
reviews its quality.

The five important dimensions are:

-   Accuracy
-   Relevance
-   Timeliness
-   Cleanliness
-   Availability

### Data Quality Review

``` text
Required Data
      ↓
┌──────────────┐
│   Accurate?  │
└──────────────┘
      ↓
┌──────────────┐
│   Relevant?  │
└──────────────┘
      ↓
┌──────────────┐
│   Current?   │
└──────────────┘
      ↓
┌──────────────┐
│    Clean?    │
└──────────────┘
      ↓
┌──────────────┐
│  Available?  │
└──────────────┘
```

### Example

The architect discovers that Contoso has two warranty documents:

``` text
Warranty Policy 2024
Warranty Policy 2026
```

The 2024 document says:

> Warranty period: 12 months

The 2026 document says:

> Warranty period: 24 months

If both documents are available to the AI without proper organization,
the agent may retrieve outdated information.

The architect must establish which document is authoritative and ensure
that the AI uses the approved information.

------------------------------------------------------------------------

# Step 4 --- Apply Security and Permissions

The AI solution must respect existing business permissions.

For example, customer information is stored in the CRM.

A support employee should only receive customer information that the
employee is authorized to access.

### Security Flow

``` text
Customer Data
      ↓
CRM Permissions
      ↓
Employee Identity
      ↓
Authorization
      ↓
AI Retrieval
      ↓
Allowed Information
```

The AI should not bypass the organization's security model.

### Example

Employee A has access to Customer A.

Employee B does not have access to Customer A.

The AI should not allow Employee B to retrieve Customer A's information
simply because the AI can technically access the CRM.

### Architecture Principle

``` text
User Identity
      ↓
Permissions
      ↓
Allowed Data
      ↓
AI Retrieval
      ↓
AI Response
```

------------------------------------------------------------------------

# Step 5 --- Organize the Data

The required data exists across multiple systems.

The architect needs to create an AI-ready path from those systems to the
AI solution.

The data should be:

-   Relevant
-   Accurate
-   Current
-   Clean
-   Accessible
-   Governed
-   Secure

### AI-Ready Data Flow

``` text
SharePoint ───────┐
CRM ──────────────┤
Support Database ─┤
Azure SQL ────────┘
        ↓
   Required Data
        ↓
Clean / Organize
        ↓
Govern / Secure
        ↓
Index / Search
        ↓
Retrieve Relevant Context
        ↓
AI Support Agent
```

### Why Organize the Data?

The data exists in different systems and cannot simply be exposed to the
AI without planning.

The architect needs to make sure that the required information can be:

-   Accessed by the solution
-   Retrieved efficiently
-   Kept current
-   Secured according to user permissions
-   Used as reliable context for AI responses

The goal is to create an AI-ready path from the original business
systems to the AI solution.

------------------------------------------------------------------------

# Step 6 --- Use Retrieval-Augmented Generation

The support employee asks:

> What should I do if the X200 overheats?

The AI should not rely only on general model knowledge.

Instead, the solution can retrieve relevant Contoso information and
provide that information as context for the AI response.

This is the basic idea of **Retrieval-Augmented Generation (RAG)**.

### Why RAG?

RAG allows the AI solution to:

-   Retrieve relevant business information
-   Use organization-specific knowledge
-   Use current information when the knowledge source is maintained
-   Generate a response based on retrieved context

### RAG Architecture

``` text
Employee Question
       ↓
AI Support Agent
       ↓
Search / Retrieval
       ↓
Relevant Business Information
       ↓
Context
       ↓
Generative AI
       ↓
Grounded Response
       ↓
Employee
```

### Example

Employee asks:

> What should I do if the X200 overheats?

The AI retrieves:

``` text
X200 Troubleshooting Guide
        +
X200 Product Manual
        +
Relevant Support Information
```

Then the AI generates a response based on the retrieved information.

------------------------------------------------------------------------

# Step 7 --- Add Business Actions

The AI solution should not only answer questions.

The support employee may ask:

> Create a high-priority support case for Fabrikam because the X200 is
> overheating.

The agent now needs to perform a business action.

### Knowledge vs. Action

**Knowledge** helps the agent understand or answer a question.

**Action** allows the agent to perform a business operation.

### Architecture

``` text
Employee
   ↓
AI Support Agent
   ├───────────────┐
   ↓               ↓
Knowledge        Action
   ↓               ↓
Answer         Create Case
                   ↓
              Support System
```

### Example

``` text
Employee
   ↓
"Create a support case"
   ↓
AI Support Agent
   ↓
Validate Required Information
   ↓
Invoke Action
   ↓
Support System
   ↓
Case Created
   ↓
Confirmation to Employee
```

------------------------------------------------------------------------

# Final Architecture

``` text
                    ENTERPRISE DATA
                          │
       ┌──────────────────┼──────────────────┐
       ↓                  ↓                  ↓
   Documents           CRM / Apps         Databases
       │                  │                  │
       └──────────────────┼──────────────────┘
                          ↓
                  Required Data
                          ↓
                Clean / Organize
                          ↓
                  Govern / Secure
                          ↓
                   Search / Index
                          ↓
                 Retrieve Context
                          ↓
                 AI Support Agent
                    /          \
                   ↓            ↓
              Knowledge       Actions
                   ↓            ↓
              Grounded       Business
               Answer         Process
```

------------------------------------------------------------------------

# End-to-End Example

A support employee receives a customer request:

> Our X200 machine is overheating after three hours of operation. What
> should I check?

The solution works as follows:

``` text
Customer Request
       ↓
AI Support Agent
       ↓
Retrieve Relevant Information
       ↓
X200 Troubleshooting Guide
       +
X200 Product Manual
       +
Customer Information
       ↓
Generate Grounded Response
       ↓
Support Employee
       ↓
Employee Decides Next Action
       ↓
Create Support Case
       ↓
Business System
```

------------------------------------------------------------------------

# Architect Questions

**Q: Should all enterprise data be connected to the AI solution?**

**Expected answer:** No. Only data required for the business scenario
should be included.

**Q: What should determine which data is selected?**

**Expected answer:** Business requirements, relevance, quality,
security, permissions, and AI requirements.

**Q: Why is data organization important?**

**Expected answer:** Organized data makes it easier for AI systems to
find and use relevant information.

**Q: What are the key data-quality dimensions to review?**

**Expected answer:** Accuracy, relevance, timeliness, cleanliness, and
availability.

**Q: What is RAG?**

**Expected answer:** A pattern where relevant business information is
retrieved and provided as context to generative AI.

**Q: Why use RAG for enterprise AI?**

**Expected answer:** To provide the AI with relevant
organization-specific information when generating a response.

**Q: What should the architect consider when designing RAG?**

**Expected answer:** Data sources, indexing, retrieval quality,
freshness, permissions, security, and monitoring.

**Q: Why are permissions important in AI data retrieval?**

**Expected answer:** They prevent the AI from exposing information to
users who are not authorized to access it.

**Q: What is the difference between knowledge and an action?**

**Expected answer:** Knowledge helps the agent answer or understand
information; an action allows the agent to perform a business operation.

**Q: Why is the data architecture important to the AI solution?**

**Expected answer:** The AI agent depends on reliable, relevant,
current, secure, and accessible business data.

**Q: What should the architect consider before adding a data source?**

**Expected answer:** Business relevance, data quality, ownership,
security, permissions, freshness, and the AI requirement.

------------------------------------------------------------------------

# Key Takeaway

``` text
Business Requirement
        ↓
Required Data
        ↓
Data Quality
        ↓
Security & Governance
        ↓
Organize / Index
        ↓
Retrieve Relevant Context
        ↓
AI Agent
        ↓
Knowledge + Actions
        ↓
Business Outcome
```

> **The AI agent is only one part of the solution. The data architecture
> underneath it is equally important.**
