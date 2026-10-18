# Generic system-prompt install

For any LLM that takes a system prompt: GPT-4/5, Gemini, Llama, Mistral, local models via Ollama/LM Studio/vLLM, or any agent framework (LangChain, AutoGen, CrewAI, etc.).

## Install

Paste `system-prompt.md` into:

- ChatGPT custom GPT instructions
- Claude.ai project custom instructions
- OpenAI API `system` role
- Anthropic API `system` parameter
- Gemini API `systemInstruction`
- Ollama Modelfile `SYSTEM` directive
- LangChain `SystemMessage`
- Any agent framework's system-prompt field

## Verify

Type "is this a company or feature" with startup idea. Skill should transform.

## Caveat

Adherence to long system prompts varies by model:

1. Claude 3.5 Sonnet and above (highest)
2. GPT-4o / GPT-5
3. Gemini 1.5 Pro / 2.0
4. Llama 3.1 70B+
5. Smaller local models (often need explicit trigger phrases)
