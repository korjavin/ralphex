# agy-as-claude

Antigravity CLI wrapper for ralphex, allowing `agy` to replace Claude Code in task and review phases.

## Scripts

### agy-as-claude.sh

Wraps `agy` CLI to produce Claude-compatible stream-json output. Acts as a drop-in replacement for `claude` in task and review phases. Since Antigravity outputs plain text, this script wraps each line in a `content_block_delta` JSON event.

Additionally, to prevent deadlock/recursion loop issues when running the wrapper inside an active Antigravity agent process, the wrapper automatically unsets `ANTIGRAVITY_*` environment variables when invoking `agy`.

**Configuration** (`~/.config/ralphex/config` or `.ralphex/config`):

```ini
claude_command = /path/to/scripts/agy-as-claude/agy-as-claude.sh
claude_args =
```

## Testing

```bash
bash scripts/agy-as-claude/agy-as-claude_test.sh
```

## Requirements

- `agy` (Antigravity) CLI installed and accessible in the system PATH
- `jq` for JSON translation
