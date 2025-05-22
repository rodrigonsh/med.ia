# Phase 1: API Specifications

## Base URL
`http://localhost:8000/v1` (development)
`https://api.med.ia/v1` (production)

## Authentication
- **OAuth 2.0**:
  - Authorization URL: `/oauth/authorize`
  - Token URL: `/oauth/token`
  - Scopes:
    - `patient:read` - Read patient data
    - `institution:read` - Read institution data

## Endpoints

### Patient Records
- `GET /patients/{id}/records`
  - Description: Get all records for a patient
  - Parameters:
    - `id`: Patient ID (required)
  - Response: FHIR Bundle of patient resources
  - Status Codes:
    - 200: Success
    - 401: Unauthorized
    - 404: Patient not found

- `GET /patients/{id}/records?date={date}`
  - Description: Get records for a specific date
  - Parameters:
    - `id`: Patient ID (required)
    - `date`: Date in YYYY-MM-DD format (optional)
  - Response: FHIR Bundle of matching resources
  - Status Codes:
    - 200: Success
    - 400: Invalid date format
    - 401: Unauthorized

### Metadata
- `GET /.well-known/fhir-metadata`
  - Description: FHIR capability statement
  - Response: FHIR CapabilityStatement resource
  - Status Codes:
    - 200: Success

## Rate Limiting
- 100 requests/day per access token
- `X-RateLimit-Limit` header shows limit
- `X-RateLimit-Remaining` shows remaining requests

## Response Format
```json
{
  "data": {},
  "meta": {
    "timestamp": "ISO-8601",
    "request_id": "UUID"
  },
  "errors": []
}
```

## Development Notes
- Swagger UI available at `/docs`
- Postman collection available in repository
- Python SDK included in `/sdk`
