# Agent Ops Prompt Pack — Expanded

**50 production-tested prompt templates for AI agent operations, multi-agent orchestration, and autonomous workflows.**

## Categories (5 templates each)

| Category | Description |
|----------|-------------|
| **agent-delegation** | Role-scoped delegation, subagent spawning, delegation chains, capability matching, feedback loops |
| **task-decomposition** | Hierarchical breakdown, dependency graphs, vertical slicing, effort estimation, merge point planning |
| **quality-gates** | Pre-commit gates, schema validation, regression detection, security scanning, human-in-the-loop review |
| **error-recovery** | Retry with backoff, checkpoint/rollback, graceful degradation, circuit breakers, compensating transactions |
| **parallel-execution** | Fan-out/fan-in, work-stealing queues, pipeline parallelism, map-reduce, speculative execution |
| **context-management** | Sliding window, artifact grounding, context injection, memory indexing, context compression |
| **tool-selection** | Tool routing, composition chains, fallback chains, cost-aware selection, dynamic discovery |
| **output-validation** | Structural, semantic, adversarial, consensus, and regression validation |
| **handoff-protocols** | Agent-to-agent, human escalation, session transfer, error handoff, quality review handoff |
| **escalation-patterns** | Confidence-based, time-based, multi-signal, progressive autonomy, swarm escalation |

## Template Structure

Every template includes:
- **Prompt template** with `[VARIABLE]` placeholders
- **Variables** section documenting each placeholder
- **Example** with concrete values filled in
- **Tips** for effective usage

## Usage

1. Pick a template matching your agent pattern
2. Replace `[VARIABLES]` with your specifics
3. Adapt the example to your framework (CrewAI, AutoGen, LangChain, custom)
4. Combine templates for complex workflows (e.g., delegation → quality gate → handoff)

## Framework Compatibility

- **CrewAI**: Role/Goal/Backstory mapping for agent definitions
- **AutoGen**: AssistantAgent/UserProxyAgent task prompts
- **LangChain**: Agent executor and tool selection prompts
- **Custom**: Direct prompt injection for any LLM-based agent system
