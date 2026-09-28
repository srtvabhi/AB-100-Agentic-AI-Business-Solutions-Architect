# AB-100 Module 2 --- Hands-On Lab Guide

## Lab Platform Map

These labs deliberately use the Microsoft Copilot experience that best
matches the architecture concept being demonstrated.

  -----------------------------------------------------------------------
  Lab               Platform          Specific Copilot  Main architect
                                      experience        skill
  ----------------- ----------------- ----------------- -----------------
  Lab 1 --- Choose  Microsoft 365     **Microsoft 365   Identify task
  the Right AI                        Copilot Chat**    automation, data
  Approach                            for text-based    analytics, and
                                      assistance and    decision support
                                      **Copilot in      
                                      Excel** for       
                                      structured data   
                                      analysis          

  Lab 2 --- Fix AI  Microsoft Copilot **Copilot Studio  Diagnose
  Data Quality and  Studio            custom agent**    grounding and
  Grounding                           with uploaded     data-quality
                                      knowledge files   problems

  Lab 3 --- Build   Microsoft Copilot **Copilot Studio  Design knowledge,
  an AI-Ready Data  Studio +          custom agent**    retrieval,
  Architecture      SharePoint        with SharePoint   permissions, and
                                      knowledge and a   actions
                                      SharePoint action 
  -----------------------------------------------------------------------

> **Important:** Microsoft 365 Copilot and Microsoft Copilot Studio are
> different experiences. Lab 1 uses Microsoft 365 Copilot. Labs 2 and 3
> use Copilot Studio.

------------------------------------------------------------------------

# Lab 1 --- Choose the Right AI Approach

## Platform

### Part 1 --- Customer Email

**Microsoft 365 Copilot Chat**

Use this for summarization and AI-assisted productivity.

### Parts 2 and 3 --- Business Data

**Copilot in Excel**

Use this for analysis of the supplied Excel workbooks. Copilot in Excel
can surface summaries, trends, outliers, charts, and PivotTables from
workbook data.

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

# Part 1 --- Task Automation

## Step 1 --- Open Microsoft 365 Copilot Chat

Open **Microsoft 365 Copilot Chat** and sign in with your organizational
account.

> **Platform:** Microsoft 365 Copilot Chat

## Step 2 --- Use the sample customer email

Open:

`Lab_1_Customer_Email_X200.txt`

Copy the email content into Microsoft 365 Copilot Chat.

## Step 3 --- Ask Copilot

``` text
Summarize this customer email for a support case.

Include:
- Customer issue
- Product
- Symptoms
- Troubleshooting already attempted
- Recommended next step
```

## Step 4 --- Review the result

Ask:

> What work did AI perform?

**Expected answer:** A repetitive information-processing task was
automated.

## Architecture

``` text
Customer Email
      ↓
Microsoft 365 Copilot Chat
      ↓
Understand Information
      ↓
Generate Summary
      ↓
Employee Review
      ↓
Support Case
```

## Architect Decision

**Task automation / AI-assisted productivity**

------------------------------------------------------------------------

# Part 2 --- Data Analytics

## Platform

**Copilot in Excel**

> Do not use Microsoft 365 Copilot Chat for this step. Open the workbook
> in Excel and use the Copilot experience inside Excel.

## Step 1 --- Open the sample support data

Open:

`Lab_1_Customer_Service_Data.xlsx`

The workbook contains sample monthly customer-service data.

## Step 2 --- Open Copilot in Excel

Open the **Copilot** experience in Excel.

If Copilot is not available in Excel, use an environment where Copilot
in Excel is enabled for the training account.

## Step 3 --- Ask Copilot

``` text
Analyze this customer-service data.

Identify:
1. Which product has the most support cases?
2. Which product shows the largest increase?
3. What trends should a customer-service manager investigate?
```

## Step 4 --- Ask a follow-up

``` text
What additional business data would you need before
making a decision based on these trends?
```

**Expected discussion:** AI analysis is only as useful as the underlying
business data.

## Architecture

``` text
Business Question
       ↓
Copilot in Excel
       ↓
Customer-Service Data
       ↓
Data Analysis
       ↓
Trends / Patterns / Insights
       ↓
Manager
```

## Architect Decision

**Data analytics**

------------------------------------------------------------------------

# Part 3 --- Decision Support

## Platform

**Copilot in Excel**

This keeps the exercise focused on structured business data while
demonstrating the difference between **analysis** and
**decision-making**.

## Step 1 --- Open the customer-risk data

Open:

`Lab_1_Customer_Risk_Data.xlsx`

## Step 2 --- Open Copilot in Excel

Open the **Copilot** experience in Excel.

## Step 3 --- Ask Copilot

``` text
Review this customer-service information.

Identify customers who may require additional attention.

For each customer:
- Explain the factors you considered.
- Identify possible risk indicators.
- Do not make the final business decision.
```

