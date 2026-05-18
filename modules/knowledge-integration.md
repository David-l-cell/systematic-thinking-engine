# M3: Knowledge Integration Algorithm Reference

## Knowledge Node Format

```
Node { id, domain, subdomain, type: concept|method|principle|fact|pattern,
       content, attributes: { abstraction_level: 0-1, confidence: 0-1, source },
       connections[] }
```

## Association Detection

```
DETECT(new_node, kb):
  FOR each existing_node in kb:
    IF same_domain AND similarity > 0.95: skip (redundant)
    scores = {
      semantic: cosine(embed(new), embed(existing)),
      structural: compare_patterns(new.structure, existing.structure),
      methodological: overlap(new.methods, existing.methods),
      axiological: alignment(new.values, existing.values)
    }
    composite = weighted_avg(scores)
    IF composite > THRESHOLD(0.7):
      type = CLASSIFY(scores): analogy|isomorphism|transfer|unification
      associations.append({node, score, type})
  RETURN sort(associations, by=score, desc)
```

## Principle Extraction

```
EXTRACT_PRINCIPLE(association):
  return {
    name, abstract_form (domain-agnostic),
    manifestations: { domain_a: desc, domain_b: desc },
    core_mechanism, applicability[], boundaries[], transfer_instructions
  }
```

## Transfer Bridge

```
BUILD_BRIDGE(domain_x, domain_y):
  vocab_map: { term_in_x: term_in_y }
  method_adaptations: [{ source_method, steps[], effectiveness, limitations[] }]
  emergent_insights[], application_areas[]
```

## Interdisciplinary Solver

```
SOLVE(problem):
  aspects = DECOMPOSE(problem) → [{aspect, capability, constraints}]
  FOR each aspect:
    matches = SEARCH_KB(capability, constraints)[:TOP_K]
  solution = SYNTHESIZE(aspects, mode=combinatorial_innovation)
  IF !COHERENT(solution): REFINE(solution)
  RETURN solution
```