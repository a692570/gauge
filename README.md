# gauge

Claude Code status bar with context window visibility. Fork of [NoobyGains/claude-pulse](https://github.com/NoobyGains/claude-pulse).

## What's different

### 1. Claude Code stdin format fix
The original script looked for `total_input_tokens` and `used_percentage` fields that Claude Code doesn't actually send. Gauge reads `context_window.current_usage.input_tokens` (the real format) and computes context percentage from token counts. The context bar now reflects actual usage.

### 2. `full` context format
A new `--context-format full` mode showing used and remaining tokens explicitly:

```
Context ━━━━── 60% 40k • 40% 160k left
```

vs the default `60%` or tokens mode `40k/200k`.

### 3. Context on line 2
In `full` format, context renders on a second line instead of inline. This prevents truncation on narrow terminals where session + weekly + model bars already fill the width.

```
Session ━━── 8% 12m | Weekly ━━── 5% R:Tue 9am | Sonnet ━━── 8% | Off-Peak ✓
Context ━━━━── 60% 40k • 40% 160k left
```

## Install

```bash
git clone https://github.com/a692570/gauge ~/.gauge
python3 ~/.gauge/claude_status.py --install
python3 ~/.gauge/claude_status.py --context-format full
```

Requires Python 3.12+. On macOS: `brew install python@3.13`

## License

MIT — same as upstream. See [NoobyGains/claude-pulse](https://github.com/NoobyGains/claude-pulse).