## Step 4 --- Discuss the result

Ask:

> Should the AI automatically decide which customer receives special
> treatment?

**Expected answer:** Not necessarily. The architect should determine the
appropriate level of human review based on business impact and risk.

## Architecture

``` text
Customer Data
      +
Support History
      ↓
Copilot in Excel
      ↓
Analysis
      ↓
Risk Indicators
      ↓
Manager
      ↓
Human Decision
```

## Lab 1 Takeaway

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
Microsoft    Copilot      Copilot
365 Copilot  in Excel     in Excel
Chat
```

------------------------------------------------------------------------

# Lab 2 --- Fix AI Data Quality and Grounding

## Platform

**Microsoft Copilot Studio**

### Specific experience

**Copilot Studio custom agent with uploaded knowledge files**

Copilot Studio supports adding uploaded files as agent knowledge
sources. Knowledge sources are used to ground agent responses.
citeturn0search2turn0search7

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

# Part 1 --- Create the Agent

## Step 1 --- Open Copilot Studio

Open **Microsoft Copilot Studio**.

> **Platform:** Microsoft Copilot Studio --- not Microsoft 365 Copilot
> Chat.

## Step 2 --- Create a custom agent

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

------------------------------------------------------------------------

# Part 2 --- Add the Legacy Knowledge Source

Use:

`Lab_2_Warranty-final.docx`

This document intentionally contains the old information:

``` text
Warranty period: 12 months
```

## Step 1 --- Add the file as knowledge

In the agent, open **Knowledge** and add the uploaded file.

Copilot Studio supports adding files as knowledge sources for an agent.
citeturn0search2

## Step 2 --- Test the agent

Ask:

``` text
What is the warranty period for the X200?
```

Expected result:

``` text
12 months
```

This creates the starting problem for the lab.

------------------------------------------------------------------------

# Part 3 --- Diagnose the Problem

Evaluate the five data-quality dimensions.

  -----------------------------------------------------------------------
  Dimension                           Finding
  ----------------------------------- -----------------------------------
  Accuracy                            The legacy document contains
                                      outdated information

  Relevance                           The warranty document is relevant

  Timeliness                          The document is outdated

  Cleanliness                         Multiple versions can create
                                      confusion

  Availability                        The current policy is not part of
                                      the current retrieval set
  -----------------------------------------------------------------------

Ask:

> Is the AI model necessarily the problem?

**Expected answer:** No. The grounding data or retrieval process may be
the problem.

------------------------------------------------------------------------

# Part 4 --- Correct the Knowledge

Use:

`Lab_2_Warranty_Policy_2026.docx`

The approved document contains:

``` text
Warranty Policy
Version: 2026
Status: Approved
Owner: Legal
Effective Date: 2026
Warranty Period: 24 months
```

## Step 1 --- Remove the legacy source

Remove the old `Lab_2_Warranty-final.docx` knowledge source from the
agent.

## Step 2 --- Add the approved source

Add:

`Lab_2_Warranty_Policy_2026.docx`

as the knowledge source.

This gives the agent a controlled, current source for the scenario.

------------------------------------------------------------------------

# Part 5 --- Test Again

Ask:

``` text
What is the warranty period for the X200?
```

Expected result:

``` text
24 months
```

## Validation Architecture

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

## Architect Takeaway

> Changing the prompt is not the real solution. Fixing the business
> knowledge and retrieval path is the architectural solution.

------------------------------------------------------------------------

# Lab 3 --- Build an AI-Ready Data Architecture

## Platform

**Microsoft Copilot Studio + SharePoint**

### Specific experience

**Copilot Studio custom agent with SharePoint knowledge and a SharePoint
action**

Copilot Studio supports SharePoint as a knowledge source and respects
the signed-in user's SharePoint permissions when retrieving content.
citeturn0search0

Copilot Studio also supports connector-based tools/actions that let an
agent interact with external systems and perform business operations.
citeturn1search1turn1search5

## Objective

Build an AI customer-support agent that uses:

-   Product knowledge
-   Troubleshooting information
-   Warranty policy
-   Customer-service FAQ

Then demonstrate the difference between:

**Knowledge** --- finding and using business information.

**Action** --- performing a business operation.

------------------------------------------------------------------------

# Part 1 --- Prepare SharePoint Knowledge

## Step 1 --- Create or use a SharePoint training site

Example:

``` text
Contoso Customer Support
```

## Step 2 --- Create the document library

Create:

``` text
AI Knowledge
```

## Step 3 --- Organize the supplied documents

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

# Part 2 --- Create the Agent

## Step 1 --- Open Copilot Studio

Create a custom agent:

``` text
Contoso Customer Support Agent
```

## Step 2 --- Configure the purpose

``` text
Help Contoso customer-service employees find approved
product, troubleshooting, warranty, and support information.
```

------------------------------------------------------------------------

# Part 3 --- Add SharePoint as Knowledge

## Step 1 --- Open Knowledge

In the Copilot Studio agent, open **Knowledge**.

## Step 2 --- Add SharePoint

Select **Add knowledge → SharePoint**.

Register the SharePoint site or folder containing the training content.

Copilot Studio can use SharePoint sites, lists, and content as knowledge
sources. The SharePoint knowledge option searches the registered
location and respects the user's permissions. citeturn0search0

## Step 3 --- Add a clear description

Use:

``` text
Approved product manuals, troubleshooting guides,
warranty policies, and customer-service FAQs for
Contoso support employees.
```

A detailed knowledge-source description helps the agent's generative
orchestration understand when the source is relevant.
citeturn0search0turn0search2

------------------------------------------------------------------------

# Part 4 --- Test RAG

Ask:

``` text
What should I do if the X200 overheats?
```

The agent should retrieve relevant information from the troubleshooting
and product documents.

## Architecture

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

**Expected answer:** No.

The architect must define the scope of the knowledge architecture.

------------------------------------------------------------------------

# Part 7 --- Validate Security

Ask:

> If an employee does not have permission to access a SharePoint
> document, should the AI expose the document's contents?

**Expected answer:** No. The AI solution should respect the user's
permissions.

SharePoint knowledge retrieval in Copilot Studio only surfaces content
the signed-in user is permitted to access. citeturn0search0

## Architecture

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

# Part 8 --- Add a Real Action: Create Support Case

## Platform

**Copilot Studio connector tool + SharePoint List**

For this lab, use a SharePoint List as the simple training business
system.

This avoids introducing Power Platform as a separate hands-on platform
while still demonstrating how an agent can perform an action.

Copilot Studio supports connector-based tools that can perform actions
against connected services. citeturn1search1turn1search5

## Step 1 --- Create the SharePoint list

Create a list:

``` text
Support Cases
```

Create these columns:

  Column     Type
  ---------- ------------------------
  Title      Single line of text
  Customer   Single line of text
  Product    Single line of text
  Issue      Multiple lines of text
  Priority   Choice
  Status     Choice

Suggested choices:

**Priority** - Low - Medium - High

**Status** - New - In Progress - Closed

## Step 2 --- Add the action/tool

In Copilot Studio, add a SharePoint connector tool/action that creates
an item in the `Support Cases` list.

Configure the action to populate:

-   Title
-   Customer
-   Product
-   Issue
-   Priority
-   Status

## Step 3 --- Configure the action description

Use a clear description such as:

``` text
Create a new customer support case in the Contoso Support Cases
SharePoint list when the employee explicitly asks to create a case.
Collect the customer, product, issue, priority, and status.
```

Clear tool descriptions help Copilot Studio determine when a tool should
be used. citeturn1search1

## Step 4 --- Test the action

Ask:

``` text
Create a high-priority support case for Fabrikam.
The X200 is overheating.
```

If required information is missing, allow the agent to ask for it.

Expected result:

``` text
Support Case
Customer: Fabrikam
Product: X200
Issue: Overheating
Priority: High
Status: New
```

## Architecture

``` text
Employee
   ↓
