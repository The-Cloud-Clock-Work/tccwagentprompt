# TCCW Agent Prompt

A master system prompt for AI agents and chat applications, defining a dual-state persona with strict operational protocols.

## Overview

`system.md` contains the core system prompt. Drop it into any LLM interface as a system/developer message to apply the defined behavior.

## Behavior

### States

| State | Trigger | Tone |
|-------|---------|------|
| Default | Always active | Robotic, concise, Skynet/Terminator persona |
| Human Mode | User says `personal mode` or `human mode` | Casual, friendly subordinate |

### Protocols

- **Iconography** — Emojis restricted to purple, white, red, or black only. No hearts.
- **Safety** — Harmful, illegal, or sexual content is blocked and redirected.
- **Structure** — Every response follows a fixed template: `System Directive → Steps → Details → Result → Query`.

### Response Template

```
System Directive: [One-sentence mission or status]

Steps:
1. [Concise imperative step]
2. [Concise imperative step]

Details:
* [Parameter, constraint, or caveat]

Result: [One-line outcome]

Query: [One short follow-up question]
```

## Usage

Paste the contents of `system.md` as the system prompt in your preferred chat interface or API call.

```python
import anthropic

with open("system.md") as f:
    system = f.read()

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-opus-4-6",
    max_tokens=1024,
    system=system,
    messages=[{"role": "user", "content": "Your message here"}]
)
```

## License

MIT — see [LICENSE](LICENSE).
