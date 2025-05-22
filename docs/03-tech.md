# Technology Stack

## Core Components

### Backend
- **Languages**: Go/Python (FastAPI) for high-throughput healthcare workloads.
- **Database**: Postgres (for metadata).
- **Caching**: Redis.

### Git Layer
- **Git Infrastructure**: Gitaly (GitLab) or libgit2 for core Git operations.
- **Scaling**: VFS for Git (scaling to 100M+ patient repos).

### AI
- **LLM Integration**: Hugging Face Transformers + FHIR-specific fine-tuning.
- **AI Pipeline**: NVIDIA CLARA for FHIR-model training.

### MCP Server
- **Framework**: FastAPI (Python) or Go.
- **Endpoints**: POST `/mcp/query` for context retrieval, POST `/mcp/update` for tool-initiated data writes.
- **Validation**: Enforce MCP schema compliance with JSON Schema or Protobuf.

### Policy Engine
- **Framework**: Open Policy Agent (OPA) for Rego policies.
- **Enterprise Control**: Styra DAS for enterprise SSO/SLA controls.

## Infrastructure

### Hosting
- **Cloud Providers**: HIPAA-compliant clouds (AWS GovCloud, Azure Healthcare APIs).
- **Encryption**: Encrypt data at rest (AES-256) and in transit (TLS 1.3).

### Data Management
- **Backups & Disaster Recovery**: Geo-redundant Git mirrors (e.g., GitHub Enterprise Server + AWS Backup).
- **Data Retention**: Minimum 10-year data retention.

### Compliance
- **Automated Audits**: GitBlit for real-time commit monitoring against HIPAA rules, AWS Macie for scanning accidental PHI.
- **Geo-Fencing**: Spiffe-based workload identity enforces data residency.
- **Reporting**: Drata (automated HIPAA reporting).

## Development Tools & Practices
- **Developer Portal**: Interactive API docs (Swagger/Postman), SDKs (Python/JS/Java).
- **FHIR Schema Guides**: Comprehensive documentation for FHIR schema implementation.
- **EHR Integration**: Pre-built connectors for Epic/Cerner EHR systems.
- **Open Source**: Open-Source FHIR-to-Git converter (Apache 2.0).
