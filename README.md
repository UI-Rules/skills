# UI Rules skills

Agent skills for [UI Rules](https://uirules.com): they teach a coding agent to build interfaces and write copy that follow a brand's rules, from its identity and content to its components and design tokens, through the UI Rules MCP server.

| Skill | What it does |
| --- | --- |
| [`ui-rules`](skills/ui-rules/SKILL.md) | Builds UI with the brand's rules, design tokens and assets, checks the work against them, and changes them when asked. |

## Install

```bash
npx skills add ui-rules/skills
```

The skill uses the UI Rules MCP server. Connect your agent to it from **Connect** in the [UI Rules app](https://app.uirules.com).

## License

[Apache-2.0](LICENSE)
