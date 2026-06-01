# Food Chain v2.2 — Product Improvements Design Spec

**Date:** 2026-06-01
**Scope:** Battle gallery, food-chain-pitch skill, spec alignment, 6 engine upgrades

---

## 1. Battle Gallery on Website

### What
New section in `index.html` displaying the 4 existing battle transcripts as browseable cards with expandable full transcripts.

### Placement
After "Why this is different" section, before "Usage". Section header: "Real Battles".

### Card Data (hardcoded from battles/ directory)

| Battle | Outcome | Apex | Hook |
|---|---|---|---|
| Viral Content Repurposer | Restructured | Crow | "Structural intelligence produces convergence" |
| MealBot Office Coordinator | Killed | Crow | Most offices already use contracted caterers |
| Email Audio Briefing | Killed | Lion | Dead zone between consumer price and enterprise compliance |
| AI Meeting Notetaker SME | Survived (pivoted) | Elephant | Microsoft/Google bundle it free |

### Card Design
- Match existing field-guide aesthetic (parchment, green/brown palette)
- Outcome badge: green=survived, amber=restructured, red=killed
- Animal emoji prominent
- Execution mode badge (SUBAGENT/FALLBACK) shown honestly
- "Read full battle" accordion — expands inline, no separate page
- Transcript rendered as styled markdown inside the accordion

### No Build Step
Card data hardcoded in HTML. No markdown parser, no JS framework. When new battles are added, add a card manually.

---

## 2. food-chain-pitch Skill

### What
New skill at `skills/food-chain-pitch/SKILL.md` with dedicated animal library at `skills/food-chain-pitch/references/pitch-animal-library.md`.

### How It Differs from Ideation
Ideation attacks the **idea** (market, ICP, moat, distribution). Pitch attacks the **presentation of the idea to investors** (narrative holes, due diligence traps, financial model weaknesses, founder-market fit gaps).

### Frontmatter
```yaml
name: food-chain-pitch
version: 1.0.0
description: >
  Investor pitch stress-tester. Spawns adversarial agents from a pitch-specific
  behavioral DNA library. Each attacks the pitch narrative, financial model, or
  due diligence surface under strict role-lock. Elimination rounds harden the pitch.
  Works in Claude.ai, Claude Code, Cursor, Windsurf, Copilot with no dependencies.
when_to_use: >
  "food chain pitch", "stress test my pitch", "tear apart my deck",
  "what would investors ask", "due diligence test", "pitch practice",
  "will this raise", "attack my fundraise"
argument-hint: "[your pitch or deck summary]"
```

### Pre-Flight
Asks for: stage (pre-seed/seed/A/B/C), ask amount, key metrics claimed (ARR, growth rate, margins), target investor profile. Mandatory — generic pitch input produces generic attacks.

### Pitch Animal Library (~12 animals)

| Animal | Emoji | Attack Vector |
|---|---|---|
| Vulture | :vulture: | Unit economics — picks apart margins, CAC/LTV, burn math |
| Bloodhound | :dog2: | Due diligence forensics — finds claims that don't survive a check |
| Hyena | :hyena: | Market sizing — tears apart TAM/SAM/SOM methodology |
| Porcupine | :hedgehog: | Defensibility — "what stops Google from doing this Tuesday?" |
| Chameleon | :lizard: | Narrative inconsistency — slide 3 contradicts slide 8 |
| Wolverine | :badger: | Founder-market fit — why YOU, why NOW |
| Praying Mantis | :cricket: | Competition slide — who you conveniently left off |
| Python | :snake: | Revenue model — slow squeeze on pricing assumptions |
| Mosquito | :mosquito: | Small but fatal legal/regulatory/IP detail |
| Cuckoo | :bird: | Borrowed conviction — thesis is someone else's blog post |
| Remora | :fish: | Dependency — your growth is attached to someone else's platform |
| Pangolin | :otter: | Timing — why now? Market timing assumptions that don't hold |

### Engine
Same elimination + absorption loop as ideation. Same subagent/fallback dual mode. Same blind scoring. Differences:
- **Audience agent becomes Investor Simulation** — GP at relevant stage fund, with stated thesis and check size
- **Apex output includes "Due Diligence Survival" section** — top 3 questions a serious investor would ask after reading the pitch, with whether the pitch currently answers them
- **No pivot engine** — dead pitches go back to ideation for product rethink, not to another pitch
- **Real-time data mode** (see Section 4 below) — agents research current market data, competitor funding, comparable exits before attacking

### Output Format
Follows ideation v2.1 markdown table format (not ASCII box art). Same compression rule: subagents produce full attacks, God Agent renders 2-sentence summary + kill shot in tables.

---

## 3. Spec Alignment (3 SKILL.md files)

Mechanical frontmatter update to match ideation v2.1 spec compliance.

### food-chain-code/SKILL.md
- Extract triggers from `description` to new `when_to_use` field
- Add `argument-hint: "[your architecture decision]"`
- Clean `description` to product sentence only
- Bump version to 2.1.0
- Update output format from ASCII box art to markdown tables (match ideation v2.1)

