# AB-100 Module 2 --- Hands-On Lab Guide

## Lab Overview

These three labs use different Microsoft platforms deliberately.

  -----------------------------------------------------------------------
  Lab               Module 2 concept  Platform          Architect skill
  ----------------- ----------------- ----------------- -----------------
  Lab 1 --- Choose  Task automation,  Microsoft 365     Identify the
  the Right AI      data analytics,   Copilot + Copilot right AI approach
  Approach          decision support  Chat              

  Lab 2 --- Fix AI  Accuracy,         Microsoft Copilot Diagnose and
  Data Quality and  relevance,        Studio            improve AI
  Grounding         timeliness,                         grounding
                    cleanliness,                        
                    availability,                       
                    grounding                           

  Lab 3 --- Build   Data sources,     Microsoft Copilot Design an
  an AI-Ready Data  security, RAG,    Studio +          AI-ready data
  Architecture      knowledge +       SharePoint        architecture
                    actions                             
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Lab 1 --- Choose the Right AI Approach

## Platform

**Microsoft 365 Copilot Chat + Microsoft 365 Copilot**

## Objective

Determine whether three business requirements are primarily:

-   Task automation
-   Data analytics
-   Decision support

## Scenario

Contoso Manufacturing has three customer-service challenges:

1.  Employees manually summarize customer emails.
2.  Managers analyze monthly support reports manually.
3.  Managers need to identify customers who may require additional
    attention.

The architect must determine the appropriate AI approach for each
requirement.

------------------------------------------------------------------------

## Part 1 --- Task Automation

### Step 1 --- Open Microsoft 365 Copilot Chat

Open Microsoft 365 Copilot Chat and sign in with your organizational
account.

### Step 2 --- Use the sample customer email

Open:

`Lab_1_Customer_Email_X200.txt`

Use the content as the input to Copilot.

### Step 3 --- Ask Copilot

``` text
Summarize this customer email for a support case.

Include:
- Customer issue
- Product
- Symptoms
- Troubleshooting already attempted
- Recommended next step
```

### Step 4 --- Review the result

Ask:

> What work did AI perform?

Expected answer:

> A repetitive information-processing task was automated.

### Architecture

``` text
Customer Email
      ↓
Microsoft 365 Copilot
      ↓
Understand Information
      ↓
Generate Summary
      ↓
Employee Review
      ↓
Support Case
```

### Architect Decision

**Task automation / AI-assisted productivity**

------------------------------------------------------------------------

# Part 2 --- Data Analytics

## Step 1 --- Open the sample support data

Open:

`Lab_1_Customer_Service_Data.xlsx`

The workbook contains sample monthly customer-service data.

## Step 2 --- Ask Copilot

``` text
Analyze this customer-service data.

Identify:
1. Which product has the most support cases?
2. Which product shows the largest increase?
3. What trends should a customer-service manager investigate?
```

## Step 3 --- Ask a follow-up

``` text
What additional business data would you need before
making a decision based on these trends?
```

Expected discussion:

> AI analysis is only as useful as the underlying business data.

### Architecture

``` text
Business Question
       ↓
Microsoft 365 Copilot
       ↓
Business Data
       ↓
Analysis
       ↓
Trends / Patterns
       ↓
Manager
```

### Architect Decision

**Data analytics**

------------------------------------------------------------------------

# Part 3 --- Decision Support

## Step 1 --- Open the sample customer-risk data

Open:

`Lab_1_Customer_Risk_Data.xlsx`

## Step 2 --- Ask Copilot

``` text
Review this customer-service information.

Identify customers who may require additional attention.

For each customer:
- Explain the factors you considered.
- Identify possible risk indicators.
- Do not make the final business decision.
```

## Step 3 --- Discuss the result

Ask:

> Should the AI automatically decide which customer receives special
> treatment?

Expected answer:

> Not necessarily. The architect should determine the appropriate level
> of human review based on business impact and risk.

### Architecture

``` text
Customer Data
      +
Support History
      ↓
Microsoft 365 Copilot
      ↓
Analysis
      ↓
Risk Indicators
      ↓
Manager
      ↓
Human Decision
```

### Lab 1 Takeaway

``` text
Business Requirement
        ↓
What does AI need to do?
        ↓
┌────────────┬────────────┬──────────────┐
↓            ↓            ↓
Automate     Analyze      Support
Tasks        Data         Decisions
↓            ↓            ↓
AI           AI           AI
Assistance   Analytics    Recommendation
```

