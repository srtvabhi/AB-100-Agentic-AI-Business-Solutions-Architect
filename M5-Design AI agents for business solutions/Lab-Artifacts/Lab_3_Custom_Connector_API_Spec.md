# Custom Connector Exercise API

## Purpose
Simulate an external service that returns customer account information.

## Endpoint
GET /accounts/{accountId}

## Example Request
GET /accounts/ACC1001

## Example Response
{
  "accountId": "ACC1001",
  "customerName": "Contoso Manufacturing",
  "serviceTier": "Gold",
  "region": "North America"
}

## Authentication
Use Microsoft Entra ID OAuth 2.0 when implementing the connector in a real environment.

## Agent Use
The agent should retrieve account information only when required by the business scenario.
