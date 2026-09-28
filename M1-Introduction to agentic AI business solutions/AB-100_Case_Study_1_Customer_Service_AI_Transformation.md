# AB-100 Case Study 1 --- Customer Service AI Transformation

## Scenario

Contoso is an industrial equipment company with about 500
customer-service employees.

Customer-service employees receive hundreds of customer emails every
day.

### Current process

``` text
Customer Email
      ↓
Employee reads request
      ↓
Search SharePoint
      ↓
Search Dynamics 365
      ↓
Understand customer problem
      ↓
Write response
      ↓
Create follow-up
```

The process is slow because employees have to search multiple systems
and manually prepare responses.

## Business Goal

Contoso wants to:

-   Reduce customer-service resolution time
-   Improve employee productivity
-   Improve customer experience
-   Keep employees in control of the final response

## 1. Identify the Business Problem

The first question for the architect is not:

> "Which AI product should we use?"

The first question is:

> "What business process needs improvement?"

### Expected answer

The customer-service process is slow because employees manually search
for information, understand the issue, write responses, and create
follow-up actions.

## 2. Define What AI Needs to Do

The AI assistant should be able to:

-   Understand the customer's request
-   Find relevant product information
-   Find customer history
-   Summarize important information
-   Suggest a response
-   Suggest follow-up actions

The employee should review the AI output before sending it.

### Expected answer

AI should assist the employee rather than completely replace the
employee.

## 3. Identify Required Data

The AI solution needs access to trusted business information.

### SharePoint

-   Product manuals
-   Troubleshooting guides
-   FAQs
-   Product documentation

### Dynamics 365

-   Customer information
-   Previous cases
-   Service history
-   Customer interactions

### Expected answer

The AI needs trusted product knowledge from SharePoint and
customer/service information from Dynamics 365.

## 4. Identify Systems

The solution needs to work with the systems employees already use.

``` text
                ┌──────────────────┐
                │    Customer      │
                └────────┬─────────┘
                         ↓
                ┌──────────────────┐
                │ Customer Request │
                └────────┬─────────┘
                         ↓
                ┌──────────────────┐
                │   AI Assistant   │
                └───────┬───┬──────┘
                        │   │
             ┌──────────┘   └──────────┐
             ↓                         ↓
      ┌──────────────┐          ┌──────────────┐
      │  SharePoint  │          │ Dynamics 365 │
      │ Product Info │          │Customer Data │
      └──────────────┘          └──────────────┘
                        │
                        ↓
                ┌──────────────────┐
                │ Suggested Reply  │
                └────────┬─────────┘
                         ↓
                ┌──────────────────┐
                │    Employee      │
                │ Reviews/Edits    │
                └────────┬─────────┘
                         ↓
                ┌──────────────────┐
                │ Final Response   │
                └────────┬─────────┘
                         ↓
                      Customer
```

## 5. Security and Governance

The architect must make sure that:

-   Users only access information they are allowed to see
-   Customer information is protected
-   Existing identity and access controls are respected
-   AI-generated responses are reviewed when needed
-   The solution follows company policies and compliance requirements

### Expected answer

The AI solution must preserve existing permissions, protect customer
data, and keep appropriate human review in the process.

## 6. Define Success Metrics

The architect needs measurable outcomes.

Possible KPIs:

-   Average resolution time
-   Employee productivity
-   Customer satisfaction
-   Response quality
-   AI adoption
-   Number of cases assisted by AI

### Expected answer

Success should be measured using business outcomes such as faster
resolution, better productivity, and improved customer satisfaction.

## 7. Final Architecture

``` text
Business Goal
     ↓
Improve Customer Service
     ↓
Identify Process
     ↓
Customer Email Handling
     ↓
AI Requirements
     ↓
Understand → Search → Summarize → Draft → Suggest Action
     ↓
Business Data
     ├── SharePoint
     └── Dynamics 365
     ↓
AI Assistant
     ↓
Employee Review
     ↓
Final Customer Response
     ↓
Business Outcome
     ├── Faster Resolution
     ├── Higher Productivity
     └── Better Customer Experience
```

## Architect Decision

The architect starts with the business problem and works toward the
technology.

### Decision flow

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
Security & Governance
     ↓
Success Metrics
     ↓
Technology Selection
```

## Key AB-100 Lesson

**Do not start with the AI product. Start with the business outcome.**

The architect connects:

**Business → Process → AI Capability → Data → Systems → Security →
Measurement**
