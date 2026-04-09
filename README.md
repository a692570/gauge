# claude-pulse-reddit

A fork of [NoobyGains/claude-pulse](https://github.com/NoobyGains/claude-pulse) with three patches:

## What's different

### 1. Claude Code stdin format fix
The original script looked for `total_input_tokens` and `used_percentage` fields that Claude Code doesn't send. This fork reads `context_window.current_usage.input_tokens` (the actual format) and computes `context_pct` from token counts when `used_percentage` is absent. The context bar now reflects real usage.

### 2. `full` context format
A new `--context-format full` mode that shows used and remaining tokens explicitly:

```
Context ━━━━── 60% 40k • 40% 160k left
```

vs the default `Context ━━━━── 60%` or tokens mode `Context ━━━━── 40k/200k`.

### 3. Context on line 2
When using `full` format, context renders on a second line instead of inline. This prevents truncation on narrow terminals where the main usage line (session + weekly + sonnet) already fills the width.

```
Session ━━── 8% 12m | Weekly ━━── 5% R:Tue 9am | Sonnet ━━── 8% | Off-Peak ✓
Context ━━━━── 60% 40k • 40% 160k left
```

## Install

```bash
git clone https://github.com/a692570/claude-pulse-reddit ~/.claude-pulse
/opt/homebrew/opt/python@3.13/bin/python3.13 ~/.claude-pulse/claude_status.py --install
```

Then enable the full context format:

```bash
python3 ~/.claude-pulse/claude_status.py --context-format full
```

## Requirements

Python 3.12+ (uses f-string syntax unavailable in earlier versions). On macOS with Homebrew: `/opt/homebrew/opt/python@3.13/bin/python3.13`.

## License

MIT — same as upstream. See [NoobyGains/claude-pulse](https://github.com/NoobyGains/claude-pulse) for full license.
