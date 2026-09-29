# Module 10 Case Study 1: AI Data and Custom Model ALM

## Scenario

Contoso Manufacturing is building an AI solution that predicts whether incoming supplier documents contain compliance exceptions.

The solution uses historical supplier records, a curated validation dataset, and a custom AI model. The model is retrained when data drift or model-quality degradation is detected.

The architecture team must design an ALM process that controls data, model versions, validation, promotion, monitoring, and rollback.

## Requirements

- Separate development, test, and production environments.
- Version datasets and custom AI model versions.
- Maintain a controlled golden validation dataset.
- Validate data quality before model training.
- Validate model performance before promotion.
- Prevent unapproved model versions from reaching production.
- Track model lineage and release history.
- Monitor production performance and data drift.
- Support rollback to a previously approved model version.
- Protect sensitive supplier information throughout the lifecycle.

## Systems and Data

- Source supplier and compliance data
- Curated training dataset
- Golden validation dataset
- Custom AI model
- Model metadata/model card
- DEV environment
- TEST environment
- PRE-PROD/UAT environment
- PROD environment
- Monitoring and telemetry
- Approval and release process

## Architecture Challenge

The team currently trains models directly from operational data and manually replaces the production model.

This creates several risks:

- The training data may change without traceability.
- A model may be promoted without consistent validation.
- Production behavior may not be reproducible.
- A rollback may be difficult.
- Data drift may not be detected early.

Design an ALM architecture that treats both data and models as controlled, versioned AI assets.

## Architecture

```text
Operational Data
      |
      v
Data Quality + Governance
      |
      v
Curated / Versioned Dataset
      |
      +----> Golden Validation Dataset
      |
      v
Custom Model Training
      |
      v
Model Version + Metadata
      |
      v
DEV
      |
      v
Quality / Safety / Performance Validation
      |
      v
TEST
      |
      v
AI Evaluation + Regression
      |
      v
PRE-PROD / UAT
      |
      v
Approval Gate
      |
      v
PROD
      |
      v
Telemetry + Drift Monitoring
      |
      +---- Issue/Drift ----> Retrain / New Version
      |
      +---- Stable ----------> Continue Monitoring
```

## Example

Model version `v2.3` is trained using dataset version `2026-09`.

Before release:

1. Validate the dataset.
2. Compare `v2.3` against the current production model.
3. Run the golden validation dataset.
4. Validate accuracy, false positives, false negatives, latency, and safety requirements.
5. Record the model version and supporting dataset versions.
6. Deploy to TEST.
7. Run integration and regression tests.
8. Promote to PRE-PROD/UAT.
9. Obtain production approval.
10. Deploy to PROD.
11. Monitor drift and production performance.

If `v2.3` fails its production quality threshold, the team can return to the previously approved model version.

## Architecture Questions

1. Which AI assets must be versioned?
2. Why should the golden validation dataset be controlled separately from training data?
3. What promotion gates should exist before PROD?
4. How should the architecture support rollback?
5. What production signals should trigger model re-evaluation?

## Expected Answers

1. Training/validation datasets, model versions, model metadata, evaluation results, configuration, and release definitions should be controlled.
2. The golden dataset provides a stable reference for comparing model versions.
3. Data quality, model evaluation, security/safety, integration, regression, UAT, and approval gates should be considered.
4. Keep the previous approved model version deployable and maintain release/version lineage.
5. Quality degradation, data drift, changes in input patterns, safety issues, or significant production behavior changes should trigger re-evaluation.

## Key Architectural Decisions

- Treat data and models as versioned AI assets.
- Separate DEV, TEST, PRE-PROD/UAT, and PROD.
- Use controlled validation datasets.
- Require measurable evaluation gates before promotion.
- Maintain model lineage and release history.
- Monitor production behavior and drift.
- Keep rollback capability available.
