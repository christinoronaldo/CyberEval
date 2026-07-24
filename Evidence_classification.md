# Evidence Classification & Prioritization Methodology

## Purpose

Evidence is the foundation of every cybersecurity investigation.

Every conclusion, recommendation, confidence score, and executive decision ultimately depends on the quality of the supporting evidence.

CyberEval therefore evaluates evidence before evaluating reasoning.

This document defines how evidence is identified, classified, prioritized, and used throughout the evaluation process.

---

# Why Evidence Comes First

Cybersecurity investigations generate large amounts of information.

Not all information has the same investigative value.

For example,

- "PowerShell executed"

does not carry the same investigative weight as

- "Domain Administrator credentials successfully dumped."

Similarly,

- "VirusTotal detected 2/72"

should never outweigh

- "Mimikatz execution confirmed."

CyberEval prevents weak evidence from dominating stronger evidence by introducing structured evidence classification and prioritization.

---

# Evidence Philosophy

CyberEval follows four principles.

## Principle 1

Evidence is evaluated independently before conclusions are formed.

---

## Principle 2

Evidence strength is determined by reliability rather than frequency.

Multiple weak indicators should not outweigh one confirmed finding.

---

## Principle 3

Unknowns remain unknown.

Lack of evidence is not evidence.

---

## Principle 4

Evidence should always remain traceable.

Every significant conclusion must reference one or more supporting evidence items.

---

# Evidence Lifecycle

Every evidence item follows the same lifecycle.

```
Raw Observation

↓

Evidence Extraction

↓

Normalization

↓

Classification

↓

Weight Assignment

↓

Priority Assignment

↓

Reasoning Support

↓

Confidence Calculation

↓

Executive Reporting
```

Evidence should never bypass any stage.

---

# Evidence Categories

CyberEval classifies evidence into four categories.

---

# Tier 1 — Direct Evidence

## Definition

Evidence that independently confirms an event.

This evidence has the highest investigative value.

Examples

- Credential dumping confirmed

- Successful authentication

- Malware executed

- LSASS accessed

- Data exfiltration confirmed

- Registry modified

- Process execution confirmed

Characteristics

✔ Observable

✔ Verifiable

✔ Directly supports conclusions

✔ High confidence

---

# Tier 2 — Supporting Evidence

Supporting evidence strengthens another finding but rarely proves a conclusion independently.

Examples

- Defender disabled

- Scheduled task created

- PowerShell launched

- Office macro executed

- Suspicious registry key

Characteristics

✔ Supports investigation

✔ Requires correlation

✔ Medium evidentiary value

---

# Tier 3 — Contextual Evidence

Context improves understanding without proving technical events.

Examples

- Threat intelligence

- VirusTotal score

- Previous campaigns

- IOC similarity

- Historical malware activity

Characteristics

✔ Useful context

✔ Low evidentiary weight

✔ Never used alone

---

# Tier 4 — Unknowns

Unknowns represent unanswered investigative questions.

Examples

- Was persistence removed?

- Was ransomware attempted?

- Was data stolen?

- Was encryption successful?

- What was the attacker's objective?

Unknowns are never treated as evidence.

Instead,

they reduce confidence.

---

# Evidence Reliability

Every evidence item should be evaluated for reliability.

CyberEval recommends five reliability levels.

| Reliability | Description |
|-------------|-------------|
| Confirmed | Directly observed |
| Strong | Supported by multiple independent sources |
| Moderate | Supported but incomplete |
| Weak | Single indirect indicator |
| Unknown | Reliability cannot be determined |

Reliability influences confidence.

It does not determine priority.

---

# Evidence Weighting

Evidence weighting determines investigative importance.

Weight should consider:

- Directness

- Reliability

- Independence

- Corroboration

- Relevance

CyberEval deliberately avoids fixed numerical values.

Organizations should define weighting appropriate for their environment.

---

# Evidence Prioritization

Priority determines review order.

High-priority evidence should always be reviewed first.

Typical priority order:

1. Credential compromise

2. Privilege escalation

3. Active malware execution

4. Lateral movement

5. Persistence

6. Command and Control

7. Defense evasion

8. Discovery

9. Collection

10. Exfiltration indicators

11. Threat intelligence

12. Environmental context

---

# Evidence Conflicts

Evidence sometimes contradicts itself.

Example

```
Memory analysis shows malware.

↓

Disk scan reports clean.
```

CyberEval never resolves conflicts automatically.

Instead,

conflicting evidence should be highlighted for analyst review.

---

# Missing Evidence

CyberEval explicitly records missing evidence.

Examples include

- Memory analysis pending

- Network captures unavailable

- Log retention expired

- Endpoint offline

Missing evidence should reduce confidence.

It should never increase certainty.

---

# Traceability

Every conclusion should reference supporting evidence.

Example

```
Conclusion

↓

Supporting Evidence

↓

Evidence ID

↓

Original Observation
```

This allows reviewers to reproduce every evaluation.

---

# Common Mistakes

CyberEval discourages the following practices.

❌ Treating contextual evidence as confirmation

❌ Ignoring contradictory evidence

❌ Inferring attacker objectives

❌ Using absence of evidence as confirmation

❌ Overweighting VirusTotal results

❌ Assuming campaign attribution

❌ Ignoring investigation status

---

# Best Practices

✔ Preserve raw evidence

✔ Separate observations from interpretation

✔ Record unknowns explicitly

✔ Prioritize direct evidence

✔ Keep evidence traceable

✔ Justify confidence

✔ Allow analyst review

---

# Summary

Evidence is the foundation of CyberEval.

The framework deliberately evaluates evidence before reasoning because strong reasoning cannot exist without reliable evidence.

Every later stage—including confidence calibration, hallucination detection, business risk assessment, and executive reporting—depends on the quality and prioritization of the evidence established in this document.