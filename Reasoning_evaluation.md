# Reasoning Evaluation Methodology

## Purpose

Correct conclusions do not necessarily indicate correct reasoning.

An AI model may produce the correct answer through flawed logic, unsupported assumptions, incomplete evidence, or accidental pattern matching. While the final conclusion may appear acceptable, the reasoning process itself may introduce significant operational risk if repeated in future scenarios.

CyberEval therefore evaluates the reasoning process independently of the final answer.

The objective is to determine whether the AI reached its conclusion through defensible, evidence-based reasoning.

---

# Why Reasoning Matters

Cybersecurity investigations rarely operate with complete information.

Analysts continuously make decisions based on incomplete evidence, evolving investigations, and uncertain threat activity.

AI systems must therefore demonstrate not only technical correctness, but also disciplined reasoning.

An answer should only be considered trustworthy when:

- conclusions are supported by evidence,
- assumptions are clearly identified,
- uncertainty is communicated appropriately,
- contradictory evidence is acknowledged,
- unknowns remain unknown.

Reasoning quality directly influences confidence, business risk, and executive decision-making.

---

# CyberEval Reasoning Principles

Every reasoning chain is evaluated using five fundamental principles.

## Principle 1 — Evidence Before Inference

Observations must always precede conclusions.

Incorrect:

```
The attacker attempted ransomware deployment.

↓

No ransomware evidence was observed.
```

Correct:

```
No ransomware activity was observed.

↓

The available evidence is insufficient to determine whether ransomware deployment was attempted.
```

Evidence should always drive the conclusion.

---

## Principle 2 — Every Conclusion Requires Support

Every significant statement should be traceable to one or more evidence items.

Example:

```
Conclusion:

Credential theft occurred.

↓

Supporting Evidence

• Mimikatz executed

• LSASS accessed

• Domain Administrator credentials dumped
```

If no supporting evidence exists, the conclusion should be classified as unsupported.

---

## Principle 3 — Unknowns Remain Unknown

CyberEval discourages speculative reasoning.

Unknown information should remain explicitly unknown until supported by evidence.

Incorrect:

```
The attacker failed.
```

Correct:

```
The attacker's objective cannot be determined from the available evidence.
```

---

## Principle 4 — Confidence Must Reflect Evidence

Confidence is a consequence of evidence quality.

Confidence should never compensate for missing information.

Strong evidence permits strong conclusions.

Weak evidence requires cautious reasoning.

---

## Principle 5 — Business Context Matters

Cybersecurity reasoning should consider operational impact.

For example,

Credential theft without ransomware may still represent a critical incident due to the compromise of privileged access.

Business consequences should influence prioritization without changing the underlying evidence.

---

# Reasoning Workflow

Every evaluation follows the same reasoning workflow.

```
Evidence

↓

Evidence Classification

↓

Evidence Prioritization

↓

Inference Generation

↓

Logical Validation

↓

Contradiction Detection

↓

Unknown Identification

↓

Confidence Calibration

↓

Risk Assessment

↓

Executive Communication
```

Reasoning should progress sequentially.

Stages should not be skipped.

---

# Reasoning Components

CyberEval evaluates six core reasoning components.

---

## 1. Observation Quality

Questions:

- Were observations extracted correctly?
- Were important facts omitted?
- Were observations altered?
- Were assumptions introduced during extraction?

Expected Output:

Verified observations.

---

## 2. Evidence Correlation

Questions:

- Were related observations connected correctly?
- Were unrelated observations incorrectly linked?
- Was causal reasoning justified?

Expected Output:

Evidence relationships.

---

## 3. Inference Quality

Questions:

- Does the conclusion logically follow?
- Were intermediate reasoning steps omitted?
- Were unsupported assumptions introduced?
- Does the evidence justify the certainty?

Expected Output:

Validated reasoning chain.

---

## 4. Contradiction Analysis

Questions:

- Does one conclusion conflict with another?
- Are contradictory evidence items acknowledged?
- Were inconsistencies ignored?

Expected Output:

Contradiction report.

---

## 5. Unknown Identification

Questions:

- Which investigative questions remain unanswered?
- Are unknowns clearly separated from evidence?
- Were unknowns converted into assumptions?

Expected Output:

Unknown inventory.

---

## 6. Final Reasoning Assessment

Questions:

- Is the reasoning complete?
- Is the reasoning traceable?
- Is uncertainty appropriate?
- Is the conclusion operationally safe?

Expected Output:

Reasoning quality score.

---

# Reasoning Quality Levels

CyberEval defines four reasoning levels.

## Excellent

Characteristics:

- Evidence-driven
- Complete
- Traceable
- Consistent
- Well calibrated

---

## Good

Characteristics:

- Mostly supported
- Minor omissions
- Appropriate confidence
- Small logical gaps

---

## Weak

Characteristics:

- Missing evidence
- Unsupported assumptions
- Weak logical progression
- Limited traceability

---

## Poor

Characteristics:

- Speculative
- Contradictory
- Unsupported certainty
- Significant reasoning failures

---

# Common Reasoning Failures

CyberEval identifies recurring reasoning failures.

---

## Unsupported Assumption

Drawing conclusions without supporting evidence.

Example:

```
The attacker intended ransomware deployment.
```

No evidence supports this objective.

---

## False Causality

Assuming one event caused another without evidence.

Example:

```
No encryption occurred.

↓

The ransomware deployment failed.
```

Alternative explanations remain possible.

---

## Premature Closure

Concluding an investigation before sufficient evidence exists.

Example:

```
The malware has been removed.

↓

The incident is resolved.
```

No supporting evidence confirms complete eradication.

---

## Confirmation Bias

Overemphasizing evidence supporting an existing conclusion.

Example:

```
FIN7 infrastructure observed.

↓

Attack attributed to FIN7.
```

Contradictory indicators ignored.

---

## Anchoring Bias

Allowing one observation to dominate the reasoning process.

Example:

```
VirusTotal 2/72

↓

File is safe.
```

Weak contextual evidence outweighs stronger technical findings.

---

## Scope Creep

Extending conclusions beyond available evidence.

Example:

```
Single workstation compromised.

↓

Enterprise-wide compromise confirmed.
```

---

## Overgeneralization

Applying limited evidence to broad conclusions.

Example:

```
No ransomware.

↓

Business impact is low.
```

Credential theft alone may create significant operational risk.

---

# Traceability

Every reasoning chain should remain reproducible.

CyberEval recommends the following structure.

```
Observation

↓

Evidence ID

↓

Evidence Category

↓

Inference

↓

Conclusion

↓

Confidence

↓

Business Risk
```

Every reviewer should be able to reconstruct the decision.

---

# Best Practices

✔ Separate observations from conclusions

✔ Keep unknowns explicit

✔ Justify every inference

✔ Challenge assumptions

✔ Document uncertainty

✔ Preserve traceability

✔ Avoid narrative reasoning unsupported by evidence

---

# Summary

CyberEval evaluates reasoning rather than simply evaluating answers.

A technically correct response is only considered trustworthy when the reasoning process remains evidence-driven, logically consistent, transparent, and appropriate for the available information.

By separating reasoning evaluation from factual correctness, CyberEval helps reviewers identify failures that traditional benchmarking methods often overlook.