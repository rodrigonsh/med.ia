# Phase 1: Core Use Cases

## Patient Data Access
1. **View Medical History**
   - Actor: Patient or authorized healthcare provider
   - Flow:
     1. Authenticate via OAuth with read scope
     2. GET /patients/{id}/records
     3. System returns FHIR bundle with patient data
     4. Client displays medical history

2. **View Specific Record**
   - Actor: Patient or authorized healthcare provider
   - Flow:
     1. Authenticate via OAuth with read scope
     2. GET /patients/{id}/records?date=YYYY-MM-DD
     3. System returns specific version of record
     4. Client displays requested record

## System Administration
1. **Add New Patient**
   - Actor: System administrator
   - Flow:
     1. Initialize new Git repository for patient
     2. Create base FHIR Patient resource
     3. Commit initial data structure

2. **Audit Access**
   - Actor: Compliance officer
   - Flow:
     1. Query audit logs
     2. Verify access patterns
     3. Generate compliance report

## Developer Use Cases
1. **Setup Development Environment**
   - Actor: Developer
   - Flow:
     1. Clone development repository
     2. Run docker-compose up
     3. Verify API endpoints

2. **Test API Integration**
   - Actor: Developer
   - Flow:
     1. Obtain OAuth token
     2. Make test API calls
     3. Verify responses

## Limitations
- No data modification via API
- No bulk operations
- No webhook notifications
- Basic permissions only
