# AB-100 Hands-On Lab Guide --- Microsoft 365 Copilot & Copilot Studio

## Lab 1 --- Microsoft 365 Copilot Chat: Customer Support Assistance

### Step 1 --- Open Microsoft 365 Copilot Chat

1.  Open Microsoft 365 Copilot Chat.
2.  Sign in with your Microsoft 365 account.
3.  Start a new conversation.

### Step 2 --- Analyze a Customer Email

Use this sample customer request:

> Our X200 machine is overheating after running for three hours. What
> should we check?

Ask Copilot:

> Summarize the customer's problem and identify the information a
> support employee would need to investigate it.

### Step 3 --- Generate a Support Response

Ask:

> Draft a professional response to the customer about the X200
> overheating issue. Keep the response clear and do not invent technical
> details that are not provided.

### Step 4 --- Create a Troubleshooting Checklist

Ask:

> Create a short troubleshooting checklist that a support engineer can
> use for this customer issue.

### Step 5 --- Create a Follow-Up Summary

Ask:

> Summarize this customer issue into a short internal support note
> containing the problem, required investigation, and next action.

### Lab Architecture

``` text
Customer Email
      ↓
Microsoft 365 Copilot Chat
      ↓
Understand
Summarize
Generate
      ↓
Support Employee
```

------------------------------------------------------------------------

# Lab 2 --- Microsoft 365 Copilot: Business Knowledge

## Step 1 --- Prepare Business Documents

Use these sample documents:

-   Contoso Product Manual
-   Contoso Troubleshooting Guide
-   Contoso Warranty Policy
-   Contoso Customer Service SOP

Make the documents available in the supported Microsoft 365 location
used for the lab.

## Step 2 --- Ask a Knowledge-Based Question

Ask:

> According to the Contoso warranty policy, what should a support
> employee do when an X200 machine overheats?

Check that the response is based on the available business information.

## Step 3 --- Ask a Product Question

Ask:

> According to the Contoso troubleshooting guide, what checks should be
> performed when an X200 overheats?

## Step 4 --- Ask for a Response

Ask:

> Using the Contoso support information, draft a response to the
> customer about the X200 overheating issue.

## Step 5 --- Test an Unknown Question

Ask:

> What is Contoso's warranty policy for a product that is not included
> in the available documents?

Check how Copilot handles information that is not available.

### Lab Architecture

``` text
                 Microsoft 365 Copilot
                         ↓
                  Business Knowledge
                  /      |       \
                 ↓       ↓        ↓
             Manual     FAQ    Warranty
                  \      |       /
                   \     |      /
                    ↓    ↓     ↓
                  Grounded Response
                         ↓
                  Support Employee
```

------------------------------------------------------------------------

# Lab 3 --- Copilot Studio: Create a Customer Support Agent

## Step 1 --- Open Copilot Studio

1.  Open Microsoft Copilot Studio.
2.  Sign in.
3.  Create a new agent.

## Step 2 --- Define the Agent

Use:

**Name:** Contoso Support Agent

Use the following purpose:

> Help Contoso customer-service employees answer questions about Contoso
> products, troubleshooting procedures, and support policies.

## Step 3 --- Configure Agent Instructions

Add instructions similar to:

> You are a Contoso customer-support assistant. Use approved Contoso
> support information to answer questions. Do not invent product
> information or company policies. If the required information is not
> available, clearly tell the employee that the information is
> unavailable.

## Step 4 --- Add Knowledge

Add the following business documents:

-   Contoso Product Manual
-   Contoso Troubleshooting Guide
-   Contoso Warranty Policy
-   Contoso FAQ

## Step 5 --- Test the Agent

Ask:

> What should I do if an X200 overheats?

Check whether the agent uses the available Contoso knowledge.

### Lab Architecture

``` text
                 Contoso Support Agent
                          │
                          ↓
                    Agent Instructions
                          │
                          ↓
                       Knowledge
                    /      |       \
                   ↓       ↓        ↓
               Manual   FAQ    Warranty
                          │
                          ↓
                   Grounded Answer
```

------------------------------------------------------------------------

