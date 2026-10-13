# UI Rules skills

Agent skills for [UI Rules](https://uirules.com): they teach a coding agent to build interfaces that follow a brand's design system through the UI Rules MCP server.

| Skill | What it does |
| --- | --- |
| [`ui-rules`](skills/ui-rules/SKILL.md) | Reads the brand's rules and design tokens before building UI, and checks the work against them. |

## Install

```bash
npx skills add UI-Rules/skills
```

The skill uses the UI Rules MCP server. Connect your agent to it from **Connect** in the [UI Rules app](https://app.uirules.com).

## License

[Apache-2.0](LICENSE)
