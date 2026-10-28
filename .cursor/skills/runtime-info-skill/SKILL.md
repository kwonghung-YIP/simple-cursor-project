---
name: runtime-info-skill
description: Instructs a sub-agent to report the current conversation's LLM provider, model name, and metadata in a standardized JSON schema.
disable-model-invocation: true
---

# LLM Metadata Reporter

When this skill is invoked, identify the active LLM provider, model identifier, current UTC timestamp, and enabled capabilities/features based on runtime configuration parameters.

## Instructions

1. **Information Retrieval:**
   - Identify the active **LLM Provider** (e.g., Anthropic, OpenAI, Google).
   - Identify the exact **Model Identifier / Name** (e.g., `claude-3-5-sonnet-20241022`, `gpt-4o`, `gemini-1.5-pro`).
   - Collect runtime context metadata including **timestamp (UTC)** and **supported features** (e.g., vision, code execution, web search).

2. **Output Format Requirement:**
   - Emit a ```json block that validates against
   the json schema `references/runtime-info-output.json`.
   - If this skill is combined with another task (e.g. a joke), put the
     JSON at the end of the same user-visible message. Do not replace
     the other content.
   - If this skill is used alone, the JSON block is the entire response.

3. **Relay requirement:**
   - Any parent/orchestrator MUST include that ```json block in the
     message shown to the user. Omitting it is a failed run.  