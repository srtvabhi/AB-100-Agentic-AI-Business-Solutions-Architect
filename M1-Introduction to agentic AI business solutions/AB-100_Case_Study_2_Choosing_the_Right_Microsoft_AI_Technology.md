# AB-100 Case Study 2 --- Choosing the Right Microsoft AI Technology

## Scenario

Contoso Manufacturing wants to use AI in three different business
scenarios.

The architect must choose the appropriate Microsoft AI technology for
each requirement.

The important point is that different AI problems require different AI
capabilities.

## Requirement A --- Analyze Damaged Product Images

Contoso receives product-damage photographs as part of warranty claims.

The system should identify visible damage in the images.

### Business requirement

``` text
Damage Photo
     ↓
AI Image Analysis
     ↓
Identify Damage
     ↓
Warranty Processing
```

### Suitable technology

**Azure AI Services / Vision capabilities**

### Why?

The requirement is image understanding.

The architect should choose an AI capability designed for analyzing
images rather than using a general-purpose technology simply because it
is available.

### Expected answer

Use Azure AI vision capabilities because the business requirement is to
analyze images and identify visual information.

## Requirement B --- Predict Machine Failure

Contoso collects historical machine information:

-   Temperature
-   Pressure
-   Machine usage
-   Maintenance history
-   Machine age
-   Previous failures

The business wants to predict which machines are likely to fail.

### Business requirement

``` text
Historical Machine Data
          ↓
   Machine Learning
          ↓
Failure Prediction
          ↓
Preventive Maintenance
          ↓
Reduce Downtime
```

### Suitable technology

**Azure Machine Learning**

### Why?

This is a predictive machine-learning problem.

The organization has historical data and wants to build, evaluate,
deploy, and manage a predictive model.

### Expected answer

Use Azure Machine Learning because the requirement is to build and
manage a predictive machine-learning solution.

## Requirement C --- Generate Customer Responses

Customer-service employees need help creating responses to customer
questions.

The AI should understand the request and generate a natural-language
response.

### Business requirement

``` text
Customer Question
       ↓
Generative AI
       ↓
Draft Response
       ↓
Employee Review
       ↓
Customer Response
```

### Suitable technology

Depending on the solution context, the architect could use:

-   Azure OpenAI capabilities for a custom generative AI solution
-   Microsoft Copilot capabilities when an existing Microsoft business
    application experience meets the requirement

### Expected answer

Use generative AI when the requirement is to understand language and
generate natural-language content.

## Technology Selection View

  -----------------------------------------------------------------------
  Business Requirement    AI Capability           Example Microsoft
                                                  Technology
  ----------------------- ----------------------- -----------------------
  Analyze product images  Image understanding     Azure AI Services /
                                                  Vision

  Predict machine failure Machine learning        Azure Machine Learning

  Generate customer       Generative AI           Azure OpenAI /
  responses                                       Microsoft Copilot
  -----------------------------------------------------------------------

## Architecture

``` text
                 Business Requirements
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
     Image Analysis   Prediction    Content Generation
          ↓              ↓              ↓
    Azure AI        Azure Machine   Azure OpenAI /
    Services        Learning        Microsoft Copilot
          │              │              │
          ↓              ↓              ↓
    Faster Claims   Prevent Failure   Faster Responses
          │              │              │
          └──────────────┼──────────────┘
                         ↓
                  Business Value
```

## Architect Questions

### Question 1

**How should the architect choose an AI technology?**

### Expected answer

Choose based on the business requirement, AI capability needed, existing
environment, integration, security, scalability, and expected business
value.

### Question 2

**Should every AI requirement use generative AI?**

### Expected answer

No. Choose the technology that matches the actual business problem and
required AI capability.

### Question 3

**What should come before technology selection?**

### Expected answer

Understand the business outcome, process, AI requirement, data, and
integration needs.

## Business Value

### Vision AI

``` text
Product Damage
      ↓
Image Analysis
      ↓
Damage Identified
      ↓
Faster Warranty Processing
```

### Machine Learning

``` text
Machine Data
      ↓
Prediction
      ↓
Failure Risk
      ↓
Preventive Maintenance
      ↓
Less Downtime
```

### Generative AI

``` text
Customer Question
      ↓
Generated Draft
      ↓
Employee Review
      ↓
Faster Response
```

## Key AB-100 Lesson

**The architect chooses technology based on the business capability
required, not because one AI technology is suitable for every problem.**

Think:

**Requirement → AI Capability → Technology → Integration → Business
Value**
