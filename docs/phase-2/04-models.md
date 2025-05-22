# Phase 2: Data Models

## MCP Context Model
```json
{
  "context_type": "medical_history",
  "patient_id": "123",
  "data": {
    "HbA1c": "6.5%",
    "date": "2023-10-01",
    "source_commit": "abc123"
  },
  "permissions": {
    "read_scope": "patient:read",
    "write_scope": "lab:write"
  }
}
```

## AI Query Model
```json
{
  "query_id": "q123",
  "question": "What's the patient's HbA1c trend?",
  "context_types": ["lab_results"],
  "anonymized": true,
  "response": {
    "text": "The patient's HbA1c has decreased from 7.2% to 6.5% over 6 months",
    "citations": [
      {
        "commit": "abc123",
        "resource": "Observation/example1"
      }
    ]
  }
}
```

## Webhook Notification
```json
{
  "event_id": "evt123",
  "event_type": "Observation:create",
  "patient_id": "123",
  "resource_type": "Observation",
  "resource_id": "example1",
  "timestamp": "2023-10-01T12:00:00Z",
  "institution": "LabCorp"
}
```

## Enhanced Audit Log
```json
{
  "timestamp": "2023-10-01T12:05:00Z",
  "user_id": "doctor123",
  "action": "mcp_query",
  "patient_id": "123",
  "query_id": "q123",
  "blockchain_tx": "tx123456"
}
```

## New Models
- MCP context objects
- AI query/response
- Webhook payloads
- Blockchain-backed audit logs
