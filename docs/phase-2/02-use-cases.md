# Phase 2: Institutional Use Cases

## Data Management
1. **Lab Updates Patient Record**
   - Actor: Lab system
   - Flow:
     1. Authenticate with lab:write scope
     2. POST new Observation to /patients/{id}/records
     3. System validates and commits data
     4. Webhook notifies patient's care team

2. **Bulk Import Lab Results**
   - Actor: Lab administrator
   - Flow:
     1. Prepare NDJSON file of results
     2. POST to /bulk/import
     3. Receive job_id for tracking
     4. Check status via /bulk/status/{job_id}

## AI Integration
1. **Ask Medical Question**
   - Actor: Doctor
   - Flow:
     1. Ask "What's patient's HbA1c trend?"
     2. AI queries MCP for FHIR data
     3. System returns analysis with citations
     4. Doctor reviews clinical insights

2. **Anonymized Research Query**
   - Actor: Researcher
   - Flow:
     1. Submit aggregate question
     2. PHI anonymization layer processes
     3. AI analyzes de-identified data
     4. Returns statistical insights

## Administration
1. **Emergency Access Override**
   - Actor: ER physician
   - Flow:
     1. Activate break-glass protocol
     2. SAML assertion logged to blockchain
     3. Access patient records
     4. System notifies patient post-access

2. **Manage Institutional Permissions**
   - Actor: Hospital admin
   - Flow:
     1. Configure ABAC policies
     2. Assign roles to staff
     3. Verify access controls
     4. Audit policy changes

## New Capabilities
- Webhook notifications
- Bulk data operations
- AI-assisted queries
- Emergency access protocols
