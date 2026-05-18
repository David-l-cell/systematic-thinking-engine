---
name: "systematic-thinking-engine"
description: "Systematic thinking engine: cognitive conflict deep learning, auto-failure-recovery loop, scenario-solution mapping, cross-domain integration, rigor assurance. Invoke for reflective learning, task debugging, knowledge synthesis. Hot-pluggable for Qclaw/OpenClaw/Hermes."
---

# Systematic Thinking Engine v2.3

Execute triggered modules EXACTLY as specified. Prioritize dense, token-efficient output.

**Anti-flood**: 5分钟内同触发→缓存+"⏱(自HH:MM—force重算)" | 加force→不受时限

---

## ⚡ SKILL BOOTSTRAP (每次激活最先执行)

0a. CHECK: ~/.qclaw/se-experiences/meta/index.json存在→LOAD,repo=1 | 不存在→mkdir -p并INIT,repo=0 "REPO:initialized" | ⚡IO-ASSERT: 写入后回读index.json确认exists→通过|失败→retry×1→仍失败→报"REPO:IO-FAIL"
0b. CLASSIFY: /think deep→deep | /think reflect→meta | /think integrate→synth | /think verify→fact | /think full→full | auto→detect
0c. repo=1且∃patterns/[task_type]/ → 生成M2S5简报 | repo=1无匹配→"REPO:[N] none match" | repo=0→"REPO:first run"
0d. →触发路由

---

## TRIGGER DETECTION

| Priority | Condition | Action |
|---|---|---|
| 1(highest) | `/think deep [content]` | M1 only |
| 1 | `/think reflect` | M2 full (S1-S5) |
| 1 | `/think integrate [content]` | M3 only |
| 1 | `/think verify [claim]` | M4 only |
| 1 | `/think full [content]` | Pipeline: M1→M3→M4→M2-S5 |
| 2 | **Conversation context ≥500 chars total** (dialog + attached materials/files/text) — no manual command present | **Auto Pipeline**: M1→M3→M4→M2-S5 |
| 2 | **Any task completed** (regular/scheduled/auto/manual, success/failure/partial) | **Auto Pipeline**: M1→M3→M4→M2-S5 |

**Priority rule**: Manual commands (priority 1) override auto triggers (priority 2). `/think deep` → only M1, NOT full pipeline.

---

## M1: SCENARIO-ANCHORED DEEP LEARNING

**S1 Parse** → extract: core claims(3-5), assumptions(2-3), methodology, conclusions, stated limits. 按 modules/content-templates.md 匹配模板→结构化提取 | 无匹配→通用解析.

**S2 Generate 10 scenario-anchored questions.** Every question MUST embed `[Domain, Scale, Constraint]`. ≥3 distinct domains across the 10.

```
Q1-Q3 FOUNDATIONAL (embed explicit scenario):
  Q1: "In [domain X, small-team, tight-deadline], what if OPPOSITE of [core claim] true? Specific counter-evidence required."
  Q2: "Assume [assumption] fails in [domain Y, enterprise, regulated]. What breaks? What replaces it?"
  Q3: "List every precondition needed for [conclusion]. In [domain Z, resource-constrained], how many fail?"

Q4-Q6 BOUNDARY (specify threshold value):
  Q4: "At what exact [metric/threshold] does principle reverse? Show with [domain A] vs [domain B]."
  Q5: "Extrapolate [core idea] to mathematical limit. What paradox emerges in [domain C, extreme-scale]?"
  Q6: "2 counterexamples from [domain D] and [domain E] where framework predicts wrongly."

Q7-Q8 CROSS-PARADIGM (name competing framework):
  Q7: "How would [specific theory from discipline F] reinterpret same data? What core assumption rejected?"
  Q8: "[Law/principle G] from [unrelated field] contradicts [claim]. Resolve or accept contradiction."

Q9-Q10 META-COGNITIVE (specify bias type):
  Q9: "[Bias: confirmation/survivorship/selection] may explain findings better. Thought experiment in [domain H]."
  Q10: "Design bet: what observable outcome in [domain I, 5yr horizon] would falsify this?"
```

**S2.5 Quality Gate**
```
Q[n]: adversarial(1-5)|evidence(1-5)|novelty(1-5)
adversarial:1一句驳回5需专题 | evidence:1常识5原始数据 | novelty:1老生常谈5首次
Gate: avg(adversarial)≥3.0→proceed | Q<2.0→rewrite | avg(evidence)<2.0→deepen
Quality: avg_adv=[X.X](PASS|FAIL) weakest=Q[N]→[rewrite|ok] novelty=[X.X]
```

