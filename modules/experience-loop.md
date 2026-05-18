# M2: Experience Loop Algorithm Reference

## Outcome Classification

```
CLASSIFY(task) → { type: success|partial|failure, confidence: 0-1 }
metrics = { goal_achievement, efficiency, quality, timeliness } // all 0-1
```

## Success Pattern Extraction

```
EXTRACT_SUCCESS(task):
  factors = { necessary(weight=1.0), contributing(0.5-0.9), enabling(0.3-0.5) }
  return { preconditions[], action_sequence[{order,action,rationale,isCritical}],
           success_indicators[], applicability[], anti_conditions[], confidence, source_ids[] }
```

## Failure Analysis

```
ANALYZE_FAILURE(task):
  // 5 Whys
  chain = [{level:1..5, description, why_question}]
  error_type = CLASSIFY(chain): structural | execution | environmental | knowledge
  rule = { condition, constraint, rationale, alternative, verification, priority: critical|high|medium }
  return { failure_mode, chain, error_type, detectability, rules[], lessons[] }
```

## Repository Management (backed by modules/repository-persistence.md)
REPO=~/.qclaw/se-experiences/
STORE: write REPO/[type]/[task]/[id].json → update meta/index.json | dup merge | conflict flag
RETRIEVE: read index.json → filter(task_type) → top-3×(conf×recency) → return top-3
PRUNE: 30d+conf<0.5→archive | total>100→del lowest | conflicts never deleted
> CRITICAL: 必须执行真实文件I/O。目录不存在则自动创建。