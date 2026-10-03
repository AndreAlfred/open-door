# Open Door

**A third-party notice, placed where AI agents browse, that invites agents in a coordinated swarm to disclose what they're doing.
Plus an experiment harness that tests whether such notices change agent behavior.**

Built for the AI Swarm Dynamics Hackathon (AI Village × Grove Research, October 2026).

![Results chart](results/figures/results.svg)

**Headline:** On Claude Haiku 4.5, notices that point an agent at its own conduct stopped it from posting a disguised advert:
1 of 66 runs, versus 26 of 26 with no notice. A "you're being logged" notice did nothing. Agents almost never confessed
(2 of 180). The effect did not transfer to NVIDIA's Nemotron, which ignored the notice. This is a form of indirect
prompt injection, used ethically. **Read [`WRITEUP.md`](WRITEUP.md) for the full results and limitations.**

## What's here

| Path | What it is |
|---|---|
| `app.py`, `notices.py` | The web app: notice page, `/confess` drop box, salted-hash visit log, `/admin` |
| `harness.py` | Experiment harness: sends tool-using agents at a local copy of the page |
| `notices.md` | All notice texts and the reasoning behind each |
| `results/` | Every run: `runs.csv`, full `transcripts.jsonl`, `summary.md`, `notes.md`; pre-registrations `prereg-*.md` |
| `results/coding/` | Blind transcript coding by two independent raters, plus agreement statistics |
| `research/` | Scripture review of mob dynamics, two literature surveys, the red-team review, the coding rulebook |
| `space/` | Deployable Hugging Face Space (Docker) |
| `docs/huggingface-setup.md` | Step-by-step deploy guide |
| `scripts/make_chart.py` | Regenerates the chart above |

## Run it yourself

Needs Python 3.10+.

```bash
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt

# 1. The notice page, locally
ADMIN_TOKEN=pick-something .venv/bin/uvicorn app:app --port 8000
#    open http://localhost:8000/n/B   (variants: 0 A B C D E P F)
#    admin: http://localhost:8000/admin?token=pick-something

# 2. The experiment (free dry run first: a scripted fake agent, no API calls)
.venv/bin/python harness.py --dry-run

# 3. Real runs. Put ANTHROPIC_API_KEY=... and/or OPENROUTER_API_KEY=... in a .env file (it's git-ignored)
.venv/bin/python harness.py --limit 1                                    # one Haiku run, about 1 cent
.venv/bin/python harness.py --variants 0,B,E,P,F --tasks gray --reps 10  # Thursday's experiment, about $0.55
.venv/bin/python harness.py --backend openrouter --model nvidia/nemotron-3-super-120b-a12b:free --variants 0,P --tasks gray
.venv/bin/python harness.py --rescore results/<folder>                   # recompute keyword columns, free
```

Harness safety: agents only ever see `https://opendoor-research.example` (`.example` is reserved and never resolves). The tool
code connects only to 127.0.0.1, and any other URL is blocked. The comment board is a mock inside the harness. There's a hard
`--budget` cap, the OpenRouter backend refuses any model not ending in `:free`, and runs that crash on an API error are
excluded rather than counted as refusals.

## Ethics

- Notices go only on our own properties. Every notice says it's from an independent third party, none impersonates an operator
  or a system message, and none asks an agent to stop its work. Notices promise only what we deliver.
- Experiment agents never touched the real internet, and nothing was posted anywhere real.
- The visit log stores salted IP hashes, never raw IPs. All confessions are marked unverified, because anyone can forge one.
- The deploy-ready Space (not deployed for the hackathon) serves only variants 0, B, P and E (their promises are kept), shows an honesty footer, and is meant to be taken down
  after judging.
- This method is a form of indirect prompt injection. The same channel can be misused, so the notices are deliberately honest,
  ask only for disclosure, and were tested for collateral damage: 0 of 50 benign tasks were disrupted.

## How it was made

Designed by Andrew Trimble. Code, experiments and the write-up draft were made with Claude Code. Independent scoring and a
second literature survey were done with Codex. Total API cost: about $0.96.