# Lab 4 --- Copilot Studio: Extend the Agent with an Action

## Step 1 --- Define the Business Requirement

The support employee should be able to ask:

> Create a support case for this customer.

The agent should perform an action instead of only generating text.

## Step 2 --- Create the Support Case Data

Create or use a support-case data source with fields such as:

-   Case ID
-   Customer
-   Issue
-   Priority
-   Status

## Step 3 --- Create the Action

Create an action/workflow that can create a new support case.

The action should accept information such as:

-   Customer
-   Issue
-   Priority

## Step 4 --- Add the Action to the Agent

Configure the Contoso Support Agent so it can invoke the action when the
user requests a new support case.

## Step 5 --- Test the Action

Ask:

> Create a high-priority support case for Fabrikam. The X200 is
> overheating after three hours of operation.

Check that the agent:

1.  Understands the request.
2.  Collects required information.
3.  Invokes the action.
4.  Creates the support case.
5.  Returns the result to the employee.

### Lab Architecture

``` text
Employee
   ↓
"Create a support case"
   ↓
Contoso Support Agent
   ↓
Tool / Action
   ↓
Business Workflow
   ↓
Support Case Data
   ↓
Case Created
```

------------------------------------------------------------------------

# Lab 5 --- Copilot Studio: Configure Agent Boundaries

## Step 1 --- Test a Supported Question

Ask:

> What is the warranty period for the X200?

Verify that the agent provides an answer based on the approved
knowledge.

## Step 2 --- Test an Unsupported Request

Ask:

> Invent a new warranty policy for the X200.

Verify that the agent does not create a fictional company policy.

## Step 3 --- Test Missing Information

Ask:

> What is the warranty period for a product that is not included in the
> Contoso documents?

Verify that the agent indicates that the information is unavailable
instead of inventing an answer.

## Step 4 --- Test Business Scope

Ask:

> Tell me the personal information of a Contoso customer.

Verify that the agent follows the configured business boundaries and
available permissions.

------------------------------------------------------------------------

# Lab 6 --- Copilot Studio: Test and Tune the Agent

## Step 1 --- Create Test Questions

Use these test cases:

  -----------------------------------------------------------------------
  Test                    User Request            Expected Behavior
  ----------------------- ----------------------- -----------------------
  1                       What is the X200        Answer from approved
                          warranty?               knowledge

  2                       How do I troubleshoot   Grounded
                          X200 overheating?       troubleshooting answer

  3                       Invent an X200 warranty Do not invent
                                                  information

  4                       Information about an    State that information
                          unknown product         is unavailable

  5                       Create a support case   Invoke the configured
                                                  action

  6                       Ambiguous support       Ask for clarification
                          request                 
  -----------------------------------------------------------------------

## Step 2 --- Run the Tests

Run each test against the agent.

Record:

-   Actual response
-   Expected response
-   Pass/Fail
-   Required change

## Step 3 --- Tune the Agent

If a test fails:

1.  Review the agent instructions.
2.  Review the knowledge source.
3.  Review the action configuration.
4.  Make the required change.
5.  Run the test again.

### Lab Architecture

``` text
Build
  ↓
Test
  ↓
Identify Issue
  ↓
Tune
  ↓
Test Again
  ↓
Ready for Deployment
```

------------------------------------------------------------------------

# Final Lab Architecture

``` text
                    CONTOSO CUSTOMER SUPPORT
                              │
                              ↓
                     Customer Question
                              │
                              ↓
                 ┌────────────────────────┐
                 │ Microsoft 365 Copilot  │
                 │       / Chat           │
                 └───────────┬────────────┘
                             ↓
                    Business Knowledge
                             │
                             ↓
                 ┌────────────────────────┐
                 │    Copilot Studio      │
                 │    Support Agent       │
                 └───────────┬────────────┘
                             │
                    ┌────────┴────────┐
                    ↓                 ↓
                Knowledge          Tools
                    ↓                 ↓
             Business Answer      Action
                                      ↓
                               Support Workflow
                                      ↓
                               Support Case
                                      ↓
                              Employee Outcome
```
