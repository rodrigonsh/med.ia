# Data Models

## Core Entities

### FHIR R4 Bundles
- **Primary Data Model**: All patient medical records are stored as FHIR R4 Bundles, enforced via JSON Schema.
- **Versioned Data**: Each update to a patient's record results in a new Git commit, ensuring a complete historical version of FHIR resources.
- **Key FHIR Resources**:
    - **Patient**: Demographics, contact information.
    - **Observation**: Lab results, vital signs.
    - **Condition**: Diagnoses, medical history.
    - **MedicationRequest/Dispense**: Prescriptions and medication administration.
    - **DiagnosticReport/ImagingStudy**: Reports and metadata for medical images (DICOM/PACS).
    - **Consent**: Patient consent directives for data sharing.
- **AuditLog**: Git commit metadata combined with custom logs for all API operations (User ID, Timestamp, Action Type, Affected Records).

## AI Models

### Contextual Grounding
- **Vector Embeddings**: FHIR data is transformed into UMLS (Unified Medical Language System) concepts via ClinVar for contextual grounding.
- **RAG Pipeline**: User queries are processed through a Retrieval-Augmented Generation (RAG) pipeline, which extracts UMLS concepts and searches Git history for relevant FHIR data to inform LLM responses.

### PHI-Safe Inference
- **Confidential Processing**: Utilize secure environments (e.g., Azure Trusted Launch) for confidential LLM processing.
- **Differential Privacy**: Apply differential privacy techniques in training data to protect patient privacy.

### Specific AI Models
- **Image Analysis CNN**: Deep learning model for anomaly detection in medical imaging.
- **Drug Interaction Predictor**: Graph neural network for pharmacovigilance.
- **Risk Stratification Model**: Survival analysis for patient risk scoring.

## Model Validation
- FDA 510(k) compliance for diagnostic aids
- HIPAA-compliant training data pipelines
- Continuous monitoring for model drift detection
