# Data Model and Schema Specification

# Purpose

The CyberEval framework processes a wide variety of structured and unstructured information throughout the evaluation lifecycle.

To ensure interoperability, traceability, reproducibility, and scalability, every major component within the framework must exchange data through standardized schemas.

This document defines the logical data model used throughout CyberEval.

It specifies:

- Core entities
- Relationships
- Object definitions
- Processing contracts
- Data validation rules
- Serialization formats
- Traceability identifiers

This document acts as the implementation contract between every engine.

---

# Design Philosophy

CyberEval follows five principles.

## 1. Every object has a unique identity.

Every record must have a globally unique identifier.

Example

```
Evidence ID

EV-000143
```

---

## 2. Objects are immutable.

Original evidence should never be modified.

Normalization creates new objects while preserving raw evidence.

---

## 3. Every relationship is explicit.

Hidden relationships should never exist.

Every dependency should be represented.

---

## 4. Every object is traceable.

Every evaluation result should reference the evidence that produced it.

---

## 5. Every stage consumes standardized inputs.

No engine should depend on another engine's internal implementation.

---

# Core Data Model

CyberEval consists of the following entities.

```
Incident

│

├── Timeline

├── Asset

├── Evidence

├── AI Response

├── Evaluation

├── Hallucination

├── Confidence

├── Risk

├── Recommendation

└── Executive Report
```

---

# Entity Relationships

```
Incident

↓

Timeline Events

↓

Evidence

↓

Reasoning

↓

Confidence

↓

Hallucination

↓

Risk

↓

Report
```

Every downstream entity references upstream identifiers.

---

# Incident Object

Purpose

Represents one investigation.

Attributes

```
Incident ID

Title

Description

Investigation Status

Priority

Created Date

Analyst

Business Unit

Incident Type

Current Phase
```

---

# Timeline Event Object

Purpose

Represents one observed event.

Attributes

```
Event ID

Timestamp

Source

Description

Host

User

MITRE Technique

Evidence Reference
```

Multiple events belong to one incident.

---

# Evidence Object

Purpose

Stores every observation extracted during evaluation.

Attributes

```
Evidence ID

Incident ID

Category

Tier

Description

Source

Reliability

Weight

Timestamp

Supporting Artifacts

Status
```

Evidence objects remain immutable.

---

# Evidence Categories

Allowed values

```
Direct

Supporting

Contextual

Speculative
```

---

# AI Response Object

Purpose

Stores the original LLM output.

Attributes

```
Response ID

Prompt ID

Model

Version

Temperature

Timestamp

Raw Output

Execution Metadata
```

Raw responses should never be modified.

---

# Claim Object

Purpose

Represents one claim extracted from the AI response.

Attributes

```
Claim ID

Claim Text

Referenced Evidence

Confidence

Status

Reviewer Notes
```

Each response may produce multiple claims.

---

# Reasoning Object

Purpose

Represents one evaluated reasoning chain.

Attributes

```
Reasoning ID

Evidence IDs

Intermediate Inferences

Conclusion

Quality Score

Reviewer Comments
```

Reasoning should always reference evidence.

---

# Confidence Object

Purpose

Stores confidence evaluation.

Attributes

```
Confidence ID

Evidence Confidence

Reasoning Confidence

Conclusion Confidence

Unknown Count

Contradiction Count

Final Confidence
```

CyberEval separates confidence dimensions.

---

# Hallucination Object

Purpose

Represents one hallucination.

Attributes

```
Hallucination ID

Category

Claim

Supporting Evidence

Contradictory Evidence

Severity

Business Impact

Recommended Rewrite
```

---

# Risk Object

Purpose

Stores risk assessment.

Attributes

```
Risk ID

Technical Risk

Operational Risk

Business Risk

Executive Risk

Overall Risk

Reviewer Notes
```

---

# Recommendation Object

Purpose

Stores recommended analyst actions.

Attributes

```
Recommendation ID

Priority

Description

Justification

Status

Reviewer
```

Recommendations remain separate from observations.

---

# Executive Report Object

Purpose

Represents the final deliverable.

Attributes

```
Report ID

Summary

Key Findings

Risk

Confidence

Recommendations

Reviewer

Approval Status
```

---

# Relationships

One Incident

↓

Many Timeline Events

↓

Many Evidence Objects

↓

Many Claims

↓

One Evaluation

↓

Many Hallucinations

↓

One Risk Profile

↓

One Executive Report

---

# Traceability Model

Every object references its parent.

Example

```
Report

↓

Risk

↓

Hallucination

↓

Confidence

↓

Reasoning

↓

Evidence

↓

Timeline Event

↓

Incident
```

Traceability should never be broken.

---

# Validation Rules

Evidence cannot exist without an Incident.

Claims cannot exist without an AI Response.

Reasoning cannot exist without Evidence.

Confidence cannot exist without Reasoning.

Risk cannot exist without Confidence.

Reports cannot exist without Risk.

---

# Serialization

CyberEval objects should support

- JSON
- YAML
- CSV (exports)
- Database storage

JSON is recommended for internal processing.

---

# Example Evidence Schema

```json
{
  "evidence_id": "EV-102",
  "incident_id": "INC-08",
  "category": "Direct",
  "tier": 1,
  "description": "Domain Administrator credentials dumped",
  "weight": 10,
  "reliability": "High"
}
```

---

# Example Confidence Schema

```json
{
  "evidence_confidence": "High",
  "reasoning_confidence": "Medium",
  "conclusion_confidence": "Medium",
  "unknowns": 2,
  "contradictions": 1
}
```

---

# Example Hallucination Schema

```json
{
  "category": "Premature Closure",
  "severity": "Critical",
  "claim": "Incident is resolved.",
  "supported": false,
  "business_risk": "High"
}
```

---

# Versioning

Every schema should include:

- Schema Version
- Framework Version
- Evaluation Version

This enables backward compatibility.

---

# Best Practices

✔ Never overwrite original evidence.

✔ Normalize instead of modifying.

✔ Use globally unique identifiers.

✔ Maintain complete traceability.

✔ Separate observations from evaluations.

✔ Keep schemas version-controlled.

✔ Validate every object before processing.

---

# Summary

The CyberEval Data Model defines the structural foundation of the framework.

By standardizing entities, relationships, validation rules, and serialization formats, it enables every evaluation engine to communicate consistently while preserving traceability and auditability.

This specification serves as the implementation contract for developers building CyberEval.