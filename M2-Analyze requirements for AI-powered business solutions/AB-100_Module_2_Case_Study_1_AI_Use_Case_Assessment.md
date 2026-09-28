# AB-100 Module 2 --- Case Study 1: Choosing the Right AI Approach

## Scenario

Contoso Manufacturing operates a customer-service department that
supports customers across multiple products.

The customer-service team handles a large number of customer requests
every day. As the number of customers and support cases increases,
managers are looking for opportunities to use AI to improve productivity
and decision-making.

The department has identified three business challenges:

1.  Employees manually summarize customer emails.
2.  Managers spend several hours analyzing monthly support reports.
3.  Managers need to identify customers who may require additional
    attention.

The architect must determine **what type of AI capability is appropriate
for each business requirement**.

The key question is not:

> Which AI product should we use?

The first question is:

> What does the business need AI to do?

------------------------------------------------------------------------

## Current Business Process

Today, the customer-service team performs several activities manually.

``` text
Customer Requests
       ↓
Customer-Service Employees
       ↓
Read / Understand Information
       ↓
Summarize / Analyze / Review
       ↓
Business Action or Decision
```

Some activities are repetitive, some require analysis of business data,
and some require human judgment.

The architect must identify where AI can provide value and determine the
appropriate level of automation or human involvement.

------------------------------------------------------------------------

## Architect's Challenge

For each business requirement, determine whether AI should primarily be
used for:

-   **Task automation**
-   **Data analytics**
-   **Decision support**

The architect should also consider:

-   Business value
-   Required data
-   Process complexity
-   Risk
-   Security
-   Integration requirements
-   Human involvement

------------------------------------------------------------------------

# Requirement 1 --- Customer Email Summarization

## Current Process

Customer-service employees receive many customer emails every day.

For each email, an employee must read the message, understand the
customer's issue, and manually create a summary for the support case.

``` text
Customer Email
      ↓
Employee Reads Email
      ↓
Employee Understands Issue
      ↓
Employee Creates Summary
      ↓
Summary Added to Case
```

This process is repeated many times every day.

The activity consumes employee time even though the basic task is
usually straightforward and repeatable.

------------------------------------------------------------------------

## AI Opportunity

An AI agent can assist with the repetitive work by:

-   Reading the customer request
-   Identifying the main issue
-   Extracting important information
-   Generating a concise summary
-   Preparing the summary for the support case

The employee can review the generated summary before it is used.

### Why AI Fits This Requirement

The activity is:

-   Repetitive
-   Time-consuming
-   Clearly defined
-   Suitable for generating a consistent output
-   Easy to review by an employee

The architect therefore identifies this as a **task automation**
opportunity.

------------------------------------------------------------------------

## Architecture

``` text
Customer Email
      ↓
AI Agent
      ↓
Understand Request
      ↓
Extract Important Information
      ↓
Generate Summary
      ↓
Employee Review
      ↓
Customer Case
```

------------------------------------------------------------------------

## Expected Architect Decision

Use AI for **task automation** because the activity is repetitive and
can reduce manual effort.

The employee can remain in the process when review or approval is
required.

------------------------------------------------------------------------

# Requirement 2 --- Customer-Service Analytics

## Current Process

Managers receive monthly customer-service reports containing information
such as:

-   Number of support cases
-   Products involved
-   Case categories
-   Resolution information
-   Customer trends

Today, managers manually review these reports to identify important
patterns.

For example, a manager may ask:

> Which products generated the most support cases last quarter?

The manager has to search through reports and analyze the data manually.

------------------------------------------------------------------------

## AI Opportunity

An AI solution can allow managers to ask questions about business data
using natural language.

The AI can:

-   Retrieve relevant business data
-   Analyze the data
-   Identify trends
-   Identify patterns
-   Present useful insights

### Why AI Fits This Requirement

The primary requirement is not to perform a repetitive action.

The requirement is to **understand business data and discover useful
information**.

The architect therefore identifies this as a **data analytics**
opportunity.

------------------------------------------------------------------------

## Architecture

``` text
Business Question
      ↓
AI Agent
      ↓
Customer-Service Data
      ↓
Data Analysis
      ↓
Trends / Patterns / Insights
      ↓
Manager
```

------------------------------------------------------------------------

## Example

Manager asks:

> Which products generated the most support cases last quarter?

The AI solution can:

``` text
Manager Question
       ↓
Retrieve Support Data
       ↓
Analyze Case Data
       ↓
Identify Patterns
       ↓
Present Insight
       ↓
Manager
```

The manager uses the insight to understand what is happening in the
business.

------------------------------------------------------------------------

## Expected Architect Decision

Use AI for **data analytics** because the requirement is to analyze
business data and identify useful trends, patterns, and insights.

------------------------------------------------------------------------

# Requirement 3 --- Customer Attention

## Current Process

Customer-service managers want to identify customers who may require
additional attention.

They currently review several pieces of information, including:

-   Number of support cases
-   Recent complaints
-   Service history
-   Customer activity

This information may be spread across different business systems.

The manager must review the information and determine whether a customer
requires additional attention.

------------------------------------------------------------------------

## AI Opportunity

An AI solution can analyze the available information and identify
patterns that may indicate increased customer risk or the need for
additional attention.