### apex-to-action/SKILL.md
- Extract triggers from `description` to new `when_to_use` field
- Add `argument-hint: "[paste your battle log]"`
- Clean `description`
- Bump version to 2.1.0

### food-chain-monitor/SKILL.md
- Extract triggers from `description` to new `when_to_use` field
- Add `argument-hint: "[paste battle log + what changed]"`
- Clean `description`
- Bump version to 2.1.0

---

## 4. Engine Upgrades (apply to ideation, pitch, code, monitor where relevant)

### 4a. Real-Time Data Mode
**Applies to:** food-chain-pitch (native), food-chain-ideation (v2.2), food-chain-monitor (v2.2)

When WebSearch/WebFetch tools are available:
- Subagents receive instruction: "Before attacking, search for current data on: [competitor names], [market described], [claimed metrics]"
- Kill shots backed by actual current data (funding rounds, product launches, pricing pages, market reports)
- Badge: `Data: LIVE` or `Data: STATIC (training data only — web tools unavailable)`

When tools unavailable: state limitation, use training data, no degradation of core battle logic.

### 4b. Kill Shot Confidence Tags
**Applies to:** all battle skills

Each kill shot tagged:
- **CONFIRMED** — backed by verifiable/verified data (especially with live data mode)
- **PROBABLE** — strong structural signal, high likelihood
- **SPECULATIVE** — plausible but unproven, needs validation

Format in round table: `Kill Shot [CONFIRMED]: "..."` or inline tag after the sentence.

### 4c. Scoring Reasoning
**Applies to:** all battle skills

Blind scoring agent outputs 1-line justification per dimension alongside the score:
```
Specificity: 35/40 — "Names exact API endpoint and rate limit"
Lethality: 28/40 — "Requires platform policy change to kill; not guaranteed"
Survivability: 15/20 — "No known mitigation in current architecture"
```

Rendered in the scoring table as a tooltip/footnote or additional column.

### 4d. Audience Panel (3 ICPs)
**Applies to:** food-chain-ideation (v2.2), food-chain-pitch (investor panel)

Replace single audience agent with panel of 3:
- **Early Adopter** — tech-forward, tries everything, low price sensitivity, high churn risk
- **Mainstream Buyer** — needs proof, references, case studies before committing
- **Skeptical Enterprise** — procurement process, security review, legal approval

Each answers the same 5 questions independently. Divergence between them = distribution insight.

For food-chain-pitch: panel of 3 investor personas (angel, seed GP, Series A partner).

### 4e. Founder Defense Agent
**Applies to:** food-chain-ideation (v2.2), food-chain-pitch (native)

After each round's attacks, before scoring:
- Spawn a **Founder Agent** that sees ALL attacks from that round
- Founder gets 1 defense per attack (2 sentences max)
- Scoring agent receives attacks + defenses, scores on residual lethality after defense
- If defense neutralizes the attack, score drops accordingly

This tests whether the founder can articulate why the attack doesn't apply — not just whether a passive patch fixes it.

### 4f. Animal Selection Reasoning
**Applies to:** all battle skills

God Agent explains selection logic in ecosystem design:
```
Selected: Tapeworm (API dependency) over Remora (feature dependency)
Reason: Dependency is at infrastructure level, not feature level
Rejected: Raccoon (DIY alternative) — ICP is enterprise; DIY is not credible threat
```

Rendered after the ecosystem table as a collapsed/optional section.

---

## 5. Downstream Updates

After all above is implemented:

### CLAUDE.md
- Add food-chain-pitch to repo structure
- Update animal count (32 product + 20 code + 12 pitch = 64)
- Move food-chain-pitch from "Still planned" to "Shipped"

### README.md
- Add pitch to skills table (5 skills now)
- Update "52 animals" to "64 animals" in hero section
- Add pitch to usage examples

### index.html
- Add pitch to skills section
- Battle gallery (Section 1 above)
- Update animal count

### .claude-plugin/plugin.json and marketplace.json
- Update descriptions to mention pitch skill

---

## 6. What's NOT in This Spec

- food-chain-hire, food-chain-price — deferred to next cycle
- Battle memory (structured JSON) — large effort, deferred
- pressure-suite branding — marketing decision, not product
- CI validation for community animals — infrastructure, deferred

---

## Implementation Order

All three main workstreams are independent and can be built in parallel:
1. **Battle Gallery** — HTML/CSS only, touches index.html
2. **food-chain-pitch** — new files only, no existing file edits
3. **Spec Alignment** — mechanical edits to 3 existing SKILL.md files

Engine upgrades (4a-4f) apply after the base work:
4. **Engine upgrades to ideation SKILL.md** — add real-time data, confidence tags, scoring reasoning, audience panel, founder defense, selection reasoning
5. **Engine upgrades to pitch SKILL.md** — native (built in from the start)
6. **Engine upgrades to code/monitor** — applicable subset only
7. **Downstream updates** — CLAUDE.md, README.md, index.html, plugin configs
