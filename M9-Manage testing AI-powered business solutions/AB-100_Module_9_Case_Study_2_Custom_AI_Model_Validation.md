# AB-100 Module 9 — Case Study 2: Custom AI Model Validation

## Scenario

Fabrikam Financial Services is evaluating a custom AI model that classifies incoming financial documents and extracts information required for downstream processing.

The model will support a business process where incorrect extraction can cause delays and manual rework. The architecture team must create validation criteria before approving the model for production.

## Requirements

- Define measurable model-quality criteria.
- Validate accuracy across representative document types.
- Test edge cases and low-quality inputs.
- Validate safety, compliance, and data-handling requirements.
- Measure operational performance and reliability.
- Establish criteria for acceptance, rejection, and re-validation.

## Systems and Data

- Custom AI model
- Representative financial document dataset
- Ground-truth labels
- Document classification and extraction rules
- Business validation rules
- Test environment
- Model evaluation results

## Architecture Challenge

The team cannot validate the model using accuracy alone.

The solution must define quantitative and qualitative criteria covering model performance, output quality, safety/compliance, cost or efficiency, user experience, and operational reliability.

## Architecture

```text
Representative Test Dataset
          |
          v
     Custom AI Model
          |
          v
Classification / Extraction
          |
          +-----------------------------+
          |                             |
          v                             v
Ground Truth                    Business Rules
          |                             |
          +-------------+---------------+
                        |
                        v
               Validation Framework
                        |
       +----------------+----------------+
       |                |                |
       v                v                v
   Quality          Safety /         Operational
   Metrics          Compliance       Metrics
       |                |                |
       +----------------+----------------+
                        |
                        v
                 Acceptance Criteria
                        |
              +---------+---------+
              |                   |
           Pass                 Fail
              |                   |
              v                   v
       Release Candidate     Tune / Re-Test
```

## Example

The team creates validation criteria for document extraction.

| Validation Area | Example Criterion |
|---|---|
| Classification | Correctly identifies supported document categories |
| Extraction | Required fields are extracted accurately |
| Quality | Output follows required business format |
| Safety | Model does not expose restricted information |
| Compliance | Processing follows organizational requirements |
| Reliability | Model behaves consistently across repeated tests |
| Performance | Processing meets the defined operational target |
| Edge cases | Missing fields, poor scans, and unexpected formats are tested |

These values are examples for the case study. Actual thresholds must be defined by the business and solution requirements.

## Architecture Questions

1. Why is accuracy alone insufficient?
2. What should be included in a custom-model validation framework?
3. How should edge cases be represented in the test dataset?
4. When should a model be re-tested?
5. How should acceptance criteria differ from exploratory test observations?

## Expected Answers

1. A model can achieve acceptable accuracy while failing safety, compliance, reliability, performance, or business-process requirements.
2. Include quantitative, qualitative, safety/compliance, performance, usability where relevant, and operational criteria.
3. Include representative variations, incomplete inputs, poor-quality documents, unsupported formats, and other known failure conditions.
4. Re-test after significant model, data, prompt, configuration, or processing changes, and whenever validation criteria are not met.
5. Acceptance criteria define measurable conditions for approval; exploratory observations help identify weaknesses and improve the solution.

## Key Architectural Decisions

- Establish validation criteria before evaluating the model.
- Use representative and edge-case test data.
- Separate model-quality measures from business acceptance criteria.
- Include safety and compliance validation.
- Treat model changes as a trigger for re-validation.
- Maintain documented test results for release decisions.

## Final Architecture

```text
Business Requirements
        |
        v
Validation Criteria
        |
        v
Representative + Edge-Case Dataset
        |
        v
Custom AI Model
        |
        v
Evaluate
  |-- Quality
  |-- Safety
  |-- Compliance
  |-- Performance
  |-- Reliability
        |
        v
Compare with Acceptance Criteria
        |
   +----+----+
   |         |
  Pass      Fail
   |         |
   v         v
Approve   Tune / Re-Test
```
