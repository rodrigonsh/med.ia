# Phase 1: Data Models

## Core FHIR Resources

### Patient
```json
{
  "resourceType": "Patient",
  "id": "example",
  "identifier": [
    {
      "system": "urn:oid:1.2.36.146.595.217.0.1",
      "value": "12345"
    }
  ],
  "name": [
    {
      "family": "Doe",
      "given": ["John"]
    }
  ],
  "gender": "male",
  "birthDate": "1974-12-25"
}
```

### Observation (Lab Results)
```json
{
  "resourceType": "Observation",
  "id": "example",
  "status": "final",
  "code": {
    "coding": [
      {
        "system": "http://loinc.org",
        "code": "789-8",
        "display": "Hemoglobin [Mass/volume] in Blood"
      }
    ]
  },
  "subject": {
    "reference": "Patient/example"
  },
  "effectiveDateTime": "2023-10-01",
  "valueQuantity": {
    "value": 13.2,
    "unit": "g/dL",
    "system": "http://unitsofmeasure.org",
    "code": "g/dL"
  }
}
```

## Git Metadata Model
```json
{
  "commit": {
    "sha": "abc123",
    "author": {
      "name": "LabCorp System",
      "email": "system@labcorp.com",
      "timestamp": "2023-10-01T12:00:00Z"
    },
    "message": "[LabCorp] Added HbA1c result (Order #12345)"
  },
  "verification": {
    "signature": "gpg-signature",
    "verified": true
  }
}
```

## Audit Log Model
```json
{
  "timestamp": "2023-10-01T12:05:00Z",
  "user_id": "doctor123",
  "action": "read",
  "patient_id": "example",
  "resource_type": "Observation",
  "resource_id": "example"
}
```

## Limitations
- Basic FHIR resources only
- No complex relationships
- No AI models
- Simple audit logging
