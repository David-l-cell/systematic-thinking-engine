# M1: Deep Learning Algorithm Reference

## Question Generation

```
FOR category in [foundational, boundary, cross_paradigm, meta_cognitive]:
  count = (category == 'foundational' || 'boundary') ? 3 : 2
  FOR i in 1..count:
    q = GENERATE(category, content)
    // Foundational: reverse core premise, test necessity vs contingency
    // Boundary: edge cases at parameter extremes, monotonicity violations
    // Cross-Paradigm: retrieve 2-3 competing paradigms, construct clash
    // Meta-Cognitive: bias checklist, methodological critique, observer effects
    questions.append(q)
```

## Dialectical Resolution

```
FOR each question:
  thesis = challenge perspective
  antithesis = content defense
  synthesis = RESOLVE(thesis, antithesis, strategy)
  // Strategy selection: SUBLATION | INTEGRATION | REFRAMING | CONTEXTUALIZATION | ACKNOWLEDGMENT
  insight = extract deepened understanding
```

## Contradiction Classification

```
CLASSIFY(question, synthesis):
  IF formal inconsistency → logical
  IF conflicts with observed data → empirical
  IF incommensurable frameworks → paradigmatic
  IF productive tension → dialectical
  IF seeming conflict (definitions) → apparent
  IF irresolvable → genuine
```

## Synthesis Output

```
{
  pre_state, challenged_assumptions[], resolved_insights[], unresolved_tensions[],
  growth_vector, growth_magnitude: minimal|moderate|significant|transformative
}
```