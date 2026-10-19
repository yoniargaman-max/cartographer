---
name: cartographer
description: "Map every distribution channel for a company and its ICP (journalists, publications, podcasts, newsletters, communities, creators, events, analysts, partnerships, and GEO / AI-answer surfaces) into a scored, tiered channel map workbook. Use when the user says 'map our channels', 'where should we show up', 'where do our buyers pay attention', 'who covers our space', 'update the map', or 'find podcasts/newsletters/communities for X'."
---

# Cartographer

The job: given a company and who it sells to, produce a map of where those buyers actually pay attention: specific rooms, shows, inboxes, feeds, stages, and AI answers. Each entry carries enough evidence and enough of an entry plan that someone can start working the map the same week.

The premise: most "channel strategy" docs list categories ("do podcasts, engage communities"). A map lists *instances*: this show, hosted by this person, whose audience matches persona X, bookable via this route, at this cost, verified on this date. Categories are worthless; instances are a work queue.

## Is this the right skill?

- "Research [company] / its market" is a different job. That's who they ARE; this skill is where their buyers LISTEN.
- "Who is our ICP / build personas" comes first. This skill consumes an ICP, it doesn't invent one. If there is no ICP, do the compact synthesis in Phase 1 and get a yes/no before mapping.
- "How should we split budget across channels" (funnel math, allocation) is strategy. A finished map is a great input to it, but this skill discovers and maps; it does not allocate.
- "Where do buyers pay attention / map the channels / find the podcasts, journalists, communities" is this skill.

Honesty discipline applies throughout: every fact is tagged verified / likely / unverified, no fabricated URLs, no invented audience numbers.

## Inputs and the optional context file

Every run needs a company name plus an ICP source: an attached or linked ICP doc (read it fully), a context file (below), or enough conversation context to synthesize a working ICP.

**Saved context file (recommended for repeat runs).** If `references/company-context.md` exists, read it before anything else. Use `references/company-context-template.md` to create one. It holds the compressed ICP, named personas, fit signals and compelling events, anti-ICP, positioning language, default scope, and the inventory of the previous map. With a context file present:

- Tag every row to the personas named in the file.
- Check every discovered entity against the previous-map inventory and fill the `In prev?` column. The value of a repeat run is the NEW territory plus re-verification of the old.
- At intake, ask once whether to activate any lanes or personas the file lists as parked.

**No context file.** Extract from whatever ICP source you have: buyer personas (title, seniority, day-to-day), verticals, geography, company stage and size, the pain the product kills, and any anti-ICP. If no ICP exists, do a compact ICP synthesis first (company website, positioning, obvious buyer titles, 2-3 verticals) and show it to the user for a yes/no before mapping. Mapping against a wrong ICP wastes the entire run. These inputs drive every lane's search queries.

## Depth settings

Ask at intake (or infer from phrasing):

- **Curated** (~15 entries per lane): first-cut shortlist, cheapest run. "Quick map", "shortlist".
- **Deep** (~30-50 entries per lane, tiered): the default. Tier A = top ~10 per lane, fully enriched with entry plays and verification. Tier B = the rest, scored with core data, lighter verification.
- **Exhaustive**: everything findable, tiered the same way. Warn the user before running: this is a very large research job (likely well over a million tokens across subagents). Suggest running it lane by lane across sessions instead.

A deep run across all lanes is itself a substantial job. If the user seems budget-conscious, offer to run the 4-5 highest-value lanes first and the rest in a follow-up session. Better half a map that's verified than a full map that's guessed.

## The lanes

Twelve discovery lanes, each with its own tab, plus README / Shortlist / Parked. Per-lane discovery queries, enrichment fields, verification rules, and entry-play patterns live in `references/lane-playbooks.md`; read it before dispatching lane research. Exact tab layouts and column definitions live in `references/output-spec.md`; read it before building the workbook.

1. **Journalists**: named individual reporters and editors: beat, outlet, evidence they cover this space (linked recent pieces), pitch angle, public contact route.
2. **Publications**: outlets and trade press as entities: earned vs. contributed routes, story angles per beat.
3. **Podcasts**: shows: host, audience signal, guest vs. sponsor play, pitch angle, landing difficulty.
4. **Newsletters**: author/publisher, subscriber evidence, sponsorship route and rate where public, non-paid entry plays.
5. **Communities**: Slack, Discord, Reddit, paid memberships, forums: size, promotion tolerance (open / gray / strict-ban), an entry play that respects the room's rules.
6. **Creators: LinkedIn**: operators with ICP-matched audiences: collab angle, alignment risk, cost signal.
7. **Creators: YouTube**: channels: format (interview / tutorial / essay), audience evidence, integration vs. dedicated vs. guest play.
8. **Creators: X**: accounts: what they engage with, reply vs. paid vs. earned-mention plays.
9. **Events**: conferences, dinners, meetups: next date, audience composition, sold-stage vs. earned-stage vs. hallway play.
10. **Analysts, Awards & Review sites**: analyst firms and named analysts covering the category, industry awards with deadlines, review platforms and the specific category pages that matter.
11. **Partnerships & Affiliates**: marketplaces, integration ecosystems, VC platform networks, agencies and consultants who refer, affiliate and newsletter rev-share programs.
12. **GEO**: the buyer queries that matter, who wins each AI answer today (actually run the queries where possible), and what would change the answer.

Anything discovered that's real but out of scope for this run goes to **Parked** with a one-line "the play when activated". Never drop it silently.

## The run protocol

**Phase 0: Intake.** Company, ICP source, depth, scope (geography, personas in/out, lanes in/out), and any channels the user already works (mark them, don't re-pitch them). Batch these into one question set. In unattended runs, state assumptions at the top and proceed with defaults (Deep, all lanes, the company's primary market).

