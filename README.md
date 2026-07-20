# minto-executive-communication

`minto-executive-communication` drafts ready-to-send executive email, memos,
WhatsApp and Teams messages, and speaking points in Arabic or English. It puts
the answer first and applies Minto-style structure only as far as the message's
risk and weight require, from a six-line status note to a fully checked memo.

## How it differs from existing Minto skills

- Drafts the correspondence instead of returning an analysis artifact.
- Scales rigor to message weight rather than applying a full pyramid everywhere.
- Supports Arabic and English, with explicit Arabic register and honorific safeguards.
- Keeps visual HTML output opt-in.

## Install

### Skills CLI

Run from your target project directory using the third-party cross-agent
`skills` CLI. It requires Node.js 22.20 or newer. Select **Project** when
prompted to place the skill in the correct project scope.

```bash
npx skills add ArabianCowboy/minto-executive-communication
```

For a non-interactive project installation targeting selected agents:

```bash
npx skills add ArabianCowboy/minto-executive-communication \
  --skill minto-executive-communication \
  --agent claude-code \
  --agent codex \
  --agent opencode \
  --agent antigravity \
  --yes
```

From the project where it was installed, update an existing CLI-managed installation:

```bash
npx skills update minto-executive-communication
```

### Manual installation

Use manual installation when Node.js or `npx` is unavailable:

```bash
git clone https://github.com/ArabianCowboy/minto-executive-communication.git
cp -R \
  minto-executive-communication/.agents/skills/minto-executive-communication \
  /path/to/your/agent/skills/
```

Copy the complete skill folder, including `SKILL.md`, `references/`, and any
provider metadata. Use the destination documented by your agent.

### Claude.ai Projects

`npx` cannot install directly into a browser-based Claude.ai Project. Paste
the instructional content from `SKILL.md` into Project instructions and upload
`references/arabic-register-guide.md` as Project knowledge.

### Repository and workspace discovery

This repository contains the canonical skill at:

```text
.agents/skills/minto-executive-communication/
```

When this repository is the active workspace, Codex, OpenCode, and Google
Antigravity discover the skill at that path automatically, no extra setup
needed.

### User and global installation

For agents whose discovery path differs from the canonical one above:

- **Claude Code (project):** copy or symlink the canonical folder to
  `.claude/skills/minto-executive-communication/`.
  Note for Windows: if the `.claude/skills/` entry does not resolve as a link
  after cloning, either enable symlinks (`git config core.symlinks true` before
  checkout, with Developer Mode on) or simply copy the canonical folder into
  `.claude/skills/`.
- **Claude Code (personal):** copy or symlink to
  `~/.claude/skills/minto-executive-communication/`.
- **Codex manual (user scope):** use `$HOME/.agents/skills/`.
- **Codex managed:** ask `$skill-installer` to install this repository skill.
  The installer selects its own `$CODEX_HOME/skills/` destination. Do not copy
  files manually into that managed directory.
- **OpenCode (global):** use `~/.agents/skills/` or
  `~/.config/opencode/skills/`.
- **Antigravity (global):** use `~/.gemini/config/skills/`.

### Optional provider metadata

`.agents/skills/minto-executive-communication/agents/openai.yaml` is optional
Codex-specific metadata. It is not required by OpenCode, Antigravity, Claude
Code, or the Agent Skills standard. This file declares display metadata and
implicit invocation only; it has no tool dependencies.

## Usage

Use a direct request or a natural trigger:

```text
Draft an email to my VP asking for approval to start the checklist rollout by 1 July.
```

```text
رد على هذا الايميل بصياغة رسمية، وأجب عن سؤال الموعد في أول جملة.
```

By default, the response is the copyable message only. Ask `show the structure`
for the governing message, support, evidence status, and gaps. Ask for `HTML`
or `visual` only when a dark visual artifact is wanted.

## Credits

Inspired by prior community Minto skills, notably work shared publicly by Ole Lehmann. This is an independent reimplementation.

## License

This original implementation is released under the MIT License. Copyright ©
2026 Mohammed I. Fouda.