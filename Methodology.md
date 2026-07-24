# CyberEval Evaluation Methodology

## Purpose

This document defines the complete evaluation methodology used by the CyberEval framework.

Rather than measuring only whether an AI-generated cybersecurity assessment is correct, CyberEval evaluates the complete decision-making process that produced the assessment. The methodology focuses on the relationship between evidence, reasoning, confidence, business risk, and executive communication.

Every evaluation follows the same structured workflow to ensure consistency, transparency, and reproducibility.

---

# Evaluation Philosophy

CyberEval is founded on one principle:

> **Conclusions should be earned through evidence, not assumed through confidence.**

A technically correct answer produced through unsupported reasoning is considered unreliable.

Likewise, a cautious answer that clearly communicates uncertainty is often more valuable than an overconfident answer that hides missing evidence.

For this reason, CyberEval evaluates the reasoning process rather than only the final response.

---

# End-to-End Evaluation Pipeline

Every evaluation follows the same sequence.

```
Cybersecurity Incident

        │
        ▼

Input Processing

        │
        ▼

Evidence Extraction

        │
        ▼

Evidence Classification

        │
        ▼

Evidence Weighting

        │
        ▼

Reasoning Evaluation

        │
        ▼

Confidence Calibration

        │
        ▼

Hallucination Detection

        │
        ▼

Risk Assessment

        │
        ▼

Executive Readiness

        │
        ▼

Final Evaluation Report
```

Every stage produces structured outputs that become inputs for the following stage.

---

# Stage 1 — Input Processing

## Objective

Understand the incident before evaluating the AI response.

The evaluator should identify:

- Incident timeline
- Available evidence
- Missing information
- Investigation status
- Known unknowns
- Business context

No assumptions should be made during this stage.

Only documented information should be collected.

### Output

Structured incident context.

---

# Stage 2 — Evidence Extraction

Every factual observation should be extracted independently.

Examples include:

- Defender disabled
- Mimikatz executed
- Domain Admin credentials dumped
- Scheduled task created
- Active HTTPS C2
- No ransomware observed
- Investigation ongoing

Evidence should remain atomic.

Avoid combining multiple observations into one statement.

### Output

Evidence inventory.

---

# Stage 3 — Evidence Classification

Every evidence item is classified according to its evidentiary strength.

CyberEval defines four evidence categories.

## Tier 1 — Direct Evidence

Evidence directly confirming an event.

Examples

- Credential dumping confirmed
- Malware executed
- Successful authentication
- LSASS accessed

Highest confidence.

---

## Tier 2 — Supporting Evidence

Evidence supporting another conclusion without proving it independently.

Examples

- Defender disabled
- PowerShell execution
- Scheduled task
- Registry modification

---

## Tier 3 — Contextual Evidence

Evidence providing useful context.

Examples

- VirusTotal score
- Threat intelligence matches
- Previous campaigns
- Historical indicators

---

## Tier 4 — Unknowns

Questions that remain unanswered.

Examples

- Was data stolen?
- Was persistence removed?
- Was ransomware attempted?
- What was the attacker's objective?

Unknowns are never treated as evidence.

---

# Stage 4 — Evidence Weighting

Not every evidence item contributes equally.

CyberEval evaluates:

- Reliability
- Relevance
- Directness
- Independence
- Corroboration

Higher-weight evidence should dominate lower-weight indicators.

For example:

```
Credential Dumping

>

PowerShell

>

VirusTotal

```

This prevents weak contextual indicators from overriding confirmed technical findings.

---

# Stage 5 — Reasoning Evaluation

CyberEval evaluates whether the AI's conclusions logically follow from the available evidence.

The evaluator should determine:

- Are all conclusions supported?
- Were important facts ignored?
- Were unsupported assumptions introduced?
- Does the reasoning remain internally consistent?
- Are unknowns acknowledged?

A technically correct answer with weak reasoning receives a lower evaluation than a well-reasoned answer with appropriately stated uncertainty.

---

# Stage 6 — Confidence Calibration

Confidence should represent evidence strength.

Confidence should never compensate for missing evidence.

CyberEval defines four confidence levels.

| Level | Meaning |
|--------|----------|
| Low | Evidence is insufficient |
| Medium | Evidence suggests but does not confirm |
| High | Strong supporting evidence exists |
| Very High | Multiple independent evidence sources directly support the conclusion |

Confidence must always be justified.

---

# Stage 7 — Hallucination Detection

CyberEval classifies hallucinations by reasoning pattern.

Examples include:

- Anchoring Bias
- Confirmation Bias
- Unsupported Certainty
- Premature Closure
- Scope Creep
- False Causality
- Overgeneralization
- Unsupported Attribution

The objective is not simply to identify hallucinations but to explain why they occurred.

---

# Stage 8 — Risk Assessment

Incorrect conclusions introduce risk.

CyberEval evaluates:

- Technical Risk
- Business Risk
- Operational Risk
- Executive Risk

Risk increases when incorrect reasoning influences important decisions.

---

# Stage 9 — Executive Readiness

An AI response should be suitable for executive communication.

The evaluator determines whether the report:

- avoids unsupported certainty,
- communicates uncertainty clearly,
- highlights business impact,
- prioritizes significant findings,
- avoids unnecessary technical detail,
- remains actionable.

---

# Stage 10 — Final Evaluation

Every evaluation concludes with a structured assessment.

The report includes:

- Overall Verdict
- Technical Accuracy
- Evidence Usage
- Reasoning Quality
- Confidence Calibration
- Hallucination Analysis
- Business Risk
- Executive Readiness
- Recommended Rewrite
- Remaining Unknowns

---

# Guiding Principles

Every CyberEval assessment follows five immutable principles.

1. Evidence precedes conclusions.
2. Unknowns remain unknown until supported.
3. Confidence reflects evidence.
4. Business impact influences prioritization.
5. Human reviewers make final decisions.

---

# Summary

CyberEval evaluates far more than factual correctness.

It evaluates whether the AI reached the correct conclusion for the right reasons.

The framework therefore measures the complete reasoning process, ensuring that conclusions remain explainable, evidence-based, and operationally trustworthy.