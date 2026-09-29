# AB-100 Module 10 — Hands-On Lab Guide

## Module: Design ALM Process for AI-Powered Business Solutions

### Lab Overview

These three labs provide practical architecture exercises for the Module 10 ALM topics:

1. **Design an ALM Process for AI Data and Custom Models**
2. **Design an ALM Process for Copilot Studio Agents, Connectors, and Actions**
3. **Design an End-to-End ALM Process for Dynamics 365 AI Solutions**

The labs use realistic sample artifacts so you can practice the architecture decisions without requiring production data.

---

# Lab 1 — AI Data and Custom Model ALM

## Objective

Design and validate an ALM lifecycle for data used by an AI model and for controlled model versions.

## Scenario

Contoso Manufacturing uses a custom AI model to classify supplier compliance documents.

The solution has:

- Source supplier data
- Curated training data
- A golden validation dataset
- Multiple model versions
- DEV, TEST, PRE-PROD, and PROD stages
- Production telemetry

You will create an ALM release decision for a new model version.

## Artifacts

- `Lab1_AI_Training_Data.csv`
- `Lab1_Golden_Validation_Data.csv`
- `Lab1_Model_Release_Candidates.csv`
- `Lab1_Model_ALM_Checklist.md`

## Steps

### Step 1 — Review the source data

Open:

`Lab1_AI_Training_Data.csv`

Identify:

- Input fields
- Target label
- Data quality concerns
- Sensitive information
- Fields that should not be used directly for model training

Record your findings.

### Step 2 — Review the golden validation dataset

Open:

`Lab1_Golden_Validation_Data.csv`

Confirm that the dataset is separate from the training data.

Identify at least three validation scenarios that should remain stable across model versions.

### Step 3 — Review model release candidates

Open:

`Lab1_Model_Release_Candidates.csv`

Compare the candidate models using:

- Accuracy
- False-positive rate
- False-negative rate
- Latency
- Safety/quality status
- Validation status

Do not select a model based on one metric alone.

### Step 4 — Apply the ALM checklist

Open:

`Lab1_Model_ALM_Checklist.md`

For the proposed release, verify:

1. Data quality validation completed.
2. Dataset version recorded.
3. Model version recorded.
4. Golden validation completed.
5. Security and safety checks completed.
6. Regression testing completed.
7. UAT completed.
8. Approval recorded.
9. Rollback version identified.
10. Monitoring configured.

### Step 5 — Create the promotion path

Document the release flow:

```text
DATA
  ↓
CURATED DATASET
  ↓
MODEL TRAINING
  ↓
MODEL VERSION
  ↓
DEV
  ↓
TEST
  ↓
PRE-PROD / UAT
  ↓
APPROVAL
  ↓
PROD
  ↓
MONITORING
  ↓
RETRAIN / NEW VERSION
```

### Step 6 — Define rollback

Identify:

- Current production model
- Candidate model
- Rollback model
- Trigger for rollback
- Person or role responsible for approval

### Expected Outcome

You should have a controlled lifecycle where both data and models are versioned, validated, promoted, monitored, and recoverable.

---

# Lab 2 — Copilot Studio Agent ALM

## Objective

Design an ALM process for a Copilot Studio agent and its supporting connectors, actions, prompts, and configuration.

## Scenario

Fabrikam Financial Services has a Copilot Studio agent that helps employees investigate customer account questions.

The agent uses:

- Knowledge
- Prompts
- Topics/instructions
- A customer lookup connector
- An account-status action
- Environment-specific configuration

A new action version must be promoted without directly changing production.

## Artifacts

- `Lab2_Copilot_Agent_Components.csv`
- `Lab2_Environment_Configuration.json`
- `Lab2_Agent_Test_Scenarios.md`
- `Lab2_Copilot_ALM_Release_Checklist.md`

## Steps

### Step 1 — Review the solution components

Open:

`Lab2_Copilot_Agent_Components.csv`

Classify each component as:

- Agent behavior
- Knowledge
- Connector
- Action
- Configuration
- Security dependency
- Test dependency

### Step 2 — Review environment configuration

Open:

`Lab2_Environment_Configuration.json`

Identify values that must differ between:

- DEV
- TEST
- PRE-PROD
- PROD

Do not hard-code environment-specific connection details into the core solution.

### Step 3 — Review test scenarios

Open:

