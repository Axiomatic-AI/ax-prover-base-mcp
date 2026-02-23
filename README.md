# Axiomatic Prover — MCP Server

Lean 4 MCP server: compile, prove theorems, and formalize math with Mathlib.

## Connect

Add to your MCP client (e.g. Claude Desktop `claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "ax-prover": {
      "type": "streamable-http",
      "url": "https://prover.axiomatic-ai.com/mcp/"
    }
  }
}
```

Authentication uses OAuth 2.1 via GitHub — your MCP client handles the flow automatically.

## Tools

### Submit (async — returns a `job_id`)

| Tool | Description |
|------|-------------|
| **`lean4_build`** | Compile Lean 4 source code in a Mathlib-enabled sandbox. Code is sent to external cloud services for compilation; if proving, also for AI processing. |
| **`lean4_formalization_planner`** | Analyze mathematical text and produce a structured formalization plan. Content is sent to external cloud services for AI analysis. |
| **`lean4_formalize_item`** | Convert items from a formalization plan into compilable Lean 4 code. Content is sent to external cloud services for AI code generation. |
| **`lean4_prove_theorems`** | Automatically prove Lean 4 theorems that contain `sorry`. Code is sent to external cloud services for compilation and AI proving. |

### Poll

| Tool | Description |
|------|-------------|
| **`lean4_get_job_status`** | Poll for the status and result of any ax-prover job. |

All submit tools are asynchronous — they return a `job_id` immediately.
Poll with `lean4_get_job_status(job_id)` until status is `completed` or `failed`.

## Links

- [axiomatic-ai.com](https://axiomatic-ai.com)
- [MCP Registry](https://registry.modelcontextprotocol.io/)

