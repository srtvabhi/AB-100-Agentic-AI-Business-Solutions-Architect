# Module 11 Case Study 3: Data Residency, Access Control, and AI Auditability

## Scenario

Northwind Global Services is deploying an AI assistant for employees in Europe and North America.

The assistant uses employee, customer, and business documents from several repositories.

Some information is subject to geographic and regulatory requirements.

The organization must ensure that data is accessed only by authorized users, remains within approved boundaries, and can be traced throughout the AI lifecycle.

## Requirements

- Classify data before it is used by AI.
- Apply role-based access to grounding data.
- Separate sensitive data domains.
- Validate where data is stored and processed.
- Review connector and external-service data movement.
- Consider logging and telemetry locations.
- Restrict model and tuning permissions.
- Record model and data versions.
- Record important configuration changes.
- Support investigation after an incident.
- Prevent cross-user and cross-domain information leakage.

## Systems and Data

- Microsoft Entra ID
- SharePoint and enterprise repositories
- Customer data
- Employee data
- AI agent
- Grounding/knowledge sources
- AI model
- Connectors
- External APIs
- Telemetry and audit records
- Compliance requirements

## Architecture Challenge

The current architecture assumes that keeping the primary database in the correct region is sufficient.

The compliance team identifies additional data paths:

```text
Repository
   ↓
Connector
   ↓
Agent
   ↓
Model
   ↓
External API
   ↓
Telemetry / Logs
```

The architecture team must validate the complete data path and ensure that access and audit controls apply throughout the solution.

## Architecture

```text
                         User
                           |
                           v
                    Microsoft Entra ID
                           |
                           v
                    Authorization
                           |
             +-------------+-------------+
             |                           |
             v                           v
       Approved Data                 User Role
             |                           |
             +-------------+-------------+
                           |
                           v
                     AI Agent
                           |
             +-------------+-------------+
             |                           |
             v                           v
       Grounding Data                 Model
             |                           |
             +-------------+-------------+
                           |
                           v
                    Tool / Connector
                           |
                           v
                 Approved Business System
                           |
                           v
              Residency / Compliance Check
                           |
                           v
                 Audit + Telemetry
```

## Example

A European employee asks the assistant to summarize an employee document.

The architecture checks:

1. The employee is authorized to access the document.
2. The document belongs to an approved data domain.
3. The AI workflow uses an approved processing location.
4. Connectors do not move restricted data to an unauthorized destination.
5. Telemetry and audit records follow applicable requirements.
6. The model and configuration versions can be identified later.

A North American employee should not receive the European employee data simply because the AI agent can technically retrieve it.

## Architecture Questions

1. Why is data residency an end-to-end architecture concern?
2. Which components should be included in a data-flow review?
3. How should grounding access be controlled?
4. Who should be allowed to change model or tuning configuration?
5. What should be recorded to support an investigation?

## Expected Answers

1. AI data can move through repositories, connectors, models, external services, and telemetry, not just the primary database.
2. Review data sources, connectors, agents, models, APIs, business systems, logs, telemetry, and storage/processing locations.
3. Use identity-aware authorization, least privilege, data segmentation, and appropriate repository permissions.
4. Only authorized roles with a defined responsibility should modify model or tuning configuration, with controlled change processes.
5. Record identity, timestamp, version, configuration change, model/data lineage, deployment information, and relevant activity.

## Key Architectural Decisions

- Classify data before AI use.
- Apply authorization to grounding data.
- Separate sensitive data domains.
- Map complete data movement paths.
- Validate storage and processing locations.
- Restrict model and tuning permissions.
- Maintain model and data lineage.
- Maintain audit trails for important changes.
- Use telemetry and audit data together for investigation.
