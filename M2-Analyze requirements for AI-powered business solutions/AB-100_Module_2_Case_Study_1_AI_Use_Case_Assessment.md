# AB-100 Module 2 --- Case Study 1: Choosing the Right AI Approach

## Scenario

Contoso Manufacturing operates a customer-service department.

The department has three business challenges:

1.  Employees manually summarize customer emails.
2.  Managers spend several hours analyzing monthly support reports.
3.  Managers need to identify customers who may require additional
    attention.

The architect must determine where AI agents can provide business value.

------------------------------------------------------------------------

## Requirement 1 --- Customer Email Summarization

### Current Process

``` text
Customer Email
      ↓
Employee Reads Email
      ↓
Employee Summarizes Issue
      ↓
Summary Added to Case
```

This process happens many times every day.

### AI Opportunity

An AI agent can:

-   Read the customer request
-   Identify the main issue
-   Summarize important information
-   Prepare a case summary

### Architecture

``` text
Customer Email
      ↓
AI Agent
      ↓
Understand Request
      ↓
Generate Summary
      ↓
Employee Review
      ↓
Customer Case
```

### Expected Architect Decision

Use AI for **task automation** because the activity is repetitive and
can reduce manual effort.

------------------------------------------------------------------------

## Requirement 2 --- Customer-Service Analytics

Managers currently review monthly reports manually.

They want to ask:

> Which products generated the most support cases last quarter?

### AI Opportunity

The AI solution can analyze business data and provide insights.

### Architecture

``` text
Business Question
      ↓
AI Agent
      ↓
Customer-Service Data
      ↓
Data Analysis
      ↓
Trends / Patterns
      ↓
Manager
```

### Expected Architect Decision

Use AI for **data analytics** because the requirement is to understand
business data and identify useful patterns.

------------------------------------------------------------------------

## Requirement 3 --- Customer Attention

Managers want to identify customers who may require additional attention
based on:

-   Number of support cases
-   Recent complaints
-   Service history
-   Customer activity

### AI Opportunity

The AI solution can analyze the available information and provide a risk
indicator or recommendation.

### Architecture

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

### Expected Architect Decision

Use AI for **decision support**. The AI provides analysis or
recommendations while the appropriate person makes the final business
decision.

------------------------------------------------------------------------

## Architect Comparison

  Business Requirement                     AI Use
  ---------------------------------------- ------------------
  Summarize customer emails                Task automation
  Analyze support reports                  Data analytics
  Identify customers requiring attention   Decision support

------------------------------------------------------------------------

## Architect Questions

**Q: Which requirement is task automation?**

**Expected answer:** Customer email summarization.

**Q: Which requirement is data analytics?**

**Expected answer:** Analyzing customer-service reports and identifying
trends.

**Q: Which requirement is decision support?**

**Expected answer:** Identifying customers who may require additional
attention.

**Q: Should the AI automatically decide which customers to contact?**

**Expected answer:** Not necessarily. The architect should determine the
required level of human review based on business impact and risk.

**Q: What should the architect consider before selecting an AI
solution?**

**Expected answer:** Business value, required data, process complexity,
risk, integration, security, and human involvement.

------------------------------------------------------------------------

## Key Takeaway

``` text
Business Requirement
        ↓
Identify AI Opportunity
        ↓
┌────────────┬────────────┬──────────────┐
↓            ↓            ↓
Automate     Analyze      Support
Tasks        Data         Decisions
↓            ↓            ↓
AI           AI           AI
Agent        Agent        Agent
```
