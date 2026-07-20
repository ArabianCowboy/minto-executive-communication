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

### Repository and workspace discovery

This repository already contains the canonical skill at:

```text
.agents/skills/minto-executive-communication/
```

That path is the workspace discovery location for the Agent Skills standard,
Codex, OpenCode, and Google Antigravity. The `.claude/skills/` entry is one
symlinked mirror for Claude Code compatibility. Do not create another copy.

### User and global installation

- **Claude Code:** copy or symlink the skill directory to
  `.claude/skills/minto-executive-communication/` for one project, or to
  `~/.claude/skills/minto-executive-communication/` for personal use.
  Note for Windows: if the .claude/skills/ entry does not resolve as a link after cloning, either enable symlinks (git config core.symlinks true before checkout, with Developer Mode on) or simply copy the canonical folder from .agents/skills/minto-executive-communication/ into .claude/skills/.
- **claude.ai Projects:** paste the contents of `SKILL.md` into Project
  instructions, or upload it as Project knowledge and reference it in the
  instructions.
- **Codex manual:** use repository scope `.agents/skills/` or user scope
  `$HOME/.agents/skills/`.
- **Codex managed:** ask `$skill-installer` to install this repository skill.
  The installer selects its own `$CODEX_HOME/skills/` destination. Do not copy
  files manually into that managed directory.
- **OpenCode project:** use the existing canonical `.agents/skills/` directory.
- **OpenCode global:** use `~/.agents/skills/` or `~/.config/opencode/skills/`.
- **Antigravity workspace:** use the existing canonical `.agents/skills/`
  directory.
- **Antigravity global:** use `~/.gemini/config/skills/`.

Cowork filesystem discovery is not documented here. Its official documentation
describes account-enabled skills rather than a local discovery path.

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

## Validation

Run the independent protocol in [`tests/test-cases.md`](tests/test-cases.md).
The canonical skill is intentionally lean and has no scripts or generated
assets.

## Phase 1 verification log

- Agent Skills specification: https://agentskills.io/specification confirmed the required frontmatter, naming, relative references, and validation command.
- Codex skills: https://developers.openai.com/codex/build-skills confirmed `.agents/skills/`, `$HOME/.agents/skills/`, symlink support, managed-install distinction, and `agents/openai.yaml` fields.
- Codex installer: https://raw.githubusercontent.com/openai/skills/main/skills/.system/skill-installer/SKILL.md confirmed installation under `$CODEX_HOME/skills/`, normally `~/.codex/skills/`.
- Claude Code skills: https://code.claude.com/docs/en/skills confirmed project and personal `.claude/skills/` locations, supporting files, and symlink support.
- Claude Projects: https://support.claude.com/en/articles/9517075-what-are-projects confirmed Project instructions and uploaded Project knowledge.
- OpenCode skills: https://opencode.ai/docs/skills confirmed canonical `.agents/skills/`, global `~/.agents/skills/` and `~/.config/opencode/skills/`, and supported frontmatter.
- OpenCode implementation: https://raw.githubusercontent.com/anomalyco/opencode/dev/packages/opencode/src/tool/skill.ts confirmed relative resources are resolved from the skill base directory.
- Antigravity skills: https://antigravity.google/assets/docs/antigravity-2-0/skills.md confirmed workspace `.agents/skills/`, global `~/.gemini/config/skills/`, YAML frontmatter, and supporting resource folders.
- Source A: https://raw.githubusercontent.com/olelehmann1337/claude-skills/refs/heads/main/skills/minto/SKILL.md was studied for concepts only; its repository has no declared license.
- Source B: https://github.com/damianof/minto-skill was studied for README packaging patterns only; GitHub reports no repository license.
- Spec hygiene source: https://github.com/itzcull/thinking-skills and its MIT license were used for concept-level authoring guidance only.

Omitted: Cowork local paths, Antigravity legacy `.agent/skills/`, and redundant
provider mirrors because they were not needed or not verifiable for this build.

## Credits

Inspired by prior community Minto skills, notably work shared publicly by Ole Lehmann. This is an independent reimplementation.

## License

This original implementation is released under the MIT License. Copyright ©
2026 Mohammed I. Fouda.
