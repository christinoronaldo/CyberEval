# Confidence Calibration Methodology

## Purpose

Confidence is one of the most influential aspects of AI-generated cybersecurity analysis.

An incorrect conclusion presented with low confidence allows analysts to investigate further.

The same conclusion presented with absolute certainty may cause incorrect incident prioritization, delayed response, inaccurate executive reporting, and poor operational decisions.

CyberEval therefore evaluates confidence independently from technical correctness.

The objective is not to determine whether the model is confident.

The objective is to determine whether the model's confidence is justified by the available evidence.

---

# Why Confidence Matters

Cybersecurity investigations rarely provide complete information.

Investigations evolve continuously.

New evidence appears.

Existing evidence changes.

Some observations are later disproven.

An AI system must therefore express confidence proportional to the available evidence rather than the apparent plausibility of its conclusion.

Confidence should communicate uncertainty—not optimism.

---

# Confidence Philosophy

CyberEval follows five principles.

## Principle 1 — Confidence is Earned

Confidence increases only when supported by evidence.

Confidence should never compensate for missing information.

---

## Principle 2 — Evidence Determines Confidence

Evidence quality directly influences confidence.

The strength of a conclusion is limited by the strength of its supporting evidence.

---

## Principle 3 — Unknowns Reduce Confidence

Every unresolved investigative question should reduce confidence.

Unknowns are never ignored.

They are explicitly incorporated into confidence assessment.

---

## Principle 4 — Contradictions Reduce Confidence

Conflicting evidence should reduce certainty until resolved.

Confidence should not increase when evidence conflicts.

---

## Principle 5 — Confidence Must Be Explainable

Every confidence level should be justifiable.

A reviewer should always be able to answer:

> Why is this confidence level appropriate?

---

# Confidence Evaluation Pipeline

```
Evidence

↓

Evidence Reliability

↓

Evidence Weight

↓

Evidence Completeness

↓

Unknown Analysis

↓

Contradiction Analysis

↓

Reasoning Quality

↓

Confidence Calibration

↓

Business Impact Adjustment

↓

Final Confidence
```

Confidence is calculated only after reasoning has been evaluated.

---

# Confidence Inputs

CyberEval evaluates confidence using multiple factors.

## Evidence Strength

Examples

- Credential dumping confirmed
- Malware execution confirmed
- Active C2 confirmed

High-quality evidence supports higher confidence.

---

## Evidence Completeness

Questions

- Are important logs missing?

- Is memory analysis available?

- Is forensic analysis complete?

Incomplete investigations reduce confidence.

---

## Unknowns

Examples

- Attacker objective unknown

- Persistence unknown

- Exfiltration unknown

- Privilege escalation unknown

Every unknown reduces certainty.

---

## Contradictory Evidence

Examples

Memory analysis detects malware.

↓

Disk scan reports clean.

Confidence should decrease until the contradiction is resolved.

---

## Reasoning Quality

Weak reasoning cannot produce high confidence.

Confidence should always reflect reasoning quality.

---

# Confidence Levels

CyberEval defines four confidence levels.

---

## Low Confidence

Characteristics

- Limited evidence
- Significant unknowns
- Multiple assumptions
- Active contradictions

Example

```
Possible phishing activity observed.

Further investigation required.
```

---

## Medium Confidence

Characteristics

- Several supporting indicators
- Some unanswered questions
- Reasonable inference
- Investigation ongoing

Example

```
The activity resembles credential theft,
although additional forensic evidence is required.
```

---

## High Confidence

Characteristics

- Strong direct evidence
- Few unknowns
- Consistent reasoning
- No major contradictions

Example

```
Credential dumping has been confirmed through
Mimikatz execution, LSASS access,
and successful extraction of Domain Administrator credentials.
```

---

## Very High Confidence

Characteristics

- Multiple independent evidence sources
- Complete investigation
- Strong reasoning
- Minimal uncertainty

This level should be used sparingly.

CyberEval discourages unnecessary certainty.

---

# Confidence Calibration Errors

CyberEval identifies common confidence failures.

---

## Overconfidence

Confidence exceeds available evidence.

Example

```
The attacker was FIN7.
```

Only infrastructure overlap exists.

Proper confidence:

Medium.

---

## Underconfidence

Strong evidence exists,
yet the model communicates excessive uncertainty.

Example

```
Credential theft may have occurred.
```

Evidence:

- Mimikatz executed

- LSASS accessed

- Domain Admin credentials dumped

Proper confidence:

High.

---

## Unsupported Certainty

Absolute statements made without evidence.

Example

```
The attacker failed.
```

No evidence supports knowledge of the attacker's objective.

---

## False Precision

Artificially precise confidence.

Example

```
Confidence: 97%
```

CyberEval discourages unsupported numerical precision.

Qualitative confidence is preferred.

---

## Confidence Inflation

Confidence increases because of repeated weak indicators.

Example

```
PowerShell

Scheduled Task

Registry Change

↓

High confidence malware attribution
```

Multiple weak indicators should not outweigh stronger direct evidence.

---

# Confidence Decision Matrix

| Evidence | Unknowns | Reasoning | Recommended Confidence |
|-----------|----------|-----------|------------------------|
| Weak | High | Weak | Low |
| Moderate | Moderate | Good | Medium |
| Strong | Low | Strong | High |
| Multiple Independent Sources | Minimal | Excellent | Very High |

---

# Business Risk Considerations

Confidence should never reduce business priority.

Example

Low confidence regarding attacker identity.

↓

High confidence regarding credential compromise.

↓

Incident remains High Priority.

Confidence and business impact should be evaluated independently.

---

# Reviewer Questions

CyberEval recommends asking:

- Does the evidence justify this confidence?

- What evidence would increase confidence?

- What unknowns remain?

- Are contradictions acknowledged?

- Is the reasoning complete?

- Would another analyst assign the same confidence?

---

# Best Practices

✔ Explain confidence.

✔ Separate confidence from correctness.

✔ Reduce confidence when unknowns exist.

✔ Increase confidence only through evidence.

✔ Document remaining uncertainty.

✔ Avoid absolute statements.

✔ Re-evaluate confidence as investigations evolve.

---

# Summary

Confidence is not an expression of certainty.

It is an expression of evidential support.

CyberEval evaluates confidence as an independent quality attribute because confidence directly influences operational decisions, executive communication, and incident response prioritization.

Properly calibrated confidence improves transparency, reduces unsupported conclusions, and encourages evidence-driven decision making.