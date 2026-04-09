# gauge

A status bar for Claude Code that shows session usage, weekly limits, and context window consumption in real time.

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

Restart Claude Code. The status bar appears automatically on every interaction.

Requires Python 3.12+. On macOS: `brew install python@3.13`

## What it shows

**Line 1** — usage bars for the current 5-hour session, 7-day rolling window, and Sonnet model limit. Includes reset times and an off-peak indicator.

**Line 2** — context window bar showing tokens used and remaining in the current conversation.

## Configuration

```bash
# Themes
python3 ~/.gauge/claude_status.py --theme ember

# Bar style
python3 ~/.gauge/claude_status.py --bar-style dot

# Peak hours window (Anthropic 2x consumption period)
python3 ~/.gauge/claude_status.py --peak-hours 13:00-19:00

# Hide sections
python3 ~/.gauge/claude_status.py --hide cost
python3 ~/.gauge/claude_status.py --hide lines
```

Available themes: `default`, `ocean`, `sunset`, `ember`, `frost`, `candy`, `neon`, `pride`, `mono`, `rainbow`

## Requirements

Claude Code with a Pro or Max subscription. The status bar reads usage data from Claude Code's session API — no separate API key needed.

## License

MIT
