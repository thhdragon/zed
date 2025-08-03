# Zed AI & LLM Settings Reference

This document lists all settings related to AI, LLMs, chat, completion, and prompt handling in the Zed codebase. It includes both user-configurable and hardcoded settings, with notes on which should be made configurable.

---

## Table of Contents
- [User-Configurable Settings](#user-configurable-settings)
- [Hardcoded/Internal Settings](#hardcodedinternal-settings)
- [Recommended for Configuration](#recommended-for-configuration)

---

## User-Configurable Settings

### General
- **mode**: `system` | `dark` | `light` — Theme/mode selection (see `assets/settings/default.json`)
- **show_completions_on_input**: `true` | `false` — Show completions as you type
- **show_completion_documentation**: `true` | `false` — Show docs in completion menu
- **show_user_picture**: `true` | `false` — Show user avatar in UI
- **use_system_prompts**: `true` | `false` — Use system dialogs for prompts

### AI/LLM/Chat/Completion
- **model**: Model ID (e.g., `gpt-4.1`, `claude-3.7-sonnet`) — Selects LLM backend
- **temperature**: `float` — Sampling temperature for LLM completions
- **n**: `int` — Number of completions to generate
- **stream**: `true` | `false` — Enable streaming responses
- **tools**: List of enabled tool/function calls
- **tool_choice**: `auto` | `any` | `none` — Tool selection mode
- **max_context_window_tokens**: `int` — Max context window for LLM
- **max_output_tokens**: `int` — Max output tokens for LLM
- **max_prompt_tokens**: `int` — Max prompt tokens for LLM
- **vendor**: `openai` | `anthropic` | `google` | `bedrock` — LLM provider
- **enterprise_uri**: Custom Copilot/LLM endpoint

### Settings Storage
- `assets/settings/initial_user_settings.json`
- `assets/settings/default.json`
- `assets/settings/initial_server_settings.json`
- `assets/settings/initial_local_settings.json`

---

## Hardcoded/Internal Settings

- **DEFAULT_MODEL_ID**: `gpt-4.1` (in code, not user-configurable)
- **Copilot-Integration-Id**: `vscode-chat` (used in API headers)
- **Vision/Image support**: Enabled if message contains image parts (auto-detected)
- **Streaming**: Enabled by `stream: true` in request, but not always exposed in UI
- **OAuth token env var**: `GH_COPILOT_TOKEN` (env only)
- **API endpoints**: Derived from `enterprise_uri` or hardcoded for GitHub Copilot

---

## Recommended for Configuration

The following settings are hardcoded or only settable in code, but should be user-configurable for maximum flexibility:

- **DEFAULT_MODEL_ID**: Allow user to set the default model globally or per-project
- **Copilot-Integration-Id**: Allow override for custom integrations
- **Vision/Image support**: Expose as a toggle in settings
- **max_context_window_tokens**, **max_output_tokens**, **max_prompt_tokens**: Allow user override for advanced users
- **API endpoints**: Allow full override for all LLM providers, not just enterprise Copilot
- **Tool/function calling**: Expose tool enable/disable and tool_choice in UI
- **Persona/system prompt**: Allow user to set a custom system prompt/persona for chat and completions

---

## Notes
- Some settings are only available in JSON or TOML files and not exposed in the UI.
- Many LLM/AI settings are present in code but not surfaced to users; making these configurable would improve flexibility for power users and enterprise deployments.

---

## Example: Minimal AI/LLM Settings in JSON Format

```json
{
  "model": "gpt-4.1"
}
```

_By default, the system will use the maximum token limits and other parameters as defined by the selected model. Only override these if you need custom behavior._

_Last updated: 2025-07-31_