`Lab2_Agent_Test_Scenarios.md`

For each scenario, identify:

- Expected user intent
- Required data
- Agent behavior
- Connector/action dependency
- Security expectation
- Expected result

### Step 4 — Simulate a connector change

Assume the customer account connector changes from version `1.4` to `1.5`.

Determine the tests required for:

1. Connector connectivity
2. Authentication
3. Authorization
4. Returned data
5. Action execution
6. Agent interpretation
7. Existing scenarios
8. Security boundaries

### Step 5 — Apply the release checklist

Open:

`Lab2_Copilot_ALM_Release_Checklist.md`

Validate the change through:

```text
DEV
 ↓
PACKAGE / VERSION
 ↓
TEST
 ↓
PRE-PROD / UAT
 ↓
APPROVAL
 ↓
PROD
 ↓
TELEMETRY
```

### Step 6 — Define rollback

Document:

- Previous agent version
- Previous connector version
- Previous action version
- Configuration version
- Rollback trigger
- Validation required after rollback

### Expected Outcome

You should have an ALM design where the agent and its dependent components are released as a controlled solution rather than being edited directly in production.

---

# Lab 3 — Dynamics 365 AI End-to-End ALM

## Objective

Design a coordinated ALM process for AI-enabled business processes that span multiple Dynamics 365 applications.

## Scenario

Northwind Global Services uses:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Sales
- Dynamics 365 Customer Service

A customer-service AI experience depends on customer information from Sales. A supply-chain AI process depends on Finance data and business rules.

You must design an end-to-end release process.

## Artifacts

- `Lab3_D365_AI_Dependencies.csv`
- `Lab3_D365_Release_Scenarios.csv`
- `Lab3_End_to_End_Test_Cases.md`
- `Lab3_D365_ALM_Release_Plan.md`

## Steps

### Step 1 — Map dependencies

Open:

`Lab3_D365_AI_Dependencies.csv`

Identify:

- Source application
- Target application
- Data dependency
- AI dependency
- Security dependency
- Business-process dependency

Create a dependency map.

### Step 2 — Review release scenarios

Open:

`Lab3_D365_Release_Scenarios.csv`

For each change, determine:

- Applications affected
- AI components affected
- Integration tests required
- Business process tests required
- Security tests required
- UAT requirement

### Step 3 — Build end-to-end test coverage

Open:

`Lab3_End_to_End_Test_Cases.md`

Validate the complete business flow rather than testing each application independently.

For each scenario, verify:

1. Source data is available.
2. Data crosses the expected integration boundary.
3. Permissions are correct.
4. AI receives the correct context.
5. AI produces the expected type of result.
6. Downstream business processing works.
7. Existing functionality is not broken.

### Step 4 — Build the release plan

Open:

`Lab3_D365_ALM_Release_Plan.md`

Create the release sequence:

```text
BUSINESS REQUIREMENT
        ↓
DEPENDENCY ANALYSIS
        ↓
DEV
        ↓
APPLICATION + AI VALIDATION
        ↓
INTEGRATION TEST
        ↓
SECURITY / COMPLIANCE
        ↓
REGRESSION TEST
        ↓
PRE-PROD / UAT
        ↓
APPROVAL
        ↓
PROD
        ↓
TELEMETRY + FEEDBACK
        ↓
TUNE / FIX / RE-RELEASE
```

### Step 5 — Define release coordination

For every dependent application, record:

- Owner
- Release version
- Dependency
- Test status
- UAT status
- Approval status
- Rollback plan

### Step 6 — Define the production feedback loop

Specify how the following feed into the next ALM cycle:

- Failed AI scenarios
- User feedback
- Telemetry
- Integration failures
- Security findings
- Data changes
- Business-process changes

### Expected Outcome

You should have an end-to-end ALM design that coordinates Dynamics 365 application changes, AI components, integrations, testing, approvals, and production feedback.

---

# Module 10 Lab Completion Checklist

After completing all three labs, verify that you can:

- Version AI data and models.
- Separate DEV, TEST, PRE-PROD/UAT, and PROD.
- Define promotion gates.
- Design ALM for Copilot Studio agents, connectors, and actions.
- Identify environment-specific configuration.
- Design rollback.
- Map Dynamics 365 AI dependencies.
- Test AI behavior together with business processes.
- Coordinate cross-application releases.
- Use telemetry and feedback to drive the next release cycle.
