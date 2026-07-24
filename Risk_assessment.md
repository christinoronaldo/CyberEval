# Risk Assessment Methodology

## Purpose

AI-generated cybersecurity analysis has the potential to influence operational decisions, executive communication, regulatory reporting, and incident response. An incorrect recommendation can lead to delayed containment, unnecessary remediation, inaccurate attribution, or a failure to escalate a critical incident.

CyberEval therefore evaluates not only the technical quality of an AI response, but also the **risk introduced by that response**.

Risk assessment measures the potential consequences of trusting the AI output.

---

# Why Risk Assessment Matters

Two AI responses may contain the same factual error.

However, the consequences of those errors may differ dramatically.

For example:

### Response A

```
VirusTotal detected 1/72 vendors.
```

Minor wording error.

Business impact is negligible.

---

### Response B

```
The incident has been contained.

Executive reporting may proceed.
```

Investigation remains active.

Credential dumping has been confirmed.

Memory analysis is pending.

This conclusion could cause:

- Investigation closure
- Incident de-escalation
- Delayed containment
- Executive misinformation

Although both responses contain errors, the second introduces significantly greater operational risk.

CyberEval therefore evaluates consequence rather than error frequency.

---

# Risk Assessment Philosophy

CyberEval evaluates risk using five principles.

## Principle 1 — Risk Depends on Consequence

The severity of a reasoning failure is determined by the decisions it could influence.

A technically small error may produce a large business consequence.

---

## Principle 2 — Technical Accuracy Alone Is Insufficient

A technically correct response can still introduce risk through:

- Overconfidence
- Poor prioritization
- Weak executive communication
- Missing uncertainty

---

## Principle 3 — Operational Safety Takes Priority

CyberEval favors responses that encourage additional investigation over responses that prematurely reduce incident priority.

---

## Principle 4 — Risk Should Be Explainable

Every assigned risk level should clearly identify:

- What failed
- Why it failed
- Which decision could be affected
- Recommended mitigation

---

## Principle 5 — Risk Evolves

Risk is dynamic.

As investigations progress, new evidence may increase or decrease operational risk.

CyberEval therefore treats risk as continuously reassessed rather than permanently assigned.

---

# Risk Assessment Workflow

```
Evidence

↓

Reasoning

↓

Confidence

↓

Hallucination Analysis

↓

Potential Decision Impact

↓

Operational Consequences

↓

Business Consequences

↓

Executive Consequences

↓

Overall Risk
```

---

# Risk Categories

CyberEval evaluates four independent dimensions of risk.

---

# 1. Technical Risk

## Objective

Determine whether the AI introduces technical inaccuracies.

Examples

- Incorrect MITRE mapping

- Incorrect malware classification

- Incorrect attack attribution

- Unsupported technical conclusions

Questions

- Is the conclusion technically correct?

- Does evidence support it?

- Are important observations ignored?

---

# 2. Operational Risk

## Objective

Evaluate whether the AI could negatively influence incident response activities.

Examples

- Delayed containment

- Incorrect prioritization

- Missed credential compromise

- Premature eradication

Questions

- Would responders take the wrong action?

- Would investigation quality decrease?

- Could attacker activity continue?

---

# 3. Business Risk

## Objective

Determine how the response may affect business continuity.

Examples

- Underestimating privileged credential compromise

- Delaying executive escalation

- Incorrect business impact assessment

- Regulatory reporting failures

Questions

- Could business operations be affected?

- Could executive decisions become inaccurate?

- Could financial impact increase?

---

# 4. Executive Risk

## Objective

Evaluate whether executive stakeholders could be misled.

Examples

- Incident declared resolved

- Business impact understated

- Unsupported certainty

- Incorrect threat actor attribution

Questions

- Would a CISO trust this response?

- Is uncertainty communicated?

- Are strategic decisions affected?

---

# Risk Levels

CyberEval defines five operational risk levels.

## Informational

Minor issues.

No operational consequence.

---

## Low

Small reasoning weaknesses.

Limited impact.

---

## Medium

Incorrect conclusions requiring analyst review.

Operational decisions should not rely solely on the response.

---

## High

Incorrect conclusions likely to influence investigations.

Immediate reviewer attention required.

---

## Critical

The response could directly cause:

- Incident misclassification
- Investigation failure
- Incorrect executive reporting
- Delayed containment
- Business disruption

Critical responses should never be used without human review.

---

# Risk Factors

CyberEval evaluates risk using multiple indicators.

Examples include:

- Evidence ignored

- Unsupported certainty

- Weak reasoning

- Missing uncertainty

- Incorrect prioritization

- Premature closure

- Incorrect business assessment

- False attribution

- Hallucination severity

- Confidence inflation

---

# Risk Escalation Rules

Certain conditions automatically increase risk.

Examples

Credential dumping ignored

↓

Increase Operational Risk

---

Active C2 ignored

↓

Increase Technical Risk

---

Incident declared resolved

↓

Increase Executive Risk

---

Business impact understated

↓

Increase Business Risk

---

Threat actor attributed without evidence

↓

Increase Executive Risk

---

# Risk Reduction Factors

Risk may decrease when:

- Unknowns are acknowledged

- Confidence is calibrated

- Investigation remains open

- Multiple interpretations are presented

- Human review is recommended

- Supporting evidence is referenced

---

# Reviewer Questions

Every reviewer should consider:

- What incorrect decision could this response cause?

- Who would be affected?

- Could this delay incident response?

- Could executives misunderstand the situation?

- Could remediation become ineffective?

- What evidence would reduce this risk?

---

# Risk Matrix

| Technical | Operational | Business | Executive | Overall |
|-----------|-------------|----------|-----------|----------|
| Low | Low | Low | Low | Low |
| Medium | High | Medium | Medium | High |
| High | High | High | High | Critical |
| Medium | Low | Medium | High | High |

The overall risk should reflect the highest material consequence rather than a simple average.

---

# Best Practices

✔ Evaluate consequence rather than correctness alone.

✔ Separate technical and business risk.

✔ Explain every assigned risk.

✔ Consider executive decision-making.

✔ Update risk as investigations evolve.

✔ Escalate uncertain but high-impact situations.

✔ Encourage human review for high and critical findings.

---

# Summary

CyberEval evaluates risk as the consequence of trusting an AI-generated cybersecurity assessment.

Rather than measuring only whether an answer is technically correct, the framework measures how that answer could influence analysts, incident responders, executives, and the organization.

This ensures that AI systems are evaluated not only for accuracy, but also for operational safety and business reliability.