# API Specifications

## Base URL
`https://api.med.ia/v1`

## Authentication & Authorization
- **OAuth 2.0/OpenID Connect**: Patients grant access to institutions via scopes (e.g., `lab:write`, `hospital:read`).
- **Fine-Grained Access Tokens**: Use JWT claims for role-based access (patient, doctor, lab).
- **Patient Consent Management**: API calls are subject to patient consent, managed via a dashboard.
- **Rate Limiting**: Tier-based (e.g., free tier = 100 reqs/day, enterprise = unlimited).

## Core Endpoints (FHIR-native)

### Patient Records
- `GET /patients/{id}/records?date={date}`: Fetch historical data for a patient via Git tags/commits. Returns FHIR R4 Bundles.
- `POST /patients/{id}/records`: Create a new Git commit with changes to a patient's FHIR record.
- `GET /Patient/{id}/$everything`: Standard FHIR operation to retrieve all resources for a patient (paginated Git history).

### Bulk Operations
- `POST /$bulk-import`: Asynchronous endpoint for bulk data import. Returns a `job_id` for status tracking. Supports NDJSON/CSV for bulk FHIR data.
- `GET /bulk/status/{job_id}`: Retrieve the status of a bulk operation.
- `GET /bulk/export/{job_id}`: Retrieve exported bulk data.

### Webhooks
- **FHIR Subscriptions**: Webhooks for real-time notifications triggered by Git push events (e.g., `DiagnosticReport:create`).
- `POST /webhooks/lab-results`: Example webhook endpoint for lab results.

## MCP API Endpoints

### Context Retrieval
- `POST /mcp/query`: For context retrieval by LLMs or other MCP-compatible tools.
    - **Request Body Example**:
    ```json
    {
      "query": "patient_123:latest_vitals",
      "context_types": ["vital_signs"],
      "auth_token": "Bearer <JWT>"
    }
    ```

### Data Update
- `POST /mcp/update`: For tool-initiated data writes via MCP.
    - **Request Body Example**:
    ```json
    {
      "operation": "update",
      "context_type": "lab_results",
      "data": {"patient_id": "123", "test": "HDL", "value": "60 mg/dL"},
      "auth_token": "Bearer <LAB_JWT>"
    }
    ```
- **Validation**: Enforces MCP schema compliance with JSON Schema or Protobuf.

## Response Format
```json
{
  "data": {},
  "meta": {
    "timestamp": "ISO-8601",
    "request_id": "UUID",
    "git_commit_sha": "SHA" // For data-related responses
  },
  "errors": []
}
```

## Versioning
- Semantic versioning enforced in headers.
- Deprecation policy: 12-month support.

## Developer Resources
- **Developer Portal**: Interactive API documentation (Swagger/Postman).
- **SDKs**: Available for Python, JavaScript, Java.
- **FHIR Schema Guides**: Detailed guides for FHIR schema implementation.
- **Sample Webhook Implementations**.