For example, the solution could identify a customer with:

-   Multiple recent support cases
-   Several unresolved complaints
-   Repeated service issues
-   Increased support activity

The AI can provide a risk indicator or recommendation.

However, the architect must decide whether the AI should make the final
decision or whether a person should review the recommendation.

------------------------------------------------------------------------

## Why AI Fits This Requirement

The requirement involves analyzing information and helping a person make
a business decision.

The AI is providing:

-   Analysis
-   Patterns
-   Risk indicators
-   Recommendations

The final business decision may still require human judgment.

The architect therefore identifies this as a **decision-support**
opportunity.

------------------------------------------------------------------------

## Architecture

``` text
Customer Data
     +
Support History
     +
Business Rules
        ↓
    AI Agent
        ↓
     Analysis
        ↓
Customer Risk / Recommendation
        ↓
Manager
        ↓
Human Decision
```

------------------------------------------------------------------------

## Human Involvement

The architect should consider the consequences of allowing AI to make
the final decision.

For example:

``` text
AI Analysis
     ↓
Recommendation
     ↓
Human Review
     ↓
Business Decision
```

This approach may be appropriate when the decision has significant
customer, financial, operational, or compliance implications.

The required level of human involvement depends on the business scenario
and risk.

------------------------------------------------------------------------

## Expected Architect Decision

Use AI for **decision support** because the AI provides analysis or
recommendations while the appropriate person makes the final business
decision.

------------------------------------------------------------------------

# Architect Comparison

  -----------------------------------------------------------------------
  Business Requirement    AI Approach             Primary Purpose
  ----------------------- ----------------------- -----------------------
  Summarize customer      Task automation         Reduce repetitive
  emails                                          manual work

  Analyze support reports Data analytics          Understand business
                                                  data and identify
                                                  patterns

  Identify customers      Decision support        Provide analysis or
  requiring attention                             recommendations for
                                                  human decisions
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# End-to-End Architecture

The three requirements represent three different ways AI can support a
business.

``` text
                    CUSTOMER SERVICE
                           │
          ┌────────────────┼────────────────┐
          ↓                ↓                ↓
     Repetitive         Business          Business
        Tasks             Data             Decisions
          ↓                ↓                ↓
    Task Automation   Data Analytics   Decision Support
          ↓                ↓                ↓
      AI Agent          AI Agent          AI Agent
          ↓                ↓                ↓
    Automated/         Insights /       Recommendation
    Assisted Task       Patterns             ↓
                                           Human
                                           Decision
```

The important point for the architect is that **AI is not one single
capability**.

Different business requirements may require different AI approaches.

------------------------------------------------------------------------

# Architect Decision Flow

When analyzing a new business requirement, the architect can ask:

``` text
What does the business need AI to do?
                ↓
       ┌────────┼─────────┐
       ↓        ↓         ↓
   Automate   Analyze   Support
     Task      Data     Decision
       ↓        ↓         ↓
     Task     Data      Decision
   Automation Analytics  Support
```

### Decision Questions

**Is the requirement mainly a repetitive activity?**

→ Consider task automation.

**Is the requirement mainly about understanding business data?**

→ Consider data analytics.

**Is the requirement about helping someone make a business decision?**

→ Consider decision support.

**Does the decision have significant business impact or risk?**

→ Consider appropriate human review or approval.

------------------------------------------------------------------------

# Architect Questions

**Q: Which requirement is task automation?**

**Expected answer:** Customer email summarization.

**Q: Why is email summarization a good automation scenario?**

**Expected answer:** It is repetitive, time-consuming, clearly defined,
and produces a predictable output.

**Q: Which requirement is data analytics?**

**Expected answer:** Analyzing customer-service reports and identifying
trends or patterns.

**Q: What is the main purpose of AI in the analytics scenario?**

**Expected answer:** Help users understand business data and identify
useful insights.

**Q: Which requirement is decision support?**

**Expected answer:** Identifying customers who may require additional
attention.

**Q: Why is this decision support rather than simple automation?**

**Expected answer:** The AI analyzes information and provides
recommendations, while a person may make the final business decision.

**Q: Should the AI automatically decide which customers to contact?**

**Expected answer:** Not necessarily; the architect should determine the
required level of human review based on business impact and risk.

**Q: What should the architect consider before selecting an AI
approach?**

**Expected answer:** Business value, required data, process complexity,
risk, integration, security, and human involvement.

**Q: Should every repetitive task be automated with AI?**

**Expected answer:** No; the architect should consider business value,
complexity, risk, and whether AI is actually required.

**Q: What is the first question the architect should ask?**

**Expected answer:** What does the business need AI to do?

------------------------------------------------------------------------

# Key Takeaway

``` text
Business Requirement
        ↓
Identify What AI Needs to Do
        ↓
┌────────────┬────────────┬──────────────┐
↓            ↓            ↓
Automate     Analyze      Support
Tasks        Data         Decisions
↓            ↓            ↓
Task         Data         Decision
Automation   Analytics    Support
↓            ↓            ↓
AI Agent     AI Agent     AI Agent
                         ↓
                   Human Decision
```

> **The architect should select the AI approach based on the business
> requirement---not start with an AI product and try to fit the business
> problem into it.**