**Phase 1: Context load.** Read `references/company-context.md` if it exists; otherwise ingest or synthesize the ICP as described above. Always read `references/lane-playbooks.md`. Distill a one-paragraph "search brief" per persona: the titles, watering-hole types, and vocabulary that lane researchers will search with.

**Phase 2: Lane discovery.** If your environment supports subagents, dispatch them in parallel, one per lane (batch 3-5 at a time if the environment strains). Otherwise work the lanes sequentially. Each lane researcher gets: the search brief, its lane playbook section, the depth target, and the row schema from `references/output-spec.md`. Each returns structured rows (JSON or a markdown table), every row carrying a URL it actually fetched and a confidence tag. Lanes cross-pollinate: a podcast host is often also a newsletter author and a LinkedIn creator. Note cross-lane appearances rather than researching them twice (the "one ecosystem, four lanes" pattern).

**Phase 3: Verification.** For every Tier A row: fetch the URL, confirm the entity is alive (published or posted within ~90 days; next event date real; podcast still shipping episodes), and check the audience claim against a source. Downgrade or park anything that fails. Dead channel lists are the disease this map exists to cure; don't reproduce it. Tag every row `verified` (checked this run, date noted), `likely` (strong indirect evidence), or `unverified` (found but unchecked, Tier B only). Split tags per fact when needed ("verified (active) / likely (rate)").

**Phase 4: Score and dedupe.** Merge lanes and dedupe cross-lane entities (one canonical row per lane it's actionable in, cross-referenced in Notes). If there is a previous-map inventory, check every row against it and fill `In prev?`. Score every row 1-5 on **Fit** (ICP concentration: what share of this audience is the buyer), **Reach** (audience size on a log scale), **Access** (ease and cheapness of entry). Score = Fit x 2 + Reach + Access. Priority: H (15 or more) / M (11-14) / L (10 or less). Fit is double-weighted on purpose: a 400-person room that is 100% ICP beats a 100K-follower account that is 5% ICP, and the math should say so. Override the formula with judgment where it's clearly wrong, and say why in Notes.

**Phase 5: Synthesis.** Write 3-4 LANE INSIGHTS per lane: patterns, traps, sequencing ("guest beats sponsor economics at this stage", "community size is inversely correlated with value"). Then build the **Shortlist**: the 12-18 cross-lane plays that matter most in the next 90 days, each with a first action, cost estimate, and timing. Close with "THE FIVE MOVES THAT MATTER" on the README: if the user does nothing else, these five.

**Phase 6: Build and deliver.** Build the workbook exactly per `references/output-spec.md`. Prefer a real .xlsx (use a spreadsheet skill if one is installed, or a library such as openpyxl). If you cannot produce files, deliver one markdown table per tab in the same order and columns. Deliver with a 3-5 sentence summary: entity count, verified share, the single most surprising find, and the recommended first move. On repeat runs, also note what changed vs. the previous map (new / confirmed / now-dead).

## What "great" looks like

- **Instance-level.** "Pitch [named reporter], who covered [linked competitor story] in March", never "pitch [big outlet]".
- **Evidence-carrying.** Every row has a URL that was actually fetched. Every audience number has a source or an "est./unverified" flag. Every event has a real next date.
- **Entry-planned.** Tier A rows answer "what do I do Monday morning": a named play, not "engage authentically".
- **Room-rule aware.** Promotion tolerance is recorded and the entry play respects it. Recommending a pitch in a strict-ban community burns the user's reputation; the map must protect them from that.
- **Honest about cost.** Sponsorship rates only where publicly listed or credibly reported (tagged accordingly); otherwise "$/$$/$$$, rate unknown" beats an invented number.
- **Sequenced.** The Shortlist and lane insights say what to do first and why, not just what exists.
- **Dedupe-aware (repeat runs).** New rows are the headline; previous rows are re-verified, not re-discovered.

## Anti-patterns: refuse to

- Invent or guess email addresses, DM handles, audience sizes, sponsorship rates, or event dates. A publicly listed contact route or nothing.
- Include a row without a fetched URL. No "probably has a podcast".
- Pad lanes to hit depth targets with barely relevant entries. 28 real rows beat 50 where 22 are filler. Say plainly when a lane is thin and why.
- Recycle a category listicle ("Top 50 marketing podcasts") as discovery without checking each entry against THIS ICP. Listicles are leads, never conclusions.
- Present the map as strategy. It's a where-map with a starting sequence; budget allocation and funnel math are a separate job.
- Leave working columns dead. Status defaults to "Not started", but Owner suggestions and Notes should be filled wherever there's something real to say.

## Updating the map

"Update the map" means: re-verify all previous Tier A rows (alive? dates moved? rates changed?), hunt what's new since the last build date, and produce a delta summary (new / confirmed / changed / dead) alongside the refreshed workbook. Channel maps rot fast; stale lists rot faster. A map older than a quarter is a rumor.

After any run, offer to write or refresh the previous-map inventory in `references/company-context.md` with the new map's entities (show the diff and confirm with the user first), so the next run dedupes against the latest map.

## Reference files

| File | What it holds | Read when |
|---|---|---|
| `references/company-context.md` (optional, you create it) | Compressed ICP, personas, positioning, previous-map inventory, scope defaults | Always first, if it exists |
| `references/company-context-template.md` | Blank template for the context file | When setting up repeat runs |
| `references/lane-playbooks.md` | Per-lane discovery queries, enrichment fields, verification rules, entry-play patterns | Before Phase 2 |
| `references/output-spec.md` | Workbook structure: tabs, exact columns, scoring, formatting conventions | Before Phase 4 and Phase 6 |
