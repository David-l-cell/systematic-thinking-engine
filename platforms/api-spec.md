# API Interface Specification v1.0.0

## Core Module Interface

All four modules implement:

```
ThinkingModule {
  name, version, moduleType: deep_learning|experience_loop|knowledge_integration|rigor_assurance
  execute(input: ModuleInput) → ModuleOutput
  initialize(config), shutdown(), getState(), restoreState(state), healthCheck()
}
```

## ModuleInput

```
{
  contentType: article|document|conversation|task_result|raw_text|code
  content: string
  metadata?: { source?, domain?, subdomain?, timestamp?, author?, tags[]? }
  options?: { questionCount?, synthesisMode?, successThreshold?, similarityThreshold?, verificationLevel? }
  platformContext?: PlatformContext
}
```

## ModuleOutput

```
{
  moduleName, moduleVersion, executionTimestamp, executionDurationMs
  results: DeepLearningResult | ExperienceLoopResult | KnowledgeIntegrationResult | RigorAssuranceResult
  confidence: 0-1
  warnings: [{code, message, severity}]
  suggestions: [{action, rationale, priority}]
}
```

## Result Types

**DeepLearningResult**: questions[{id, category, question, thesis, antithesis, synthesis, keyInsight, contradictionType, resolved}], contradictionMap{internal, external, paradigm, meta}, synthesis{pre, challenged[], resolved[], unresolved[], growthVector}

**ExperienceLoopResult**: outcome, outcomeConfidence, successPatterns[]?, failureAnalysis?, avoidanceRules[]?, improvementStrategies[]?, preExecutionBriefing?

**KnowledgeIntegrationResult**: newConnections[{src, target, type, score}], universalPrinciples[], transferBridges[], knowledgeMapUpdate

**RigorAssuranceResult**: overallQuality, sourceAssessment, claimVerifications[{claim, evidenceLevel, label, confidence}], logicReport{nonContradiction, transitivity, completeness, soundness}, fabricationRisks[], requiresRevision

## PlatformContext

```
{ platform: qclaw|openclaw|hermes, version, agentId, sessionId,
  capabilities: { persistentStorage, vectorSearch, eventSystem, middlewareChain, knowledgeBase } }
```

## REST Endpoints

```
POST /modules/{name}/execute        → ModuleOutput
POST /pipeline/execute              → { phaseResults, integratedReport }
GET  /modules/{name}/health         → HealthStatus
POST /experience/patterns           → { patternId }
POST /experience/rules              → { ruleId }
GET  /experience/briefing           → PreExecutionBriefing
POST /knowledge/integrate           → KnowledgeIntegrationResult
```

## Error Handling

```
ModuleError { code, message, module, timestamp, severity, recoverable }
ErrorResponse { handled, recoveryAction: retry|skip|degrade|abort, fallbackOutput? }
```