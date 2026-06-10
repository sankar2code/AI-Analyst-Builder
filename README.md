# AI Analyst v2

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code Required](https://img.shields.io/badge/requires-Claude%20Code-blueviolet.svg)](https://claude.ai/code)

**An AI-powered product analyst that turns business questions into validated insights, narratives, and slide decks in minutes.**

You ask a question. AI Analyst runs 18 specialized agents that explore your data, find root causes, build a story, and deliver a branded presentation with speaker notes. What would take a week takes a few minutes.

---

## What You Get

**Full Analysis Pipeline**
- Question framing & hypothesis generation
- Automated data exploration & validation
- Root cause analysis with drill-down investigation
- Time-series trends, cohort analysis, segmentation
- Confidence scoring on all findings

**Storytelling & Presentation**
- Context-Tension-Resolution narrative structure
- Storytelling with Data methodology charts (SWD-styled)
- Interactive HTML components & KPI cards
- Branded Marp slide decks with speaker notes
- PDF & HTML export

**Reliability Built In**
- 4-layer validation (structural, logical, business rules, paradox checks)
- Collision detection on all charts
- Quality gates between each phase
- Pipeline resumability if interrupted
- 606 passing tests with synthetic fixtures

---

## Get Started in 3 Steps

**1. Install Claude Code** (requires [Claude Pro](https://claude.ai/pro))

```bash
npm install -g @anthropic-ai/claude-code
```

**2. Clone and set up**

```bash
git clone https://github.com/ai-analyst-lab/ai-analyst.git
cd ai-analyst
pip install -e ".[dev]"
```

**3. Connect your data and ask a question**

```bash
claude
```

Then in Claude:

```
/connect-data
```

Or skip the wizard and jump straight in:

```
/run-pipeline data_path=data/your_dataset/ question="Why is conversion dropping?"
```

---

## Quick Examples

**Ask a quick question** (1-2 minutes)
```
What's our conversion rate by device?
```
Claude queries your data and returns an answer with a chart.

**Run a full analysis** (5-10 minutes)
```
/run-pipeline data_path=data/your_dataset/ question="What's driving the decline in conversion?"
```
Get a validated analysis, branded charts, narrative, and slide deck with speaker notes.

**Explore your data**
```
/explore
```
Interactive browsing without committing to a full analysis.

**Make a single chart**
```
Make a funnel chart of the checkout flow, highlighting the biggest drop-off step.
```
Generates a chart following Storytelling with Data standards.

---

## The Pipeline: How It Works

```
FRAME              ANALYZE                    STORY              DECK
├─ Frame question  ├─ Explore data           ├─ Design story     ├─ Write narrative
├─ Generate        ├─ Verify integrity       ├─ Generate charts  ├─ Build deck
│  hypotheses      ├─ Find root cause        ├─ Review visuals   ├─ Export PDF/HTML
└─ Checkpoint      ├─ Validate findings      └─ Checkpoint       └─ Done
                   └─ Size opportunity
```

**18 specialized agents** work across these phases. Independent agents run in parallel. Quality gates checkpoint your work before moving forward. You can run the full pipeline, or just the part you need:

- `full_presentation` — Complete analysis to slide deck (all 18 agents)
- `deep_dive` — Analysis only, no presentation layer
- `quick_chart` — Just make one chart
- `refresh_deck` — Re-do the presentation using existing analysis
- `validate_only` — Check existing work

---

## Your Data

**Bring your own.** No bundled datasets. Connect:

- CSV files
- DuckDB (local or MotherDuck)
- Postgres
- BigQuery
- Snowflake

The system auto-profiles your data, documents the schema, notes quirks, and remembers context across sessions.

---

## What's Actually Happening Under the Hood

- **DAG-based execution:** Agents resolve dependencies and run independently in parallel (up to 3 at once)
- **Self-learning:** Captures corrections and proven SQL patterns to avoid repeating mistakes
- **Schema-agnostic:** Agents resolve table names and metrics from your active dataset — not hardcoded
- **Validation layers:** Structural, logical, business rules, Simpson's Paradox checks
- **Theming:** YAML-based brand colors and chart styles (WCAG-compliant palettes)
- **Resumability:** Interrupted? Pick up where you left off without re-running completed work

---

## Customization

Everything is editable markdown and YAML. No black box.

| Want to... | Where |
|-----------|-------|
| Change how Claude thinks | Edit `CLAUDE.md` |
| Add a new skill | Create `.claude/skills/your-skill/skill.md` |
| Add a new agent | Use `agents/CONTRACT_TEMPLATE.md` as a starting point |
| Change slide theme | Create YAML theme in `themes/brands/` |
| Modify the pipeline | Edit `.claude/skills/run-pipeline/skill.md` |

---

## 20 Slash Commands

Quick reference — or just ask Claude in plain English:

```
/run-pipeline          Full analysis to slide deck
/resume-pipeline       Pick up where you left off
/explore               Interactive data exploration
/data                  Show active schema
/connect-data          Add a new data source
/setup                 Interactive onboarding
/export                Export as slides, email, Slack
/metrics               Browse metric dictionary
/history               View past analyses
/runs                  Manage pipeline runs
/compare-datasets      Compare metrics across datasets
... and 9 more
```

Don't memorize them. Ask Claude: *"What can I do with this data?"* It'll tell you the exact command.

---

## Requirements

- Python 3.10+
- Node.js 18+
- Claude Code (requires Claude Pro, $20/month)
- Internet connection

---

## Before You Start

**You are the expert.** This tool handles ~80% of what an analyst does. It catches data mistakes, validates findings, and builds decks. But you validate the output. If it picks the wrong column or misinterprets a metric, you'll catch it because you know the data. Correct it once, and it remembers.

**Don't skip validation.** Run this on data you know well. By the third analysis, you'll move faster than doing it by hand. By next week, you're running 15 analyses instead of 5.

---

## Learn More

- **Setup guide:** [docs/setup-guide.md](docs/setup-guide.md)
- **Theming & styling:** [docs/theming.md](docs/theming.md)
- **Issues & bugs:** [GitHub Issues](https://github.com/ai-analyst-lab/ai-analyst/issues)

---

## License

MIT — use it however you want.
