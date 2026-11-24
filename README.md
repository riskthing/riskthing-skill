# RiskThing skill

An agent skill for risk management. It teaches an AI agent to write risks and mitigations the way an experienced risk manager would, to score them against a defined scale, and, when connected to [RiskThing](https://riskthing.com), to keep a live risk register: capture risks as they come up during other work, onboard a new project by interview or from a document, and run check-ins that report what changed.

## What it does

**Without RiskThing**, the skill is a writing and scoring guide. Ask your agent to draft a risk statement, refine a mitigation, or score likelihood and consequence, and it follows the references in this folder. You keep the results wherever you keep your register.

**With RiskThing connected**, the agent also reads and writes your register through the RiskThing MCP server, under your own account and permissions:

- **Capture during work.** When a risk comes up (a vendor slips, a test shows thin margin, you say "I'm worried that…"), the agent offers to record it, checks for a duplicate first, and writes nothing without your yes.
- **Onboarding.** For a new project, the agent interviews you about the decisions ahead, or imports a plan or proposal, and builds a first register of risks with linked mitigations.
- **Check-ins.** The agent asks RiskThing what changed since the last check-in, reviews the top risks and the ones with no mitigation, and records the changes you confirm.

## Install

Send your agent this:

```text
Read https://github.com/riskthing/riskthing-skill and install the riskthing skill.
```

Your agent installs the skill, or tells you which step is yours.

**If you are an agent reading this:** find the section for your product below and install the skill. If a step needs the person, such as an upload, a setting or a trust prompt, tell them that one step. If you cannot install skills, read `SKILL.md` and the files under `references/`, and follow them for this conversation.

You need no RiskThing account and no MCP connection to install the skill, analyze a document, draft risks, or score likelihood and consequence.

The sections below hold the steps for each agent. The chat apps take one file, [`riskthing.zip`](https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip). The coding agents take this folder. Grok Bot and ChatGPT Work install it when you ask.

Use that download link, not GitHub's **Code > Download ZIP**. The skill's folder must be named `riskthing`, and GitHub's own zip names it `riskthing-skill-main`.

<details>
<summary><b>Claude</b> (web and desktop apps)</summary>

1. Download [`riskthing.zip`](https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip). Leave it zipped.
2. In Claude, open **Customize > Skills** ([claude.ai/customize/skills](https://claude.ai/customize/skills)).
3. Select **+**, then **Create skill**, then **Upload a skill**. Choose `riskthing.zip`.
4. Check that **riskthing** is in your skills list and is switched on.
5. Start a new chat, attach a plan or a proposal, and ask: "Use the riskthing skill to list the risks in this document, each with a likelihood, a consequence and a mitigation."

If Claude shows no place to upload a skill, turn on **Code execution and file creation** in your Claude settings. On a Team or Enterprise plan, an owner may have to allow skills first.

</details>

<details>
<summary><b>ChatGPT</b> (upload the zip)</summary>

1. Download [`riskthing.zip`](https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip). Leave it zipped.
2. Open ChatGPT in a browser at [chatgpt.com](https://chatgpt.com). In the sidebar, select **Plugins**, then the **Skills** tab.
3. Select **Create**, then **Upload from your computer**. Choose `riskthing.zip`.
4. Check that **riskthing** appears under **Installed**. ChatGPT checks an uploaded skill before it becomes available.
5. Start a new chat, attach a plan or a proposal, type `@` and choose **riskthing**. Then ask: "List the risks in this document, each with a likelihood, a consequence and a mitigation."

The skill works in both Chat and Work. Use Chat to draft or score a few risks. Use Work to review a set of documents or to build a whole register.

- **No Skills tab.** OpenAI offers personal skills on Business, Enterprise, Healthcare and Edu plans, and a workspace administrator can turn them off. See OpenAI's [Skills in ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).
- **No upload option in the desktop app.** Do step 3 in the browser. The skill is then available in the app.
- **You asked Chat to install the skill from GitHub.** Chat can read the repository, but it cannot add a skill to your account. Upload the zip, or use ChatGPT Work.

</details>

<details>
<summary><b>ChatGPT Work</b> (install by asking)</summary>

1. In ChatGPT, switch from **Chat** to **Work**.
2. Select the GitHub plugin, then send:

   ```text
   Install the riskthing skill from https://github.com/riskthing/riskthing-skill. Keep SKILL.md as written, and keep references/ and references/prompts/ beside it.
   ```

3. When Work confirms the install, open the skill link it returns, or find **riskthing** under **Plugins > Skills > Installed**. If the list has not refreshed, reopen the Skills page.
4. Start a new chat, attach a plan or a proposal, type `@` and choose **riskthing**. Then ask: "List the risks in this document, each with a likelihood, a consequence and a mitigation."

</details>

<details>
<summary><b>Grok</b> (the chat at grok.com)</summary>

1. Download [`riskthing.zip`](https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip). Leave it zipped.
2. Open **Skills** at [grok.com/skills](https://grok.com/skills).
3. Choose the option to upload or import a skill, and select `riskthing.zip`.
4. Check that **riskthing** is in your skills list.
5. Start a new chat, attach a plan or a proposal, and ask: "Use the riskthing skill to list the risks in this document, each with a likelihood, a consequence and a mitigation."

These steps do not install the skill for Grok Bot or Grok Build. Each has its own section below.

</details>

<details>
<summary><b>Grok Bot</b> (the cloud assistant)</summary>

Grok Bot has no upload for a skill. Your Bot installs it when you ask.

1. In a chat with your Bot, send:

   ```text
   Install the riskthing skill from https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip

   Save SKILL.md as a skill named riskthing. Keep its frontmatter and its body as written.
   Copy every file under references/ into the skill's folder. Keep the references/ and references/prompts/ layout.
   Then list the files you installed.
   ```

2. Read the Bot's list. It must name `SKILL.md` and the files under `references/`, such as `references/scales.md` and `references/writing.md`. A skill saved without them has no writing guidance and no scales.
3. Attach a plan or a proposal and ask: "Use the riskthing skill to list the risks in this document, each with a likelihood, a consequence and a mitigation."

The skill goes into the library that all your Bots share. If another of your Bots cannot find it, open **Connect apps** in the sidebar, select the connected count next to the title, and switch on **riskthing** under **Private skills**.

</details>

<details>
<summary><b>Claude Code</b></summary>

**Every project on this computer:**

```bash
git clone https://github.com/riskthing/riskthing-skill ~/.claude/skills/riskthing
```

To update, run `git pull` in that folder.

**One project only.** Run this in the top folder of the project's git repository:

```bash
curl -L -o riskthing.zip https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip
mkdir -p .claude/skills
unzip riskthing.zip -d .claude/skills/
```

These paths must then exist, with no second `riskthing/` folder inside the first:

```text
.claude/skills/riskthing/SKILL.md
.claude/skills/riskthing/references/
```

Keep `references/` beside `SKILL.md`. `SKILL.md` alone leaves out the writing guidance and the scales.

In a session in that project, ask: "Use the riskthing skill to review this document." If the skill does not appear, restart Claude Code.

</details>

<details>
<summary><b>Codex</b> (the coding agent)</summary>

**Every project on this computer:**

```bash
git clone https://github.com/riskthing/riskthing-skill ~/.agents/skills/riskthing
```

To update, run `git pull` in that folder.

**One project only.** Run this in the top folder of the project's git repository:

```bash
curl -L -o riskthing.zip https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip
mkdir -p .agents/skills
unzip riskthing.zip -d .agents/skills/
```

These paths must then exist, with no second `riskthing/` folder inside the first:

```text
.agents/skills/riskthing/SKILL.md
.agents/skills/riskthing/references/
```

Keep `references/` beside `SKILL.md`. `SKILL.md` alone leaves out the writing guidance and the scales.

In a session in that project, ask: "Use the riskthing skill to review this document." If the skill does not appear, restart Codex.

</details>

<details>
<summary><b>Grok Build</b> (the terminal coding agent)</summary>

**Every project on this computer:**

```bash
git clone https://github.com/riskthing/riskthing-skill ~/.grok/skills/riskthing
```

To update, run `git pull` in that folder.

Grok Build also reads `~/.claude/skills/`. If the skill is installed there for Claude Code, Grok Build already has it. Keep that copy current with `git pull`.

**One project only.** Run this in the top folder of the project's git repository:

```bash
curl -L -o riskthing.zip https://github.com/riskthing/riskthing-skill/releases/latest/download/riskthing.zip
mkdir -p .grok/skills
unzip riskthing.zip -d .grok/skills/
```

These paths must then exist, with no second `riskthing/` folder inside the first:

```text
.grok/skills/riskthing/SKILL.md
.grok/skills/riskthing/references/
```

Keep `references/` beside `SKILL.md`. `SKILL.md` alone leaves out the writing guidance and the scales.

In a session in that project, ask: "Use the riskthing skill to review this document." If the skill does not appear, run `grok inspect` to see which skills Grok Build found. Grok Build loads a project skill only after you trust the folder.

</details>

<details>
<summary><b>Any other agent</b></summary>

Copy this folder to where your agent loads `SKILL.md` skills. Name the folder `riskthing`, and keep `SKILL.md` at its top level.

</details>

## Optional: connect a live RiskThing risk register

Skip this section if you only want the skill to write and score risks. Connect RiskThing when you want the agent to keep them in a live register.

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

For Grok Build:

```bash
grok mcp add --transport http riskthing https://app.riskthing.com/mcp \
  --header "Authorization: Bearer <your token>"
```

For Grok Bot, ask your Bot in chat:

```text
Add a custom connector for the MCP server at https://app.riskthing.com/mcp. Send my API token as the header Authorization: Bearer <token>.
```

The Bot asks for your token and checks with you before it adds the connector. The connector then works for all your Bots.

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
