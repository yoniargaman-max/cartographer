# Cartographer

**A skill that maps where your buyers actually pay attention.**
Give it a company and an ICP, and it returns a scored, tiered channel map of specific podcasts, newsletters, communities, creators, events, analysts, partners, publications, journalists, and AI answers, each with evidence and a first move.

## Who it's for

Marketers, founders, and GTM leads who need to know *which* rooms, shows, inboxes, and AI answers their buyers live in, not another list of channel categories. Useful for a launch, a new market, a new ICP, or a quarterly refresh of a stale channel list.

## What you get

- 12 lanes: Communities, Newsletters, Podcasts, LinkedIn / YouTube / X creators, Events, Publications, Journalists, Analysts & Awards & Review sites, Partnerships & Affiliates, and GEO (who wins the AI answers your buyers ask for).
- Every row is a real instance with a fetched URL, a confidence tag (verified / likely / unverified), and a score: **Fit x 2 + Reach + Access**, so a small room full of buyers beats a big audience of the wrong people.
- Room-rule awareness: each community's promotion tolerance is recorded so the map never sends you to pitch in a room that bans vendors.
- A Shortlist of the 12-18 plays for the next 90 days and "The Five Moves That Matter".
- Repeat runs dedupe against your previous map and report what's new, confirmed, changed, or dead.

## Install

**Claude (Claude.ai, Claude Desktop, or Claude Code):**
1. Download this repo (or the folder) as a zip, keeping `SKILL.md` and `references/` together.
2. In Claude.ai / Desktop: open Settings, find Skills (under Capabilities or Customize, depending on your version), and upload the zip. In Claude Code: copy the folder to `~/.claude/skills/cartographer/` (or `.claude/skills/cartographer/` in a project).
3. Ask for a channel map. The skill triggers on phrases like "map our channels" or "where do our buyers pay attention".

**Other agents:** any agent that reads `SKILL.md` files can use it. Drop the folder (SKILL.md plus `references/`) into the agent's skills directory, or paste `SKILL.md` into the system prompt and keep the reference files where the agent can read them.

**Works best with:** web search and page fetching (required for evidence), subagents for parallel lane research (optional), and a way to write .xlsx files (optional; it falls back to markdown tables).

**Optional, for repeat runs:** copy `references/company-context-template.md` to `references/company-context.md` and fill in your ICP, personas, and last map. Every run after that tags rows to your personas and dedupes against your previous map.

## Sample prompt

```
Map the channels for [Company], a [what it does] for [who it sells to] in [market].
Buyers are [titles] at [company size/stage]. Here's our ICP doc: [link or paste].
Deep run, all lanes. We already sponsor [channels you already work].
```

Quick version: `Quick map for [Company]: top 15 per lane, podcasts, newsletters, and communities only.`

## Example output

> **Example only.** The company, people, channels, URLs, and numbers below are fictional.

**Shiftwell** (a fictional scheduling tool for multi-location restaurant groups). The Five Moves That Matter:

1. Get customer-members talking inside the Multi-Unit Operators Circle (a strict-ban room: no pitching).
2. Pitch a guest episode to *Line Check* with original labor-cost data, not a product tour.
3. Submit a data talk to the Multi-Unit Ops Summit CFP before Nov 30.
4. Publish a "true cost of a no-show shift" benchmark built to be cited in AI answers.
5. Brief the trade reporter who has covered restaurant labor three times this quarter.

| Channel | Lane | Fit | Reach | Access | Score | Priority | Confidence |
|---|---|---|---|---|---|---|---|
| Multi-Unit Operators Circle | Communities | 5 | 3 | 3 | 16 | H | verified (active) |
| Line Check | Podcasts | 4 | 4 | 4 | 16 | H | verified |
| r/RestaurantOwnersHQ | Communities | 2 | 5 | 3 | 12 | M | verified |

See [`examples/sample-output.md`](examples/sample-output.md) for a fuller fictional run: README, Shortlist, one row per lane, lane insights, and the delivery note.

## Files

```
SKILL.md                                  the skill: modes, lanes, run protocol, rules
references/lane-playbooks.md              how to discover, verify, and enter each lane
references/output-spec.md                 workbook tabs, columns, scoring, formatting
references/company-context-template.md    optional context file for repeat runs
examples/sample-output.md                 fictional example run
```

## Credit

Created by **Yoni Argaman** ([LinkedIn](https://www.linkedin.com/in/yoniargaman/)). If it helps you, a mention or a tag is appreciated.

## License

MIT. See [LICENSE](LICENSE).
