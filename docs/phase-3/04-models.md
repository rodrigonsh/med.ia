# Phase 3: Enterprise Data Models

## Compliance Models
```json
{
  "access_request": {
    "patient_id": "123",
    "purpose": "treatment",
    "expires": "2025-12-31T23:59:59Z",
    "attributes": {
      "role": "doctor",
      "institution": "GeneralHospital",
      "location": "US-CA"
    }
  }
}
```

## Risk Model Output
```json
{
  "patient_id": "123",
  "risk_score": 0.82,
  "factors": [
    {
      "factor": "HbA1c > 7%",
      "weight": 0.35,
      "evidence": "Observation/example1"
    }
  ],
  "recommendations": [
    "Schedule endocrinology consult",
    "Increase glucose monitoring"
  ]
}
```

## Synthetic Patient
```json
{
  "synthetic_id": "synth-123",
  "based_on": "cluster-5",
  "demographics": {
    "age": 45,
    "gender": "female",
    "location": "US-NY"
  },
  "conditions": [
    {
      "code": "E11.65",
      "synthetic": true,
      "privacy_level": 0.95
    }
  ]
}
```

## Audit Trail
```json
{
  "timestamp": "2025-05-22T05:31:00Z",
  "user": "system",
  "action": "data_export",
  "patient_ids": ["123", "456"],
  "compliance_check": {
    "hipaa": true,
    "gdpr": false,
    "region": "US"
  },
  "blockchain_ref": "tx123456"
}
```

## New Models
- Attribute-based access
- Risk stratification
- Synthetic patients
- Enhanced audit trails
