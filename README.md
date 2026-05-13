# skill-ask-ami

Knowledge wrapper that helps an LLM agent explore and understand the AMI (Analysis Monitoring Interface) codebase — LCLS-II's online graphical analysis monitoring package. The skill points the agent at curated documentation (`.agent_docs/`), a SQLite code index (`.code-index.db`), and Sphinx design docs that all live alongside the AMI source at `/sdf/group/lcls/ds/dm/apps/dev/software/ami/` on SLAC's S3DF — this repo only contains the agent-facing SKILL.md that tells the agent how to use them.

## Layout

```
claude/skills/ask-ami/SKILL.md      # for Claude Code users
opencode/skills/ask-ami/SKILL.md    # for opencode users (identical content)
```

Deployment of the `opencode/` side to the shared LCLS install is handled by the [deploy-opencode](https://github.com/carbonscott/deploy-opencode) meta-deploy script. Claude Code users can symlink the `claude/skills/ask-ami/` directory into their `~/.claude/skills/` to use it locally.

## Data dependency

This skill assumes the AMI repo plus its `.agent_docs/` and `.code-index.db` exist at `/sdf/group/lcls/ds/dm/apps/dev/software/ami/`. The skill itself does not ship or sync that content — it's maintained out-of-band by the deploy-opencode maintainer via `software/update-index.sh` and direct repo updates.
