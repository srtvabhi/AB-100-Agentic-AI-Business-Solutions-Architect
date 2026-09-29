# Module 10 Case Study 3: Dynamics 365 AI ALM Across Business Applications

## Scenario

Northwind Global Services uses AI capabilities across Dynamics 365 Finance, Supply Chain Management, Sales, and Customer Service.

The organization wants a consistent ALM process for AI-enabled business solutions while recognizing that different Dynamics 365 applications may have different AI assets, configurations, prompts, agents, knowledge sources, business controls, and release dependencies.

## Requirements

- Establish a common AI ALM lifecycle.
- Keep DEV, TEST, PRE-PROD/UAT, and PROD separated.
- Manage AI-related configurations and solution components.
- Validate AI behavior together with business processes.
- Test integrations between Dynamics 365 applications.
- Apply security, compliance, and business approval controls.
- Monitor production telemetry and user feedback.
- Support coordinated releases when multiple applications are affected.
- Re-evaluate AI behavior after application or configuration changes.

## Systems and Data

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Sales
- Dynamics 365 Customer Service
- AI agents and AI features
- Prompts and instructions
- Knowledge sources
- Business data
- Integration interfaces
- Environment-specific configuration
- Telemetry and feedback
- Release and approval process

## Architecture Challenge

A change to an AI-enabled customer service process can depend on information from Sales. A supply-chain AI feature may depend on Finance data and business rules.

If each application is released independently without validating the end-to-end process, an individual component may work correctly while the overall business process fails.

Design an ALM architecture that combines application-specific lifecycle controls with end-to-end AI solution validation.

## Architecture

```text
Business Process
      |
      +-----------------------------+
      |                             |
      v                             v
Dynamics 365 Finance        Dynamics 365 Supply Chain
      |                             |
      +-------------+---------------+
                    |
                    v
             Shared Business Data
                    |
                    v
             Dynamics 365 Sales
                    |
                    v
          Dynamics 365 Customer Service
                    |
                    v
              AI Experiences
                    |
                    v
        DEV / Controlled Configuration
                    |
                    v
              TEST Environment
                    |
       +------------+------------+
       |            |            |
       v            v            v
   AI Tests    Integration   Security/
               Tests         Compliance
       |            |            |
       +------------+------------+
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
          Telemetry + Feedback
                    |
                    v
        Tuning / Fix / Re-release
```

## Example

Northwind changes a Customer Service AI experience that uses customer information originating from Sales.

The ALM process includes:

1. Develop the change in the appropriate DEV environment.
2. Identify dependent Dynamics 365 components.
3. Validate configuration and permissions.
4. Test the AI experience with representative customer scenarios.
5. Test Sales-to-Customer Service data flow.
6. Validate business rules and data access.
7. Run regression tests for existing AI scenarios.
8. Validate the integrated process in PRE-PROD/UAT.
9. Obtain business and technical approval.
10. Promote the coordinated release to PROD.
11. Monitor telemetry and user feedback.
12. Re-evaluate the solution if production behavior changes.

## Architecture Questions

1. Why is application-level testing alone insufficient for this scenario?
2. Which dependencies should be identified before a Dynamics 365 AI release?
3. What should be validated in PRE-PROD/UAT?
4. How should a cross-application AI release be coordinated?
5. What production signals should feed the next ALM cycle?

## Expected Answers

1. AI behavior may depend on data, integrations, business rules, configuration, and AI components across multiple Dynamics 365 applications.
2. Identify data dependencies, integrations, AI configurations, prompts/agents, knowledge sources, permissions, business rules, and application versions or changes that affect the process.
3. Validate end-to-end business scenarios, AI behavior, integrations, security, compliance, performance, and regression requirements.
4. Use dependency mapping, coordinated versioning/release planning, shared validation criteria, and approval gates.
5. Telemetry, user feedback, failed scenarios, quality degradation, security issues, data changes, and other production signals should feed back into development and testing.

## Key Architectural Decisions

- Use a common AI ALM lifecycle across Dynamics 365 applications.
- Preserve application-specific controls where required.
- Map cross-application dependencies before release.
- Test AI behavior together with the underlying business process.
- Include integration, security, compliance, and regression validation.
- Use PRE-PROD/UAT for end-to-end validation.
- Monitor production and feed findings into the next release cycle.