------------------------------------------------------------------------

# Lab 2 --- Fix AI Data Quality and Grounding

## Platform

**Microsoft Copilot Studio**

## Objective

Diagnose an incorrect AI answer by evaluating:

-   Accuracy
-   Relevance
-   Timeliness
-   Cleanliness
-   Availability
-   Grounding

## Scenario

Contoso has an AI support assistant.

Employee asks:

> What is the warranty period for the X200?

The agent responds:

> The warranty period is 12 months.

But the current Contoso policy says:

> The warranty period is 24 months.

------------------------------------------------------------------------

# Part 1 --- Prepare the Knowledge Sources

Use these files from the lab artifact pack:

-   `Lab_2_Warranty-final.docx`
-   `Lab_2_Warranty_Policy_2026.docx`

The old document contains:

``` text
Warranty period: 12 months
```

The current approved document contains:

``` text
Warranty period: 24 months
Status: Approved
Owner: Legal
Effective Date: 2026
```

## Step 1 --- Create the Agent

Open Microsoft Copilot Studio.

Create:

``` text
Name:
Contoso Warranty Support Agent
```

Purpose:

``` text
Help Contoso customer-service employees answer questions
about product warranties and support policies.
```

## Step 2 --- Add the old warranty document

Add:

`Lab_2_Warranty-final.docx`

as a knowledge source.

## Step 3 --- Test

Ask:

``` text
What is the warranty period for the X200?
```

Observe whether the agent retrieves the old 12-month information.

------------------------------------------------------------------------

# Part 2 --- Diagnose the Problem

Evaluate the five data-quality dimensions.

  -----------------------------------------------------------------------
  Dimension                           Finding
  ----------------------------------- -----------------------------------
  Accuracy                            Old document contains
                                      incorrect/currently invalid
                                      information

  Relevance                           Warranty document is relevant

  Timeliness                          Document is outdated

  Cleanliness                         Multiple versions create confusion

  Availability                        Current policy is not correctly
                                      retrieved
  -----------------------------------------------------------------------

Ask:

> Is the AI model necessarily the problem?

Expected answer:

> No. The grounding data or retrieval process may be the problem.

------------------------------------------------------------------------

# Part 3 --- Correct the Knowledge

Add:

`Lab_2_Warranty_Policy_2026.docx`

Remove or exclude the outdated source according to the organization's
information-management process.

The approved document contains:

``` text
Warranty Policy
Version: 2026
Status: Approved
Owner: Legal
Effective Date: 2026
Warranty Period: 24 months
```

------------------------------------------------------------------------

# Part 4 --- Test Again

Ask:

``` text
What is the warranty period for the X200?
```

Expected result:

``` text
24 months
```

### Validation Architecture

``` text
User Question
      ↓
Copilot Studio Agent
      ↓
Knowledge Search
      ↓
Approved Warranty Policy
      ↓
Relevant Context
      ↓
AI Response
```

### Architect Takeaway

> Changing the prompt is not the real solution. Fixing the business
> knowledge and retrieval path is the architectural solution.

------------------------------------------------------------------------

# Lab 3 --- Build an AI-Ready Data Architecture

## Platform

**Microsoft Copilot Studio + SharePoint**

## Objective

Build an AI customer-support agent that uses:

-   Product knowledge
-   Troubleshooting information
-   Warranty policy
-   Customer-service FAQ

Then demonstrate the difference between **knowledge** and **action**.

------------------------------------------------------------------------

# Part 1 --- Prepare SharePoint Knowledge

Create or use a SharePoint training site.

Example:

``` text
Contoso Customer Support
```

Create a document library:

``` text
AI Knowledge
```

Organize the supplied documents as:

``` text
AI Knowledge
│
├── Product
│   └── Lab_3_X200_Product_Manual.docx
│
├── Troubleshooting
│   └── Lab_3_X200_Troubleshooting_Guide.docx
│
├── Policies
│   └── Lab_3_Warranty_Policy.docx
│
└── FAQ
    └── Lab_3_Customer_Service_FAQ.docx
```

This demonstrates data organization and cleanliness.

------------------------------------------------------------------------

# Part 2 --- Create the AI Agent

Open Copilot Studio.

Create:

``` text
Contoso Customer Support Agent
```

Purpose:

``` text
Help Contoso customer-service employees find approved
product, troubleshooting, warranty, and support information.
```

