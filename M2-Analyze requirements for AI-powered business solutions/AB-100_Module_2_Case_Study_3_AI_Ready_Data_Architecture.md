# AB-100 Module 2 --- Case Study 3: Designing AI-Ready Business Data

## Scenario

Contoso wants to build an AI customer-support agent.

The information required by the agent exists across multiple systems.

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

## Step 1 --- Identify Required Data

The business requirement is:

> Help support employees answer customer questions and create support
> cases.

The architect identifies the required information.

  Requirement                   Data Source
  ----------------------------- -------------
  Product information           SharePoint
  Troubleshooting information   SharePoint
  Warranty information          SharePoint
  Customer information          CRM
  Previous support cases        Database
  Operational information       Azure SQL

------------------------------------------------------------------------

## Step 2 --- Do Not Connect Everything Automatically

The architect should not connect every enterprise system to the AI
solution.

The architect asks:

-   Is this data required?
-   Is the data relevant?
-   Is the data accurate?
-   Who owns the data?
-   Who can access the data?
-   How often does it change?
-   How will the AI retrieve it?

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

## Step 3 --- Review Data Quality

Each selected source is reviewed.

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

------------------------------------------------------------------------

## Step 4 --- Apply Security

The AI solution must respect existing permissions.

For example:

``` text
Customer Data
      ↓
CRM Permissions
      ↓
Authorized User
      ↓
AI Retrieval
      ↓
Allowed Information
```

An employee should not receive customer information that they are not
authorized to access.

------------------------------------------------------------------------

## Step 5 --- Organize the Data

The architect creates an AI-ready data flow.

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

------------------------------------------------------------------------

## Step 6 --- Use Retrieval-Augmented Generation

The support employee asks:

> What should I do if the X200 overheats?

The AI retrieves relevant information before generating the response.

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

------------------------------------------------------------------------

## Step 7 --- Add Business Actions

The employee may ask:

> Create a high-priority support case for Fabrikam because the X200 is
> overheating.

The AI needs both knowledge and an action.

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

------------------------------------------------------------------------

## Final Architecture

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

## Architect Questions

**Q: Should all enterprise data be connected to the AI solution?**

**Expected answer:** No. Only data required for the business scenario
should be included.

**Q: What should determine which data is selected?**

**Expected answer:** Business requirements, relevance, quality,
security, permissions, and AI requirements.

**Q: Why is data organization important?**

**Expected answer:** Organized data makes it easier for AI systems to
find and use relevant information.

**Q: What is RAG?**

**Expected answer:** A pattern where relevant business information is
retrieved and provided as context to generative AI.

**Q: What should the architect consider when designing RAG?**

**Expected answer:** Data sources, indexing, retrieval quality,
freshness, permissions, security, and monitoring.

**Q: Why are permissions important in AI data retrieval?**

**Expected answer:** They prevent the AI from exposing information to
users who are not authorized to access it.

**Q: What is the difference between knowledge and an action?**

**Expected answer:** Knowledge helps the agent answer or understand
information; an action allows the agent to perform a business operation.

------------------------------------------------------------------------

## Key Takeaway

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
