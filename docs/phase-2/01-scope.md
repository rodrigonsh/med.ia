# Phase 2: Institutional Integration Scope

## Data Infrastructure
- Write capabilities for Git repositories
- Conflict resolution mechanisms (CRDTs)
- Bulk data import/export pipelines
- Enhanced Git hooks for validation

## API Layer
- Write API endpoints:
  - POST /patients/{id}/records
  - PATCH /patients/{id}/records/{version}
- Bulk operations:
  - POST /bulk/import
  - GET /bulk/export
- Webhook notifications
- Enhanced OAuth scopes:
  - lab:write
  - hospital:write
  - admin:manage

## MCP Server
- Basic MCP server implementation
- FHIR-to-MCP adapters
- Context retrieval endpoints
- Data update endpoints
- Audit logging for MCP operations

## AI Integration
- Basic question-answering system
- PHI anonymization layer
- Vector embeddings for FHIR data
- Simple RAG pipeline

## Security
- Attribute-Based Access Control (ABAC)
- Break-glass emergency access
- Enhanced audit logging
- PHI detection and masking

## Limitations
- No enterprise contracts
- Basic AI only
- No government compliance
- Single-region deployment
