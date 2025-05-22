# MED.ia Technical Context

## Core Stack
- **API Layer**: Laravel (PHP)
- **MCP Server**: Python (FastAPI)
- **AI Services**: Python (PyTorch)
- **Database**: PostgreSQL
- **Cache**: Redis

## Development Tools
- **Version Control**: Git LFS
- **CI/CD**: GitHub Actions
- **Testing**: pytest, PHPUnit
- **Documentation**: Swagger, MkDocs

## Dependencies
- **FHIR**: HAPI FHIR
- **Security**: OAuth 2.0, JWT
- **AI/ML**: HuggingFace, LangChain
- **Monitoring**: Prometheus, Grafana

## Infrastructure
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Storage**: Ceph (for large binaries)
- **Networking**: Envoy proxy

## Compliance Requirements
- **Data Formats**: FHIR R4
- **Encryption**: AES-256 at rest
- **Audit**: Blockchain logging
- **Access**: ABAC with OPA