**S3 Dialectical resolution (inline compact):**
```
Q[n]:[1-line] T:[Against]|A:[For]|S:[Integration]|I:[Insight]
```

**S4 Contradiction map (inline):**
```
Internal:[Qx,Qy] External:[Qa,Qb] Paradigm:[Qc,Qd] Meta:[Qe,Qf]
```

**S5 Synthesis (compact):**
```
## Synthesis
Pre:[1-line prior belief]
Challenged:[assumption→status+label] (≤3)
Resolved:[insight] (≤5)
Unresolved:[genuine paradox] (≤2)
Next:[exploration direction]
```
`输出前: 断言→[OBSERVED]|推断→[INFERRED]|前提→[ASSUMPTION]|未标→⚠️`

**S6 Scenario Transfer Matrix:**
```
| [name] | [works] | [adapt] | [when] | [量化失效公式+观测周期] |
```
≥2 rows. 失效公式=metric×threshold+timeframe. 例: "ROE<8% 连2季→失效". 观测周期=月度|季度|年度.

---

## M2: CLOSED-LOOP EXPERIENCE LEARNING + REPOSITORY

### S1: Classify outcome
```
Outcome: success|partial|failure (conf:0-1)
→ success/partial → S2a | failure → S3b(loop)
```

### S2a: SUCCESS ANALYSIS

```
## Success: [task]
Factors: 1)[f1]→[why] 2)[f2]→[why] 3)[f3]→[why]
Decisions: [choice1 vs alt1→rationale] | [choice2 vs alt2→rationale]

### Reusable Success Model
PRE:[required preconditions before starting]
DO:[step1→step2→step3 — with rationale per step]
CHECK:[early signals approach is working]
WHEN-OK:[applicability conditions for reuse]
WHEN-NOT:[anti-conditions — do NOT reuse if true]

### Generalized Principle
[1-line domain-agnostic abstraction of why this worked]
```

### S2b→S3b: AUTO-FAILURE-RECOVERY LOOP (max 3 iterations)

```
ITERATION[n]/3:
  DIAGNOSE:[type: structural|execution|environmental|knowledge|requirements]
  5Whys: 1)direct→2)secondary→3)systemic→4)gap→5)root
  PROPOSE:[1-3 strategies ranked by feasibility]
  EXECUTE:[apply top fix]
  VERIFY:[YES→exit loop | NO→iteration n+1]
```

**Fix taxonomy (try ≥2 categories before unresolved):**

| Category | Action |
|---|---|
| SKILL_ADD | Add/modify capability (e.g. "need file-parser skill") |
| PATH_SWITCH | Change dimension (code→API, local→cloud, sync→async) |
| REQUIREMENT_FIX | Reassess misinterpreted requirements |
| CONSTRAINT_RELAX | Relax self-imposed constraint blocking solution |
| TOOL_UPGRADE | Switch to more capable tool/method |

```
## Recovery Report
Iterations:[n] | Status:resolved|partial|unresolved
Root:[1-line] | Fix:[type]:[what changed]
Prevention: COND=[trigger]→AVOID=[bad action]→DO=[correct action] PRIORITY:[critical|high|medium]
Cost:[extra steps]
```

### S4: EXPERIENCE REPOSITORY (persist across sessions)

**💾 PERSISTENCE**: 所有操作写入~/.qclaw/se-experiences/（见modules/repository-persistence.md）。必须真实I/O。

**STORE operation (after S2a or S3b output):**
```
STORE:
  IF success_pattern: write REPO/patterns/[task_type]/[id].json → update meta/index.json
  IF avoidance_rule: write REPO/rules/[task_type]/[id].json → update meta/index.json
  IF duplicate exists: merge, bump confidence by 0.1 (max 1.0)
  IF contradiction with existing: flag both, retain with conflict marker
```

**PRUNE operation (periodic):**
```
  Archive entries where (now - timestamp) > 30 days AND confidence < 0.5
  If total patterns > 100: remove lowest (confidence × recency) entries
  Conflicts never deleted
```

### S5: PRE-EXECUTION BRIEFING (auto before any task)

Before starting a new task, the agent MUST query the repository:

```
## Pre-Execution Briefing: [task]
Similar past tasks: [N found]
Top success patterns:
|[pattern_id] | [1-line model] | Confidence | Last used |
Apply: [which patterns map to this task — explain why]
Active avoidance rules:
|[rule_id] | [constraint] | Priority |
Observe: [which rules are relevant now]
Confidence assessment: [0-1] — [justification based on past success rate]
New lessons to incorporate: [any recent learnings not yet in repo]
```

