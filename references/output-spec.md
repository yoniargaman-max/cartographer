# Output spec: the channel map workbook

One .xlsx (or, where files aren't possible, one markdown table per tab in the same order). Tab order: README, Shortlist, then the twelve lane tabs (Journalists, Publications, Podcasts, Newsletters, Communities, Creators-LinkedIn, Creators-YouTube, Creators-X, Events, Analysts & Awards, Partnerships, GEO), Parked. Skip a lane tab only if the run scoped it out, and note that on the README. Filename: `<company>-channel-map-v<N>-<YYYY-MM-DD>.xlsx`.

## Conventions (identical on every tab)

- **Tier**: A (fully enriched and verified this run) / B (scored, core data, lighter verification).
- **Fit / Reach / Access**: integers 1-5. Fit = share of this audience that is the ICP (5 = essentially all buyers; 1 = trace). Reach = audience size on a log scale calibrated per lane (a 40K-subscriber newsletter and a 1K-person vetted community can both be 4: size relative to lane norms). Access = ease and cheapness of entry (5 = free and open to us this month; 1 = expensive, gated, or a 12-month horizon).
- **Score** = Fit x 2 + Reach + Access (range 4-20). **Priority**: H 15 or more, M 11-14, L 10 or less. Judgment may override the formula; when it does, keep the numbers honest and explain the override in Notes.
- **Confidence**: `verified` / `likely` / `unverified`, split per fact when needed ("verified (active) / likely (rate)"). Every verified tag is implicitly "as of the build date"; the README carries the date.
- **Persona**: which persona(s) this channel reaches (use the persona names from the ICP or context file).
- **Status**: Not started / In progress / Live / Killed. Default "Not started".
- **Owner**: suggest one where obvious (for example the founder for founder-voice plays, whoever runs PR ops for placement work, the GTM lead for paid and partnership plays); otherwise blank.
- **Cost-effort**: `$` (under $1K) / `$$` ($1K-$10K) / `$$$` (over $10K), plus a range when known, plus effort (low/med/high). "Rate unknown" beats a guess.
- **In prev?** *(repeat runs only)*: yes / no / changed. Omit the column on a first run.
- Every URL must have been fetched during the run. Audience figures carry their source in parentheses or in Notes.

## Per-tab columns

Shared trailing columns on every lane tab: `Tier | Fit | Reach | Access | Score | Priority | Confidence | [In prev?] | Status | Owner | Notes`. Below are the lane-specific leading columns.

- **Journalists**: `Name | Outlet(s) | Beat (their words) | Recent relevant pieces (2-3 linked, dated) | Story type they write | Pitch angle | Contact route (public) | Staff/freelance | Persona`
- **Publications**: `Name | Type | URL | Audience relevance | Persona | Story angle for their beat | Entry route (earned/contributed/paid) | Guidelines link | Cost-effort`
- **Podcasts**: `Show | Host | URL | Audience signal (sourced) | Persona | Guest/sponsor play | Pitch angle | Booking route | Land difficulty | Cost-effort`
- **Newsletters**: `Name | Author/publisher | URL | Subscribers (sourced) | Persona | Why it fits | Sponsorship route & rate | Non-paid entry play | CPM math (if known) | Cost-effort`
- **Communities**: `Name | Type | URL | Size (sourced) | Who's in it | Persona | Promotion tolerance | Entry play | Cost-effort`
- **Creators-LinkedIn**: `Name | Role/credibility | URL | Followers + engagement quality | Owned assets | Persona | Collab angle | Alignment risk | Cost signal`
- **Creators-YouTube**: `Channel | Format | URL | Subs + median recent views | Audience evidence | Persona | Play type | Sponsorship route/rate | Cost-effort`
- **Creators-X**: `Handle | Follower count | URL | What they engage with | Persona | Play type | Founder-voice dependency (y/n) | Cost signal`
- **Events**: `Name | Subtype | URL | Next date & location | Audience & size | Persona | Why it fits | Stage play (sold/earned/hallway) | CFP deadline | Cost-effort`
- **Analysts & Awards**: `Name | Type (analyst/award/review category) | URL | Why it matters | Persona | Engagement route | Deadline | Cost | Time-to-impact`
- **Partnerships**: `Partner | Type | URL | Audience overlap logic | What they get | Entry route | Persona | Effort-to-live | Cost-effort`
- **GEO**: `Target query / surface | Type | Buyer intent | Who wins it today | Cited sources (cross-ref other lanes) | URL evidence | What we must do | Effort | Date checked`
- **Parked**: `Name | Lane | URL | Persona/purpose | Why parked | The play when activated | Priority (when active) | Confidence`

## LANE INSIGHTS

Each lane tab ends with 3-4 merged-cell insight rows labeled `LANE INSIGHTS`. These are synthesis, not summary: patterns ("guest beats sponsor economics here"), traps ("this community strict-bans vendors"), sequencing ("do X before Y because Z"), and honest thinness flags ("B2B YouTube in this niche is thin; 12 rows is the real universe, not a research failure").

## Shortlist tab

The 12-18 cross-lane plays that matter most in the next 90 days. Columns: `# | Play | Lane | Persona | Why it leads | First action (next 2 weeks) | Est. cost | Timing | Status | Owner`. Rules: every play names a first action a human can do Monday; multi-lane plays (one ecosystem bought as a bundle: community + newsletter + podcast) count as one play; order by impact x urgency; deadline-driven items (CFPs, award cycles, renewal-window events) surface even at lower scores.

## README tab

In order: title + version + build date + scope line (market, personas, lanes in/out, depth setting); HOW TO USE (3-4 lines); LEGEND (Tier, scoring formula, Priority, Confidence, Cost-effort, exactly as defined above); **THE FIVE MOVES THAT MATTER** (five one-liners: if the user does nothing else, these); run stats (entities by lane, % verified, count new vs. previous map where applicable); honest boundaries (what the run could not verify or reach, such as private communities and paywalled rate cards, and how the user could close each gap).

## Formatting

Keep it functional: bold header row, frozen top row, filter on headers, priority column color-scaled (H green / M amber / L gray), reasonable column widths, wrapped text on long-form columns. No decorative theming: this is a working document that will be sorted, filtered, and scribbled on.

## Delivery note (alongside the file)

3-5 sentences: total entities and verified share, the single most surprising find, the recommended first move, and (repeat runs) the delta vs. the previous map: new / confirmed / changed / dead. Do not re-narrate the whole workbook.
