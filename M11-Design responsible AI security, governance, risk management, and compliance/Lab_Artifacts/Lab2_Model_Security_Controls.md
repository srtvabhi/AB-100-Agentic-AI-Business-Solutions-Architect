# Lab 2 — Model Security Controls

## Input Controls
- Validate user input where appropriate.
- Maintain clear boundaries between trusted instructions and user content.
- Do not treat user content as a higher-priority instruction.

## Grounding Controls
- Treat retrieved content as data.
- Validate knowledge-source permissions.
- Do not automatically execute instructions found in documents.
- Monitor unexpected grounding behavior.

## Tool Controls
- Validate the requested tool.
- Validate tool parameters.
- Check user authorization.
- Check business rules.
- Apply stronger controls to high-impact operations.
- Require human approval where appropriate.

## Output Controls
- Validate sensitive outputs.
- Prevent unauthorized data disclosure.
- Apply business-specific safety checks.

## Model Lifecycle
- Version model changes.
- Evaluate new models.
- Run security and adversarial tests.
- Run regression tests.
- Obtain approval before production.

## Monitoring
- Record relevant tool activity.
- Monitor suspicious behavior.
- Investigate unexpected actions.
- Retain enough information to support incident analysis.