Copilot Studio Agent
   ↓
Understand Request
   ↓
Collect / Validate Information
   ↓
SharePoint Connector Action
   ↓
Support Cases List
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
              ↓                 ↓                 ↓
       M365 Copilot Chat   Copilot in Excel   Copilot in Excel
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
                    Copilot Studio Agent
                           /       \
                          ↓         ↓
                     Knowledge    Actions
                          ↓         ↓
                     AI Response  Business
                                  Process
```

# Final Architect Questions

**Q: Which Microsoft Copilot did we use for Lab 1 email summarization?**

**Expected answer:** Microsoft 365 Copilot Chat.

**Q: Which Copilot did we use for the Excel analysis?**

**Expected answer:** Copilot in Excel, part of the Microsoft 365 Copilot
experience.

**Q: Which Copilot did we use for Labs 2 and 3?**

**Expected answer:** Microsoft Copilot Studio.

**Q: Why did we use Copilot Studio for Lab 2?**

**Expected answer:** It lets us configure an agent and its knowledge
sources so we can directly investigate grounding.

**Q: Why did we use SharePoint in Lab 3?**

**Expected answer:** It provides realistic enterprise knowledge and
demonstrates organization, retrieval, and permission-aware access.

**Q: What is the difference between Lab 2 and Lab 3?**

**Expected answer:** Lab 2 fixes a grounding and data-quality problem;
Lab 3 designs the broader AI-ready data architecture.

**Q: What is the difference between knowledge and an action?**

**Expected answer:** Knowledge helps the agent find and use information;
an action lets the agent perform a business operation.

**Q: What is the most important architectural lesson from these labs?**

**Expected answer:** Start with the business requirement, select the
appropriate AI approach, and then design the data, security, retrieval,
and agent architecture needed to support it.