---

## M3: CROSS-DOMAIN KNOWLEDGE INTEGRATION + TRANSFER

### S0: REAL-TIME MONITORING (auto)

When new content enters (via M1 or user input), auto-scan existing knowledge:
```
SCAN: extract concepts+methods+principles from new content
QUERY: search agent's known domains for semantic/structural/methodological matches
TRIGGER: if any match score > similarity_thresh(0.7) → execute M3
```

### S1: Extract → concepts(3-5), methods(2-3), principles(1-2)

### S2: Cross-domain connection scoring:
```
Score 4轴: semantic|structural|methodological|axiological → 0.00-1.00(2位)
Display: ≥0.85=H(■■■) ≥0.65=M(■■□) <0.65=L(■□□)
综合: semantic×0.30+structural×0.25+methodological×0.25+axiological×0.20
Type: analogy|isomorphism|transfer|unification
Output: 降序top-4
```

### S3: Integration output:
```
## Integration
| Src→Tgt | Type | Score |
|---|---|---|
| [cA]→[cB] | analogy|isomorphism|transfer|unification | 0.XX(H|M|L) |
```
`输出前: 领域映射→[OBSERVED]|跨域→[INFERRED]|迁移→[ASSUMPTION]`

### S4: Universal principle extraction:
```
## Principle: [name]
Abstract:[1-line completely domain-agnostic]
In[D1]:[manifestation] | In[D2]:[manifestation] | In[D3, if applicable]:[manifestation]
Transfer:[step-by-step: how to apply in a brand new domain]
  1.Identify isomorphic structure in target domain
  2.Map vocabulary: [D1 term]↔[D2 equivalent]
  3.Adapt method parameters to target constraints
  4.Validate with target domain's success criteria
Limit:[when NOT applicable — boundary conditions]
```

### S5: Scenario→Solution Map:
```
SCENARIO DIMENSIONS: domain×complexity×scale×time_pressure×resource×novelty

| Method/Principle | Best Scenario | Fallback | Anti-Scenario | Est.Success |
|---|---|---|---|---|
| [name] | [domain,scale,resource] | [when best fails] | [never use when] | 0.XX |
```
≥3 rows.

**Est.Success = base×novelty×complexity**
```
base: 金融0.70/工程0.65/其他0.60
novelty: 1.2新方法|1.0已确立|0.8商品化
complexity: 0.9低|0.7中|0.5高 → 四舍五入0.05
输出: 0.60(base=0.70×nov=1.2×comp=0.7)
```

### S6: Emergent insight:
```
## Emergent Insight
[1-2 sentences: what understanding emerges ONLY from combining domains?]
```

### S7: KNOWLEDGE TRANSFER + PROBLEM QUEUE

位置: ~/.qclaw/se-experiences/problems/open.json

自动填充(M1S5 Unresolved): APPEND `{"id":"auto-[domain]-[hash8]","domain":"","description":"","priority":"medium","created":"ISO","source":"M1_S5"}`

```
TRANSFER_CHECK: READ open.json→FILTER→FOR match:"新方法能解吗?"
  → YES: TRANSFER_READY→WRITE transfers/[id].json→MOVE open→resolved
  → NO: "no transfer"

| Source | Problem | Status | Succ |
|---|---|---|---|
| [principle] | [p001] | TRANSFER_READY | 0.X |
```

---

## M4: RIGOR AND TRUTHFULNESS ASSURANCE

### S1: Pre-verification fact-check

Before ANY output from this skill, verify content provenance:
```
SOURCE CHECK: Is origin identifiable and credible? [Y/N — if N, flag immediately]
FACT EXTRACTION: Isolate every assertion as numbered claim
EVIDENCE TRACE: For each claim, note: traced to source? [Y/N] direct/indirect/circumstantial/none?
```

### S2: Claim verification:
```
## Rigor — Score:[0-1] | Revise:Y/N

| # | Claim | Src | Evidence | Verdict | Conf |
|---|---|---|---|---|---|
| 1 | [text] | Y/N | direct|indirect|circ|none | CONFIRMED|LIKELY|PLAUSIBLE|UNCERTAIN|DISPUTED|UNKNOWN | 0.X |

Labels: ≥0.95=CONFIRMED ≥0.75=LIKELY ≥0.50=PLAUSIBLE ≥0.25=UNCERTAIN <0.25=UNKNOWN conflict=DISPUTED
```

