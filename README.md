# verify-polish-company — Claude Code plugin

A one-install Claude Code plugin that bundles:

- the **`verify-polish-company` Agent Skill**, and
- the hosted **skanfirmy.pl MCP server** (`https://skanfirmy.pl/mcp`),

so Claude can verify Polish companies straight from official government
registers — **no API key, no signup, no rate-limit registration.**

## What it does

- Look up a company by **NIP / KRS / REGON**.
- Check **VAT status** and registered **bank accounts** on the Ministry of
  Finance **White List** (Biała Lista).
- Validate an **EU VAT number** via **VIES**.

Everything runs on free, keyless public endpoints; the data comes straight from
the Ministry of Finance, the Ministry of Justice (KRS), Statistics Poland (GUS)
and the European Commission (VIES).

## Install

Once it is listed in the Anthropic community plugin marketplace:

```
/plugin
```

Then find **verify-polish-company** under Discover and install.

**Or add it directly from this repository** in Claude Code:

```
/plugin marketplace add bartosz-kuc/verify-polish-company
/plugin install verify-polish-company
```

The plugin auto-loads the skill (via `skills/`) and connects the MCP server
(via `.mcp.json`). You can then just ask, in plain language:

> is NIP 5260250995 an active VAT payer, and what is on its white list?

## Layout

```
verify-polish-company/
├── .claude-plugin/plugin.json      # plugin manifest
├── .mcp.json                       # hosted MCP server (skanfirmy.pl/mcp)
├── skills/
│   └── verify-polish-company/
│       └── SKILL.md                # the Agent Skill
├── README.md
└── LICENSE
```

## Related

- The API + MCP server this wraps: **[skanfirmy.pl](https://skanfirmy.pl)**
  ([MCP docs + the standalone skill](https://github.com/bartosz-kuc/skanfirmy-mcp)).
- Endpoint map for agents: <https://skanfirmy.pl/llms.txt>.

## Disclosure & license

skanfirmy.pl is the author's own independent project. It is free and keyless
and wraps official government registers, so the plugin has standalone value
with no paid tier. MIT licensed; data belongs to the respective public
registers.
