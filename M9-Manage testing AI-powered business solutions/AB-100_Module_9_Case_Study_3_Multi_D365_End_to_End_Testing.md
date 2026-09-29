# AB-100 Module 9 — Case Study 3: End-to-End Testing Across Dynamics 365

## Scenario

Northwind Global Services uses multiple Dynamics 365 applications to manage its order-to-cash process.

A new AI-powered experience assists users with customer and order information across the business process. The architecture team must design end-to-end tests that validate the complete workflow instead of testing each AI feature in isolation.

## Requirements

- Test the complete business process from customer request through order processing.
- Validate interactions between multiple Dynamics 365 applications.
- Test AI prompts and generated responses within the workflow.
- Validate data movement and integration points.
- Cover functional and nonfunctional requirements.
- Use Copilot to accelerate creation of repeatable test cases.
- Maintain regression coverage for future releases.

## Systems and Data

- Dynamics 365 Sales
- Dynamics 365 Customer Service
- Dynamics 365 Finance or related order-processing capabilities
- Customer and product data
- Order and case records
- AI agent or Copilot experiences
- Integration and workflow components
- Test-case repository

## Architecture Challenge

A single AI response may appear correct while the overall business process still fails.

For example, the agent may correctly identify a customer but use stale order information, fail to transfer information to another application, or produce an output that does not support the next business step.

The architecture therefore needs end-to-end scenarios with validation at each important business-process boundary.

## Architecture

```text
Customer / Employee Request
          |
          v
   Dynamics 365 Sales
          |
          v
       AI / Copilot
          |
          +----------------------+
          |                      |
          v                      v
Customer Context          Order Context
          |                      |
          +----------+-----------+
                     |
                     v
        Dynamics 365 Customer Service
                     |
                     v
          Case / Interaction Update
                     |
                     v
        Dynamics 365 Finance / ERP
                     |
                     v
             Order Processing
                     |
                     v
              Business Outcome
                     |
                     v
          End-to-End Validation
```

## Example

### End-to-End Scenario: Customer Order Issue

**Input**

A customer contacts support because an order is delayed.

**Expected flow**

1. Customer identity is resolved.
2. Relevant customer information is retrieved.
3. The AI experience identifies the correct order.
4. Order status is retrieved from the appropriate system.
5. The agent provides a grounded response.
6. The support interaction is recorded.
7. Required downstream business information is preserved.
8. The process reaches the expected business outcome.

### Validation Areas

| Area | What to Validate |
|---|---|
| Functional | Each business step completes correctly |
| AI Quality | Response is accurate and relevant |
| Grounding | Data comes from appropriate business sources |
| Integration | Information moves correctly between applications |
| Security | Users access only permitted information |
| Performance | Workflow completes within the defined target |
| Error Handling | Missing or invalid data is handled correctly |
| Business Outcome | The process produces the intended result |

## Copilot-Assisted Test Strategy

The team uses Copilot to generate initial test cases from the business-process requirements.

A generated test case includes:

- Test ID
- Purpose
- Preconditions
- Inputs
- Steps
- Expected results
- Edge cases
- Dependencies

The architecture team validates and refines the generated cases before they become part of the official test suite.

## Architecture Questions

1. Why should multi-application AI solutions be tested end-to-end?
2. Which integration points require explicit validation?
3. What should be tested when the AI response is correct but the downstream action fails?
4. How can Copilot accelerate test-case creation without replacing human validation?
5. How should regression testing be maintained as the solution changes?

## Expected Answers

1. The business outcome depends on the complete workflow, including AI behavior, data, integrations, and downstream applications.
2. Validate data retrieval, data transformation, application handoffs, business-rule execution, security boundaries, and error handling.
3. Treat the workflow as a failed end-to-end scenario because the business outcome was not achieved.
4. Copilot can generate initial scenarios and variations, but architects and testers must verify correctness, completeness, and expected results.
5. Maintain reusable test cases, version-controlled templates, regression suites, and repeatable validation criteria.

## Key Architectural Decisions

- Test the complete business process rather than isolated AI features.
- Include integration and downstream business outcomes.
- Validate both AI behavior and traditional application behavior.
- Use Copilot to accelerate test creation while retaining human validation.
- Build reusable regression scenarios for future changes.
- Include functional, nonfunctional, security, and business-outcome validation.

## Final Architecture

```text
Business Process Definition
          |
          v
End-to-End Test Scenarios
          |
          v
Copilot-Assisted Test Generation
          |
          v
Human Validation + Refinement
          |
          v
Execute Across Dynamics 365 Apps
          |
          v
Measure AI + Integration + Business Metrics
          |
          v
Analyze Failures
          |
          +----> Fix / Tune
          |          |
          |          v
          |       Re-Test
          |
          v
Regression Test Suite
          |
          v
Release Approval
```
