# RiskThing skill

An agent skill for risk management. It teaches an AI agent to write risks and mitigations the way an experienced risk manager would, to score them against a defined scale, and, when connected to [RiskThing](https://riskthing.com), to keep a live risk register: capture risks as they come up during other work, onboard a new project by interview or from a document, and run check-ins that report what changed.

## What it does

**Without RiskThing**, the skill is a writing and scoring guide. Ask your agent to draft a risk statement, refine a mitigation, or score likelihood and consequence, and it follows the references in this folder. You keep the results wherever you keep your register.

**With RiskThing connected**, the agent also reads and writes your register through the RiskThing MCP server, under your own account and permissions:

- **Capture during work.** When a risk comes up (a vendor slips, a test shows thin margin, you say "I'm worried that…"), the agent offers to record it, checks for a duplicate first, and writes nothing without your yes.
- **Onboarding.** For a new project, the agent interviews you about the decisions ahead, or imports a plan or proposal, and builds a first register of risks with linked mitigations.
- **Check-ins.** The agent asks RiskThing what changed since the last check-in, reviews the top risks and the ones with no mitigation, and records the changes you confirm.

## Install

Copy this folder, with its `SKILL.md` at the top level, to where your agent loads skills. For Claude Code, that is `~/.claude/skills/riskthing/` for every project, or `.claude/skills/riskthing/` inside one project:

```bash
git clone https://github.com/interplanetarychris/riskthing-skill ~/.claude/skills/riskthing
``` Other agents that support `SKILL.md` skills load it from their own skills folder.

## Connect RiskThing

### Your organization's administrator, once

API and MCP access starts closed. In the RiskThing admin portal:

1. Open the access policy at <https://app.riskthing.com/admin_portal/policy/> (**Configure Access Policy** on the portal dashboard). Select **Edit policy**, then choose who can connect: **Selected members**, **Selected roles** or **All active members**. The default, **No one**, keeps the API and MCP closed. The policy decides who can connect; it does not change what they can do.
2. Optional: open **Configure AI Settings**. Turn on **Enable AI Text Refinement** for the in-app writing helpers. Fill in **AI Company Context** (up to 1,000 characters) with your dated objectives, capital, size band, regulatory posture and go-to-market. Your agent can draft it with you (`references/context.md`). Keep secrets, personal data and export-controlled material out of it.

The **API Tokens** page lists every token in the organization and lets an administrator revoke one. A revoked token's next request is denied.

### Each member, once

1. Open <https://app.riskthing.com/account/tokens/> (**API tokens**, in the settings menu of your account page) and create a token. Select its lifetime. Copy the secret: it is shown only once.
2. Give your MCP client the server address `https://app.riskthing.com/mcp` and the header `Authorization: Bearer <your token>`.

For Claude Code:

```bash
claude mcp add --transport http riskthing https://app.riskthing.com/mcp \
  --header "Authorization: Bearer <your token>"
```

For a client that reads a JSON configuration:

```json
{
  "mcpServers": {
    "riskthing": {
      "type": "http",
      "url": "https://app.riskthing.com/mcp",
      "headers": {
        "Authorization": "Bearer <your token>"
      }
    }
  }
}
```

The connection works when your client lists RiskThing tools such as `find_risks`.

### What the agent can and cannot do

The agent acts as you. It sees only what you can see and changes only what you can change. It has no access to organization settings, memberships, roles, billing or the access policy, and it cannot create tokens. Every operation it makes is audited, and every change waits in your **Agent activity** worklist for you to acknowledge.

## Choose a writing style

The skill writes in one of three styles. Tell your agent which one your organization uses, or let it default to RiskThing style.

| Style | A risk reads like | Fits |
|---|---|---|
| **RiskThing** | Our hardware vendor may miss the March 15 delivery date given its 40% on-time rate, pushing installation to April and forfeiting the $200K early-completion bonus. | Founders, boards, mixed teams, and anyone with no required standard |
| **NASA RMH** | Given that the reaction wheel vendor has a 40% on-time rate, there is a possibility of delivery delays affecting integration and test, which can result in a 3-month slip, adversely affecting the launch readiness milestone. | NASA work and NASA-reviewed programs |
| **DoD RIO** | If the titanium supplier cannot meet the 30-day delivery timeline due to raw material shortages, then production will drop from 2 units to 1 a month. | Defense programs, and primes that flow down DoD practice |

Titles follow the same rules in every style: the asset at stake, then what could happen to it.

The in-app writing helpers use one style per organization. To change your organization's in-app style, write to support@riskthing.com.

## Customize it

Everything in `references/` is a starting point. Edit it to match how your organization works.

| File | What it holds | Common changes |
|---|---|---|
| `references/scales.md` | The likelihood and consequence scales | Rescale the cost bands to your budget. Add an area your work cares about. |
| `references/writing.md` | The short form of every writing rule, and the style choice | Set your default style. Add your own failure patterns. |
| `references/prompts/` | The full guidance for each job: risk and mitigation titles, a risk statement and a mitigation in each style, and scoring | Replace the examples with your own programs. Add a style. |
| `references/context.md` | How to write the company and project context strings the AI reads | Change the interview questions. Add the facts your industry scores against. |
| `references/onboarding.md`, `check-in.md`, `tools.md` | How the agent works the register | Change the interview questions or the check-in agenda. |

If you change the scales, the in-app AI ranking still uses RiskThing's scales. Your agent's scores and the in-app scores then mean different things.

## Questions

Write to support@riskthing.com.

## License

Copyright 2026 Interplanetary Enterprises LLC. Licensed under the [Apache License, Version 2.0](LICENSE). The license grants no rights to the RiskThing name or marks.
