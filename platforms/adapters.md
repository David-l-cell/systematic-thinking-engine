# Platform Adapters

Integration patterns for Qclaw, OpenClaw, Hermes. Common interface: each adapter initializes four modules + unified pipeline, registers platform-specific triggers, and formats output per platform conventions.

---

## Qclaw (Python - Skill Registration)

**Pattern**: Register as `QclawSkill` with trigger patterns + event listeners.

```python
class SystematicThinkingSkill(QclawSkill):
    def __init__(self):
        self.deep_learning = DeepLearningModule()
        self.experience_loop = ExperienceLoopModule()
        self.knowledge_integration = KnowledgeIntegrationModule()
        self.rigor_assurance = RigorAssuranceModule()
        self.pipeline = UnifiedPipeline([self.deep_learning, self.knowledge_integration, self.rigor_assurance, self.experience_loop])

    def register_triggers(self):
        return [
            SkillTrigger(pattern=r"/think\s+deep\s+(.+)", handler=self.handle_deep_learning),
            SkillTrigger(event="task.completed", handler=self.handle_task_completion),
            SkillTrigger(event="knowledge.updated", handler=self.handle_knowledge_update),
            SkillTrigger(pattern=r"/think\s+verify\s+(.+)", handler=self.handle_verification),
            SkillTrigger(pattern=r"/think\s+full\s+(.+)", handler=self.handle_full_pipeline),
            SkillTrigger(pattern=r"/think\s+reflect", handler=self.handle_reflect),
            SkillTrigger(pattern=r"/think\s+integrate\s+(.+)", handler=self.handle_integrate),
        ]

    async def handle_deep_learning(self, ctx):
        content = ctx.match.group(1)
        return await self.deep_learning.execute({
            'contentType': self._detect_type(content), 'content': content,
            'metadata': {'source': 'user_input', 'timestamp': ctx.timestamp},
            'platformContext': {'platform': 'qclaw', 'agentId': ctx.agent_id, ...}
        })
```

**Key methods**: `_detect_type(content)` → article if URL, document if >20 lines, else raw_text. `_format_response(result)` → {type, module, content, confidence, warnings, suggestions}.

Config in `qclaw_skills.yaml` → `skills.systematic-thinking-engine.config.{deep_learning, experience_loop, knowledge_integration, rigor_assurance}`.

---

## OpenClaw (TypeScript - Middleware)

**Pattern**: Implement `OpenClawMiddleware`, inject at `post-processing` phase.

```typescript
class SystematicThinkingMiddleware implements OpenClawMiddleware {
  name = 'systematic-thinking-engine'; phase = 'post-processing';

  constructor(config: MiddlewareConfig) {
    this.pipeline = new UnifiedPipeline([deepLearning, knowledgeIntegration, rigorAssurance, experienceLoop]);
  }

  async process(context: AgentContext, next: NextFunction) {
    // 1. Check for /think commands → handleCommand()
    // 2. Auto-trigger deep learning if content > 1000 chars + new topics
    // 3. Auto-trigger experience loop if task completed + autoExperienceLoop
    // 4. Rigor check on pendingResponse if rigorCheckResponses
    return next();
  }
}
```

**Command routing**: match `/think deep|full|verify|integrate|reflect` → execute appropriate module → inject result into context as system message.

**Storage**: success patterns + avoidance rules → `context.vectorStore.upsert()`.

Config in `middlewares.systematic-thinking-engine.config`.

---

## Hermes (Python - Event-Driven Plugin)

**Pattern**: Extend `HermesPlugin`, register event handlers + slash commands.

```python
class SystematicThinkingPlugin(HermesPlugin):
    async def on_plugin_load(self):
        self.register_event_handler("message.received", self.on_message, priority=NORMAL)
        self.register_event_handler("task.completed", self.on_task_complete, priority=HIGH)
        self.register_event_handler("knowledge.updated", self.on_knowledge_update, priority=NORMAL)
        self.register_event_handler("response.generated", self.on_response_check, priority=LOW)
        self.register_command("/think deep", self.cmd_deep_learning)
        # ... register other commands

    async def on_message_received(self, event):
        if len(content) > 500 and has_substantive_content(content) and not is_command:
            result = await self.deep_learning.execute({...})
            if config.inject_analysis: event.inject_context(result)

    async def on_task_completed(self, event):
        if config.auto_trigger:
            result = await self.experience_loop.execute({...})
            self.last_task_context = {'task_id': id, 'analysis': result}
```

**Substantive content detection**: ≥3 sentences after splitting on `. ! ?`.

Config in `hermes_plugins.yaml` → `plugins.systematic-thinking-engine`.

---

## Integration Checklist

- [ ] Module initialization with platform config
- [ ] All four module triggers registered
- [ ] PlatformContext constructed with correct capabilities
- [ ] Output formatted to platform's response system
- [ ] Experience stored to platform's persistence layer
- [ ] Rigor checks integrated into response pipeline
- [ ] Slash commands registered for user-facing triggers
- [ ] Error recovery strategy defined (retry/skip/degrade/abort)