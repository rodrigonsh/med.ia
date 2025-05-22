# Phase 2: API Specifications

## New Endpoints

### Write Operations
- `POST /patients/{id}/records`
  - Description: Create new patient records
  - Body: FHIR resource or bundle
  - Headers:
    - `X-Commit-Message`: Descriptive message
    - `X-Institution-ID`: Authoring institution
  - Response: Commit SHA and resource IDs

- `PATCH /patients/{id}/records/{version}`
  - Description: Update existing records
  - Parameters:
    - `version`: Git commit SHA or tag
  - Body: FHIR resource patch
  - Response: New commit SHA

### Bulk Operations
- `POST /bulk/import`
  - Description: Asynchronous bulk import
  - Body: NDJSON or CSV file
  - Response: `job_id` for status tracking
  - Headers:
    - `X-Import-Type`: FHIR resource type

- `GET /bulk/status/{job_id}`
  - Description: Check import status
  - Response: Progress percentage and stats

### MCP API
- `POST /mcp/query`
  - Description: Context retrieval for AI
  - Body: MCP query object
  - Response: Context objects

- `POST /mcp/update` 
  - Description: Tool-initiated updates
  - Body: MCP update object
  - Response: Operation status

## Updated Features
- Enhanced OAuth scopes
- Webhook subscriptions
- Rate limiting tiers
- Signed commits for institutions
