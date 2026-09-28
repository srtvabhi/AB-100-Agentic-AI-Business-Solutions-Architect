# AB-100 Case Study 3 --- Build, Extend, or Use an OOB Agent?

## Scenario

Contoso's HR team receives many employee questions.

Common questions include:

-   How many vacation days can I take?
-   What is the parental leave policy?
-   How do I submit an expense?
-   What is the travel policy?
-   Where can I find the employee handbook?

The HR team wants employees to get answers quickly.

The architect must decide whether to:

1.  Use an existing Microsoft AI agent
2.  Configure an existing agent
3.  Extend an existing agent
4.  Build a custom solution

## Step 1 --- Look for Existing Microsoft Resources

Before building anything, the architect checks for:

-   Prebuilt AI agents
-   Microsoft Copilot capabilities
-   Copilot Studio capabilities
-   Templates
-   Scenario resources
-   Existing Microsoft AI solutions

### Expected answer

First check whether Microsoft already provides an AI capability or agent
that can solve most of the requirement.

## Step 2 --- Can an Existing Agent Solve the Requirement?

Suppose an existing solution can answer common HR policy questions.

The requirement is:

> "Employees should be able to ask questions about the employee handbook
> and HR policies."

This is a good candidate for configuration.

### Approach

``` text
Employee
   ↓
HR Question
   ↓
Existing Agent
   ↓
Connect HR Knowledge
   ↓
Configure
   ↓
Test
   ↓
Deploy
```

### Expected answer

Use and configure the existing agent instead of building a new solution.

## Step 3 --- When Should We Extend?

Now the requirement becomes more complex.

The employee wants to:

> Ask about leave policy and submit a leave request.

The existing agent can answer the policy question, but it does not
perform the organization's leave-request process.

The architect can consider extending the agent with:

-   Additional knowledge
-   Actions
-   Business workflows
-   System integrations

### Architecture

``` text
Employee
   ↓
HR Question
   ↓
Existing Agent
   ├── HR Knowledge
   └── HR System Action
          ↓
    Leave Request
          ↓
    HR System
```

### Expected answer

Extend the existing agent when the current capability is close to the
requirement but needs additional knowledge, actions, workflows, or
integrations.

## Step 4 --- When Should We Build?

Imagine Contoso has a completely unique business requirement that:

-   Is not supported by an existing agent
-   Cannot reasonably be configured
-   Cannot reasonably be extended

The architect can consider a custom AI solution.

### Architecture

``` text
Unique Business Requirement
          ↓
No Suitable OOB Solution
          ↓
Cannot Reasonably Extend
          ↓
Custom AI Solution
          ↓
Business Systems + Data
          ↓
Business Outcome
```

### Expected answer

Build a custom solution when no suitable out-of-box capability exists
and the requirement cannot reasonably be met by configuring or extending
an existing solution.

## Decision Tree

``` text
                 Business Need
                      ↓
            Is OOB available?
                 /                      Yes          No
               ↓            ↓
           Configure    Can it be
                         extended?
                        /                             Yes        No
                       ↓          ↓
                    Extend      Build
                       \          /
                        \        /
                         AI Solution
```

## Three Examples

### Example 1 --- Answer HR Policy Questions

**Requirement:** Employees ask questions about the handbook.

**Approach:** Configure an existing solution with the organization's HR
knowledge.

``` text
Employee
   ↓
Question
   ↓
OOB Agent
   ↓
HR Knowledge
   ↓
Answer
```

### Example 2 --- Answer Questions + Create Leave Request

**Requirement:** Employees ask about leave and submit a request.

**Approach:** Extend the existing solution with an action/integration to
the HR system.

``` text
Employee
   ↓
Question
   ↓
Agent
   ├── HR Knowledge → Answer
   └── HR Action → Create Leave Request
```

### Example 3 --- Completely Unique AI Requirement

**Requirement:** A specialized AI process does not exist in available
Microsoft solutions and cannot reasonably be extended.

**Approach:** Consider building a custom solution.

``` text
Unique Requirement
       ↓
No OOB Solution
       ↓
No Practical Extension
       ↓
Custom AI Solution
```

## Topic 5 vs Topic 6

This distinction is useful for AB-100.

### Topic 5 --- Identify Out-of-Box Microsoft AI Agent Resources

The question is:

> **"What Microsoft resources are available to help me build or
> implement an AI solution?"**

Think about:

-   Prebuilt agents
-   Copilot Studio
-   Templates
-   Scenario resources
-   Azure AI capabilities

### Topic 6 --- Identify Out-of-Box Microsoft AI Agents

The question is:

> **"Is there already an agent that matches my business scenario?"**

Think about:

-   Existing agents
-   Business scenarios
-   Configuration
-   Extension
-   Reuse

## Architect Questions

### Question 1

**What should the architect do before building a custom AI agent?**

### Expected answer

Check whether an existing Microsoft agent or solution can meet the
requirement.

### Question 2

**When should an existing agent be configured?**

### Expected answer

Configure it when the existing capability already covers the business
requirement with only normal setup or knowledge configuration.

### Question 3

**When should an agent be extended?**

### Expected answer

Extend it when the existing capability is close but needs additional
knowledge, actions, workflows, or integrations.

### Question 4

**When should the architect build a custom solution?**

### Expected answer

Build when no suitable OOB solution exists and the requirement cannot
reasonably be met by configuration or extension.

## Final Decision Model

``` text
REUSE
  ↓
CONFIGURE
  ↓
EXTEND
  ↓
BUILD
```

The architect should prefer the simplest approach that meets the
business requirement.

## Key AB-100 Lesson

**Do not build first. Reuse Microsoft capabilities where they fit,
configure when possible, extend when necessary, and build custom only
when the requirement requires it.**

Think:

**Business Need → OOB Available? → Configure → Extend → Build**
