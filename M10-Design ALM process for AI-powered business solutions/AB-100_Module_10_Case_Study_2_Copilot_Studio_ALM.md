# Module 10 Case Study 2: Copilot Studio Agent, Connector, and Action ALM

## Scenario

Fabrikam Financial Services is deploying a Copilot Studio agent that helps employees investigate customer account questions.

The agent uses enterprise knowledge, connectors, and actions to retrieve information from business systems. The organization needs a controlled ALM process because changes to topics, prompts, connectors, actions, and configuration can change agent behavior.

## Requirements

- Separate DEV, TEST, and PROD environments.
- Manage agents and supporting components as deployable solution assets.
- Control connectors and connection configuration.
- Externalize environment-specific configuration.
- Test knowledge, prompts, topics, connectors, and actions.
- Prevent development changes from directly affecting PROD.
- Maintain release history.
- Support controlled rollback.
- Apply security and data-access controls.
- Validate agent behavior after every significant change.

## Systems and Data

- Copilot Studio agent
- Topics and instructions
- Prompts
- Knowledge sources
- Connectors
- Actions
- Dataverse/solution components
- Environment-specific configuration
- DEV environment
- TEST environment
- PROD environment
- User identity and permissions
- Telemetry and feedback

## Architecture Challenge

The development team currently edits the production agent when business users request changes.

A connector update could change the data returned by an action. A prompt change could alter agent behavior. A knowledge-source change could affect generated responses.

Design an ALM process that treats the complete agent solution—not just the agent itself—as the release unit.

## Architecture

```text
Business Requirement
        |
        v
Agent Design
        |
        v
DEV
 |  Agent
 |  Topics / Prompts
 |  Knowledge
 |  Connectors
 |  Actions
 |  Configuration
        |
        v
Solution Packaging / Version
        |
        v
TEST
 |  Functional Tests
 |  Connector Tests
 |  Knowledge Tests
 |  Prompt Tests
 |  Security Tests
 |  Regression Tests
        |
        v
PRE-PROD / UAT
        |
        v
Approval
        |
        v
PROD
        |
        v
Telemetry + Feedback
        |
        +---- Defect ----> DEV Change
        |
        +---- Enhancement -> New Version
```

## Example

The team changes an action that retrieves customer account status.

The change is developed in DEV and packaged with the related agent components.

The TEST process validates:

1. The action connects to the correct system.
2. Authentication and authorization are correct.
3. The action returns the expected fields.
4. The agent interprets the result correctly.
5. The agent does not expose unauthorized information.
6. Existing customer-service scenarios still work.
7. The new version passes regression testing.

Only after successful validation and approval is the solution promoted to PROD.

Environment-specific connection details are not hard-coded into the solution.

## Architecture Questions

1. Why should the agent, connectors, actions, prompts, and related components be treated as one ALM solution?
2. Which configuration should be environment-specific?
3. What should be tested after changing a connector?
4. How can the organization prevent DEV changes from affecting PROD?
5. What should happen when a production release causes incorrect agent behavior?

## Expected Answers

1. Agent behavior depends on the combined configuration and supporting components, so changing one component can change the overall solution.
2. Connection references, environment-specific endpoints, configuration values, and other deployment-specific settings should be separated from the core solution.
3. Connector connectivity, permissions, returned data, action execution, agent interpretation, security, and regression scenarios should be tested.
4. Use separate environments, controlled solution deployment, approvals, and promotion gates.
5. Stop or contain the release, investigate telemetry and user feedback, and roll back or deploy a corrected version through the controlled ALM pipeline.

## Key Architectural Decisions

- Treat the complete Copilot Studio solution as the release unit.
- Separate DEV, TEST, PRE-PROD/UAT, and PROD.
- Externalize environment-specific configuration.
- Test connectors and actions as part of agent behavior.
- Validate security and regression scenarios.
- Use controlled promotion and approval gates.
- Maintain rollback capability.
