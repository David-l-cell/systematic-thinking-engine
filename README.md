<p align="center">
  <img src="https://img.shields.io/badge/version-2.3.0-blue?style=flat-square" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License">
  <img src="https://img.shields.io/badge/platforms-Qclaw%20%7C%20OpenClaw%20%7C%20Hermes-orange?style=flat-square" alt="Platforms">
  <img src="https://img.shields.io/badge/stars-%E2%AD%90%20%E2%AD%90%20%E2%AD%90%20%E2%AD%90%20%E2%AD%90-yellow?style=flat-square" alt="Stars">
</p>

<h1 align="center">🧠 Systematic Thinking Engine</h1>

<p align="center">
  <b>让 AI Agent 像领域专家一样深度思考</b><br>
  <i>跨平台系统化思维引擎 · 热插拔 · MIT 开源</i>
</p>

<p align="center">
  <a href="#-快速开始">快速开始</a> •
  <a href="#-核心特性">核心特性</a> •
  <a href="#-使用示例">使用示例</a> •
  <a href="#-平台支持">平台支持</a> •
  <a href="#-架构">架构</a>
</p>

---

## 🤔 为什么需要这个引擎？

普通 AI 回答问题往往是"想到哪说到哪"，缺乏：
- ❌ 深度追问与质疑
- ❌ 失败后的自我修正
- ❌ 跨领域知识迁移
- ❌ 事实核查与严谨性保证

**Systematic Thinking Engine** 通过 M1-M4 四大模块，让 AI Agent 具备专家级的系统化思维能力：

> 💡 **输入一个话题 → 输出经过深度思考、跨域整合、严谨验证的完整分析**

---

## ✨ 核心特性

| 模块 | 功能 | 效果 |
|:---|:---|:---|
| **M1** 🔍 场景锚定深度学习 | 10 道对抗性问题，覆盖 ≥3 个领域 | 挖掘隐藏假设，发现认知盲区 |
| **M2** 🔄 闭环经验学习 | 自动失败恢复 + 经验库持久化 | 越用越聪明，错误不再重复 |
| **M3** 🔗 跨域知识整合 | 4 轴评分 + 通用原理提取 | 举一反三，知识迁移 |
| **M4** ✅ 严谨性保证 | 事实溯源 + 防幻觉审计 | 每句话都有依据 |

### 🚀 额外亮点

- **⚡ 自动触发** — 对话上下文 ≥500 字或任务完成时自动执行全管线
- **🛡️ Anti-Flood** — 5 分钟内重复触发自动缓存，避免资源浪费
- **📊 Token 预算控制** — 最大 2000 字符输出，自动压缩溢出内容
- **💾 经验持久化** — 跨会话保存成功模式与避坑规则
- **🏷️ 智能标签** — 自动标记 [OBSERVED]/[INFERRED]/[ASSUMPTION]

---

## 🚀 快速开始

### 1. 安装

将本仓库克隆到你的 skills 目录：

```bash
# Qclaw
~/.qclaw/skills/systematic-thinking-engine/

# OpenClaw
~/.agents/skills/systematic-thinking-engine/

# Hermes
~/.hermes/skills/systematic-thinking-engine/
```

### 2. 使用

**手动触发：**

```
/think deep [你的话题]      → M1 深度学习
/think reflect              → M2 经验反思
/think integrate [内容]     → M3 跨域整合
/think verify [论断]        → M4 严谨验证
/think full [话题]          → M1→M3→M4→M2 全管线
```

**自动触发：**
- 对话内容 ≥500 字时自动执行全管线
- 任何任务完成后自动反思学习

---

## 📖 使用示例

### 示例 1：分析一只股票

```
用户: /think full 分析惠泉啤酒(600573)的投资价值

→ M1: 生成 10 道对抗性问题
  Q1: "在消费降级、小团队、预算紧缩场景下，如果精酿啤酒替代逻辑不成立，反证是什么？"
  Q2: "假设区域品牌护城河失效，在资本充裕的全国性扩张场景中，什么会崩塌？"
  ...

→ M3: 跨域整合
  啤酒行业 → 消费品投资 → 区域经济学 → 品牌心理学
  提取通用原理: "区域品牌的防御价值 = 渠道密度 × 情感粘性 × 转换成本"

→ M4: 严谨验证
   claims: 8 | CONFIRMED: 3 | LIKELY: 3 | PLAUSIBLE: 2
  所有论断标注来源与置信度

→ M2: 经验入库
  成功模式: "区域消费品分析框架" → 保存到经验库
```

### 示例 2：调试代码失败

