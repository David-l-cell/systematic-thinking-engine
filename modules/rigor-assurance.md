# M4: Rigor Assurance Algorithm Reference

## Input Verification

```
VERIFY(content):
  source = { identifiable: bool, credible: bool, primary: bool }
  claims = EXTRACT_CLAIMS(content)
  quality = SCORE(claims, source)
  return { source, claims, quality, concerns[] }
```

## Evidence Mapping

```
MAP_EVIDENCE(claim):
  evidence = { direct[], indirect[], contradictory[] }
  gaps = claims_without_evidence
  level = CLASSIFY(evidence):
    well_supported | partially_supported | weakly_supported | unsupported
  label = if score >= 0.95: CONFIRMED elif >= 0.75: LIKELY
          elif >= 0.50: PLAUSIBLE elif >= 0.25: UNCERTAIN
          elif conflicting: DISPUTED else: UNKNOWN
  return { claim, evidence, gaps, level, label, confidence, rationale }
```

## Fabrication Guard

```
GUARD(assertion_type):
  IF assertion_type == FACT:
    CHECK: source_traceable, is_current, precision_appropriate, sufficient_examples
  IF assertion_type == CONCLUSION:
    CHECK: premises_supported, logically_necessary, alternatives_considered, confidence_calibrated
  IF assertion_type == CITATION:
    CHECK: source_exists, content_matches, context_accurate
```

## Logic Validation

```
VALIDATE(conclusions):
  non_contradiction: ∀ci,cj, ci ∧ cj ≠ ⊥
  transitivity: ∀a→b,b→c, verify a→c
  completeness: no unbridgeable logical gaps
  soundness: ∀premises, verified true, not just structurally valid
  RETURN { passed[], failed[], critical[], overall_valid }
```

## Output Sanitization

```
SANITIZE(output):
  separate: facts[] vs interpretations[]
  FOR each assertion: label with uncertainty taxonomy
  flag: assumptions[], inferred[] (vs observed[])
  attach: limitations[], alternative_perspectives[]
  audit: { timestamp, content_id, verification, labels[], logic, issues[], notes }
```