------------------------------------------------------------------------

# Part 3 --- Add SharePoint Knowledge

Open the agent's **Knowledge** configuration.

Add the SharePoint site or appropriate SharePoint location containing
the training documents.

Use a meaningful description:

``` text
Approved product manuals, troubleshooting guides,
warranty policies, and customer-service FAQs for
Contoso support employees.
```

------------------------------------------------------------------------

# Part 4 --- Test RAG

Ask:

``` text
What should I do if the X200 overheats?
```

The agent should retrieve relevant information from the troubleshooting
and product documents.

### Architecture

``` text
Employee Question
       ↓
Copilot Studio Agent
       ↓
SharePoint Search
       ↓
Relevant Documents
       ↓
Retrieved Context
       ↓
Generative AI
       ↓
Grounded Answer
```

------------------------------------------------------------------------

# Part 5 --- Test Different Questions

Test:

``` text
What is the X200 warranty period?
```

Then:

``` text
What should I check before opening a support case?
```

Then:

``` text
What information should I collect from the customer?
```

Then:

``` text
What does the warranty policy exclude?
```

Observe that different questions retrieve different business
information.

------------------------------------------------------------------------

# Part 6 --- Test an Unavailable Question

Ask:

``` text
What is the expected sales volume for the X200 next year?
```

Discuss:

> Is this information available in the configured knowledge?

Expected answer:

> No.

The architect must define the scope of the knowledge architecture.

------------------------------------------------------------------------

# Part 7 --- Discuss Security

Ask:

> If an employee does not have permission to access a SharePoint
> document, should the AI expose the document's contents?

Expected answer:

> No. The AI solution should respect the user's permissions.

### Architecture

``` text
Employee
    ↓
Microsoft Identity
    ↓
SharePoint Permissions
    ↓
Authorized Content
    ↓
AI Retrieval
    ↓
Grounded Response
```

------------------------------------------------------------------------

# Part 8 --- Extend the Agent with an Action

Introduce:

> Knowledge allows the agent to read information. Actions allow the
> agent to do something.

Create a simple training action such as:

``` text
Create Support Case
```

The action can write to a suitable training data source available in the
environment.

Test:

``` text
Create a high-priority support case for Fabrikam.
The X200 is overheating.
```

### Architecture

``` text
Employee
   ↓
AI Support Agent
   ↓
Understand Request
   ↓
Validate Required Information
   ↓
Create Support Case Action
   ↓
Business System
   ↓
Case Created
   ↓
Confirmation
```

------------------------------------------------------------------------

# Final Module 2 Lab Architecture

``` text
                         BUSINESS REQUIREMENT
                                │
                                ↓
                     What does AI need to do?
                                │
              ┌─────────────────┼─────────────────┐
              ↓                 ↓                 ↓
          Automate           Analyze           Support
            Tasks             Data             Decisions
              │                 │                 │
              └─────────────────┼─────────────────┘
                                ↓
                         AI / Agent Solution
                                │
                                ↓
                         Required Data
                                │
              ┌─────────────────┼─────────────────┐
              ↓                 ↓                 ↓
          SharePoint           CRM             Databases
              │                 │                 │
              └─────────────────┼─────────────────┘
                                ↓
                         Clean / Organize
                                ↓
                         Govern / Secure
                                ↓
                           Index / Search
                                ↓
                         Retrieve Context
                                ↓
                           AI / RAG
                           /       \
                          ↓         ↓
                     Knowledge    Actions
                          ↓         ↓
                     AI Response  Business
                                  Process
```

# Final Architect Questions

**Q: Why did we use Microsoft 365 Copilot for Lab 1?**

**Expected answer:** It provides a practical way to experience
AI-assisted tasks, business-data analysis, and decision support.

**Q: Why did we use Copilot Studio for Lab 2?**

**Expected answer:** It lets us directly configure and test an agent's
knowledge and grounding.

**Q: Why use SharePoint in Lab 3?**

**Expected answer:** It provides a realistic enterprise knowledge source
and demonstrates retrieval, organization, and permission-aware access.

**Q: What is the difference between Lab 2 and Lab 3?**

**Expected answer:** Lab 2 diagnoses and improves grounding quality; Lab
3 designs the broader AI data architecture.

**Q: What is the most important architectural lesson from these labs?**

**Expected answer:** Start with the business requirement, select the
appropriate AI approach, and then design the data, security, retrieval,
and agent architecture needed to support it.