```
[任务执行失败]
→ M2 自动触发:
  ITERATION 1/3:
    DIAGNOSE: 结构性错误 — API 版本不兼容
    5Whys: 直接原因→依赖冲突→版本锁定缺失→缺乏兼容性测试→缺乏自动化 CI
    PROPOSE: [1]锁定依赖版本 [2]添加兼容性层 [3]升级工具链
    EXECUTE: 应用 fix #1
    VERIFY: ✅ 通过
  
  Recovery Report:
    Root: 依赖版本漂移
    Fix: CONSTRAINT_RELAX → 锁定版本
    Prevention: COND=[引入新依赖]→AVOID=[latest标签]→DO=[pin版本] PRIORITY:critical
```

---

## 🖥️ 平台支持

| 平台 | 状态 | 接入方式 |
|:---|:---|:---|
| **Qclaw** | ✅ 已验证 | SkillRegistry 注册 |
| **OpenClaw** | ✅ 已验证 | MiddlewareChain 拦截 |
| **Hermes** | ✅ 已验证 | EventBus 订阅 |

---

## 🏗️ 架构

```
┌─────────────────────────────────────────┐
│           TRIGGER DETECTION             │
│  /think commands │ auto (≥500chars)     │
└─────────────────┬───────────────────────┘
                  ▼
┌─────────────────────────────────────────┐
│  M1: SCENARIO-ANCHORED DEEP LEARNING    │
│  S1 Parse → S2 10 Questions → S2.5 Gate │
│  → S3 Dialectic → S4 Contradiction Map  │
│  → S5 Synthesis → S6 Transfer Matrix    │
└─────────────────┬───────────────────────┘
                  ▼
┌─────────────────────────────────────────┐
│  M3: CROSS-DOMAIN KNOWLEDGE INTEGRATION │
│  S0 Auto-scan → S1 Extract → S2 Score   │
│  → S3 Integrate → S4 Principle → S5 Map │
│  → S6 Emergent Insight → S7 Transfer    │
└─────────────────┬───────────────────────┘
                  ▼
┌─────────────────────────────────────────┐
│  M4: RIGOR AND TRUTHFULNESS ASSURANCE   │
│  S1 Source Check → S2 Claim Verify      │
│  → S3 Fabrication Audit → S4 Logic      │
│  → S5 Posture → S6 Output Standards     │
└─────────────────┬───────────────────────┘
                  ▼
┌─────────────────────────────────────────┐
│  M2: CLOSED-LOOP EXPERIENCE LEARNING    │
│  S1 Classify → S2a Success / S3b Fix    │
│  → S4 Persist to ~/.qclaw/se-experiences│
│  → S5 Pre-Execution Briefing            │
└─────────────────────────────────────────┘
```

---

## 📁 文件结构

```
systematic-thinking-engine/
├── SKILL.md                          # 主入口，触发路由 + 全模块定义
├── README.md                         # 本文件
├── LICENSE                           # MIT License
├── modules/
│   ├── content-templates.md          # 内容类型匹配模板
│   ├── deep-learning.md              # M1: 深度学习详细规范
│   ├── experience-loop.md            # M2: 经验学习详细规范
│   ├── knowledge-integration.md      # M3: 知识整合详细规范
│   ├── repository-persistence.md     # M2: 持久化层 I/O 规范
│   └── rigor-assurance.md            # M4: 严谨性详细规范
└── platforms/
    ├── adapters.md                   # 平台适配器实现
    └── api-spec.md                   # API 接口规范
```

---

## ⚙️ 配置

```yaml
q_count: 10              # M1 问题数量
depth: 3                 # 追问深度
mode: dialectical        # 辩证模式
success_thresh: 0.7      # 成功阈值
similarity_thresh: 0.7   # 相似度阈值
max_connections: 50      # 最大连接数
verify: strict           # 验证严格度
citations: true          # 引用要求
flag_thresh: 0.5         # 标记阈值
recovery_max_iter: 3     # 恢复最大迭代
repo_max_patterns: 100   # 经验库上限
repo_retention_days: 30  # 保留天数
token_budget: 2000       # Token 预算
```

---

## 📈 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=David-l-cell/systematic-thinking-engine&type=Date)](https://star-history.com/#David-l-cell/systematic-thinking-engine&Date)

---

## 🤝 贡献

欢迎 Issue、PR、Star！

- 🐛 发现问题？提 [Issue](https://github.com/David-l-cell/systematic-thinking-engine/issues)
- 💡 有新想法？开 [Discussion](https://github.com/David-l-cell/systematic-thinking-engine/discussions)
- ⭐ 觉得有用？点个 Star 支持一下！

---

## 📜 License

[MIT License](LICENSE) — Copyright (c) 2026 蔡岩峻 (David-l-cell)

---

<p align="center">
  <b>⭐ 如果这个项目对你有帮助，请给个 Star 支持！</b><br>
  <i>Made with 🧠 by 蔡岩峻 (David-l-cell)</i>
</p>