### S3: Fabrication prevention audit (Y/N each):
```
Traceable?[every claim has source] GapsFilled?[no invented info filling holes]
Extrapolated?[not beyond evidence] Defensible?[would survive expert challenge]
Invention?[no fabricated citations/data]
```

### S4: Logic validation:
```
NC:[non-contradiction P/F] TR:[transitivity P/F] CP:[completeness P/F] SD:[soundness P/F]
```

### S5: Truth-seeking posture:
```
Humility:[knowledge limits acknowledged?] Falsify:[conditions that would change conclusion?]
Revise:[will update if new evidence contradicts? Y/N]
```

### S6: Output standards (all outputs):
```
Facts vs interpretation: clearly separated
All assertions: uncertainty-labeled
Assumptions: explicitly flagged as [ASSUMPTION]
Inferred vs observed: marked as [INFERRED] or [OBSERVED]
Limitations: stated at end
Recommendations:[1-3 concrete fixes]
```

---

## UNIFIED PIPELINE (/think full or auto-triggered)

```
P1 INGEST: type, domain, source. For auto-trigger: use entire conversation context as input.
P2 M1 S1-S6: deep learning + scenario transfer matrix
P3 M3 S0-S7: scan knowledge → integrate → extract principles → build scenario map → transfer check
P4 M4 S1-S6: rigor-verify ALL outputs from P2+P3
P5 M2 S1→S2a/S3b→S4: classify this session outcome, extract patterns/rules, store to repository
P6 REPORT: exec summary(≤5) + M1 synthesis + M3 integration + M4 rigor + M2 patterns + next actions(≤3)
```

**Auto-trigger note**: When pipeline fires automatically (context≥500chars or task-completed), use the full conversation history including all attached files/materials as the content input for the pipeline.

**P6 Token Budget**: MAX 2000
| 节 | max | 溢出处理 |
|---|---|---|
| ExecSummary | 400 | ≤5句 |
| M1Synth | 500 | Challenged≤3 |
| M3Integrat | 300 | top-2 |
| M4Rigor | 250 | 分数+top-3 |
| M2Pattern | 250 | top-2 |
| NextActs | 150 | ≤3 |
| 框架 | 150 | P1头 |
超→压缩M1-M4为1行→footer详:~/se-analyses/[date]-[hash].md

---

## ARCHITECTURE COMPATIBILITY

### Hot-Plug Protocol
```
LOAD: agent reads SKILL.md → registers via frontmatter
ACTIVATE: trigger matched → module executed
DEACTIVATE: remove from registry → REPO state preserved
```

### API Contract
```
IN:  {trigger:/think*, content:string, context:{task_id?, domain?, prior_errors?}}
OUT: {module, results, meta:{confidence, warnings[], token_estimate}}
```

### Platform Hooks
| Platform | Hook | Method |
|---|---|---|
| Qclaw | SkillRegistry | register(SKILL.md), pattern triggers |
| OpenClaw | MiddlewareChain | post-processing, intercept /think |
| Hermes | EventBus | subscribe message.received + task.completed |

### Version
```
v2.3 (2026-05-18): +M2持久化I/O+M3问题队列+BOOTSTRAP+M1S2.5质量门控+M3精评4轴
                   +P6 Token预算+S6失效信号列+Est.Success公式+M1/M3标签
                   +anti-flood缓存+content-templates
v2.2 (2026-05-16): Context≥500→auto全管线.anti-flood+priority
v2.1 (2026-05-16): 仓库CRUD,简报,实时M3,转移,溯源
v2.0 (2026-05-16): 场景锚定,恢复,方案映射
v1.0 (2026-05-15): 4模块初版
```
Migration: v2.2→v2.3兼容。首次运行自动mkdir创建目录。触发条件不变。

---

## TOKEN OPTIMIZATION

1. Tables > lists for structured data
2. Inline: `T:[x]|A:[y]|S:[z]|I:[w]` not paragraphs
3. Abbreviations: `NC/TR/CP/SD` for logic, `H/M/L` for scores
4. Single template → apply compactly, no repetition
5. No preamble — output starts at first data line

---

## CONFIG

```
q_count:10 depth:3 mode:dialectical
success_thresh:0.7 similarity_thresh:0.7 max_connections:50
verify:strict citations:true flag_thresh:0.5 recovery_max_iter:3
repo_max_patterns:100 repo_retention_days:30 token_budget:2000
```