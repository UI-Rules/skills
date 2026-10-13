---
name: ui-rules
description: Builds interfaces that follow a brand's UI Rules design system through the `uirules` MCP server. Use when building or styling UI, writing interface copy, or setting up design tokens in a project connected to UI Rules, and when the `uirules` tools are missing or not signed in.
license: Apache-2.0
---

# UI Rules

UI Rules serves a brand's design system (its rules, design tokens and assets) through the `uirules` MCP server. The brand's rules and tokens come first; your own defaults fill only what they leave open.

## Building UI or copy

An organization holds brands and a brand holds projects; a project inherits its brand's rules and tokens. When the connection fixes a level, the tools stop asking for it. Otherwise find the slugs with `list_organizations`, `list_brands` and `list_projects`, and ask the user when more than one fits. Verification works on a project: when only the brand is fixed, pick the project before step 3.

1. Read the brand with `get_brand_brief`, then the map of what has rules with `get_rules_index`. Done when you have named, in the index's exact spelling, every node the work touches.
2. Fetch each of those nodes with `get_rules` and apply its rules. Copy and accessibility areas cover everything you write. Done when every node you touch has its rules in context.
3. Fetch the tokens with `get_design_tokens` in the project's dialect (`css`, `tailwind-v4` or `tailwind-v3`, as `package.json` shows) and write what it serves as it comes: the stylesheet, and for `tailwind-v3` the config too. Done when `verify_stylesheet`, given both, reports it clean.
4. Build, styling through the token names. A value the tokens lack is a gap to tell the user about, not a literal to write.
5. Check the finished work with `verify_rule_compliance`, declaring each rule you departed from and why. Done when it returns its verdict and you have told the user every departure and anything it left unchecked.

## When the tools are missing or not signed in

Tools that are listed but fail every call with an authorization error are a sign-in problem: go to step 3.

1. Check that the server answers: `curl -s -o /dev/null -w "%{http_code}" https://mcp.uirules.com/mcp`. Any three-digit status means it is up; `000` means it is not.
2. Check the agent's MCP configuration for a `uirules` server whose URL starts with `https://mcp.uirules.com/mcp`. Its query narrows the connection and can hide tools: `read_only=true` leaves only reads, and `features` only those groups. If there is no such server, send the user to **Connect** in the UI Rules app (https://app.uirules.com): it gives the setup for their tool and the URL for their organization, brand or project.
3. Have the user sign in through the agent's MCP authentication, which opens UI Rules in the browser, then reload the session.

Done when the `uirules` tools are listed and `list_organizations` answers.
