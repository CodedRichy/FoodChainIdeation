# Food Chain

<p align="center">
  <img src="banner.png" alt="Food Chain — Adversarial Stress Test" width="100%" />
</p>

**Your idea has blind spots. This finds them.**

Food Chain spawns adversarial animal agents — each with hardcoded behavioral DNA —
and pits them against your product idea in live elimination rounds. The weakest
argument dies each round. The survivor absorbs its sharpest insight and attacks
a harder version of your idea. One apex predator remains.

That is the thing worth building.

```
claude plugin marketplace add CodedRichy/food-chain-ideation
claude plugin install food-chain-ideation@food-chain-ideation
```

---

## What happens when you run it

You describe your idea. The God Agent reads it, selects animals matched to your
specific threat vectors, states its kill hypothesis, and asks how many agents
you want.

Then this happens:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ROUND 1  ·  5 animals remaining
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🪱 TAPEWORM — Instagram API dependency
Instagram Graph API rate-limits at 200 calls/hr. TikTok Content Posting API
requires individual app review with revocable access. Your entire product
sits on rented land with a landlord who's building the same house.
Kill Shot: The platform adds your feature and terminates the relationship.

🐦‍⬛ CROW — Timing assumption forensics
Platform algorithms are independent — TikTok peaks over 72hrs, YouTube Shorts
over 7 days. Cross-platform "catch the wave" is meaningless. Speed provides
zero algorithmic advantage on destination platforms.
Kill Shot: You're selling a stopwatch in a race that isn't timed.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐦‍⬛ Crow consumes 🐢 Tortoise
Absorbed: authenticity/shadowban concern
Idea patch: Pivot from "publish automatically" to "draft instantly, creator approves"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Four rounds later, the original "viral content repurposer" was dead. The surviving
idea — a cross-creator structural intelligence platform — shared almost no DNA with
what went in. The Crow's final kill: *"Structural intelligence produces convergence.
Thousands of creators using the same tool produce structurally identical posts.
The better the product works, the faster it poisons its own signal."*

That insight is not in any critique tool. It emerged because each attacker was
isolated, role-locked, and forced to find a new angle after each patch.

> Full transcript: [`battles/viral-content-repurposer.md`](battles/viral-content-repurposer.md)

---

## Three outcomes, not one

A tool that only kills ideas is a pessimist. Food Chain produces all three:

| Outcome | What happened |
|---|---|
| **Survived** | Developer tool. Early termination applied — attacks couldn't land structural kills. Core thesis held. |
| **Restructured** | B2B SaaS. ICP corrected from "Indian freelancers" to "newly-registered, enterprise-triggered, 0–2 years compliance history." Distribution rebuilt. Moat found. |
| **Killed** | Office meal coordinator. The stated ICP overwhelmingly uses contracted caterers. The problem the product solved didn't exist. Redirected to B2B caterer procurement intelligence — a completely different business. |

---

## The animals

64 animals across three libraries. Each has hardcoded behavioral DNA —
the God Agent selects, never invents.

**🐦‍⬛ Crow** — Forensic. Finds the structural assumption three levels deep
that everyone overlooked. Quiet, then devastating.

**🪱 Tapeworm** — Lives inside the platform you depend on. Invisible until
you scale. Then the host adds your feature and terminates the relationship.

**🐢 Tortoise** — Has seen every wave of disruption since 2009.
Has a spreadsheet that works fine.

**🦈 Shark** — The incumbent with 200k users who can ship your feature
as a Tuesday sprint toggle.

**🐘 Elephant** — Microsoft/Google adds it to the bundle. Free. Tomorrow.

**🦂 Scorpion** — Compliance. GDPR. SOC 2. The thing you forgot until
a customer's legal team sends the questionnaire.

32 product animals. 20 code-specific animals. 12 pitch animals. Full libraries in
[`animal-library.md`](skills/food-chain-ideation/references/animal-library.md),
[`code-animal-library.md`](skills/food-chain-code/references/code-animal-library.md), and
[`pitch-animal-library.md`](skills/food-chain-pitch/references/pitch-animal-library.md).

---

## Five skills, one install

| Skill | Purpose |
|---|---|
| **food-chain-ideation** | Stress-test product ideas — 32 animals, elimination rounds, blind scoring |
| **food-chain-code** | Stress-test architecture decisions before writing code — 20 code animals |
| **food-chain-pitch** | Stress-test investor pitches — 12 pitch animals, investor simulation panel |
| **apex-to-action** | Turn battle output into a 90-day execution plan with validation gates |
| **food-chain-monitor** | Re-test after pivots or market shifts — 3 animals, 2 rounds, fast verdict |

**Stress-test → Pitch → Execute → Monitor → Re-test.**

---

## Why this is different

Standard adversarial critique gives you four attacks and a summary.
You read them, nod, and build the same thing you were going to build.

Food Chain gives you four attacks where the weakest dies, its insight
transfers to the winner, the idea patches itself, and the next round's
agents attack the *patched* version. The attacks compound. The idea evolves.
The final surviving argument has been pressure-tested by everything the
ecosystem could generate.

**Subagent mode** — In Claude Code, each animal is a separate agent with
zero shared context. Role-lock is architectural, not instructional.
A Crow literally cannot see what the Tapeworm said.

**Blind scoring** — Attacks scored by an independent agent that receives
them anonymized as "Attacker A", "Attacker B". No animal names.
No God Agent self-assessment bias.

**Pivot engine** — When an idea is killed, three pivots auto-generate from
the wreckage, each mini-battled and ranked. You don't leave with "don't
build this." You leave with "build this instead."

**Audience agent** — After the battle, a simulation of your actual ICP
reacts to the evolved idea. "Would you pay for this?"

---

## Usage

```
food chain my idea: [your idea]

what kills this: [your product]

food chain code: [your architecture decision]

food chain pitch: [your pitch or deck summary]

apex to action: [paste your battle log]

food chain monitor: [paste battle log + what changed]
```

---

## Install

**Via Claude Code plugin system (recommended):**

```
claude plugin marketplace add CodedRichy/food-chain-ideation
claude plugin install food-chain-ideation@food-chain-ideation
```

**Manual install:**

```bash
git clone https://github.com/CodedRichy/food-chain-ideation.git
# Project-level (this project only):
cp -r food-chain-ideation/skills .claude/skills
# Or global (all projects):
cp -r food-chain-ideation/skills ~/.claude/skills
```

On Windows, `~/.claude/` is `C:\Users\<you>\.claude\`.

Self-contained markdown — no build step, no config, no dependencies.

Works in Claude.ai, Claude Code, Cursor, Windsurf, Copilot.

<details>
<summary>Repo structure</summary>

```
skills/
├── food-chain-ideation/
│   ├── SKILL.md                    ← product idea battles
│   └── references/
│       └── animal-library.md       ← 32 animals, behavioral DNA
├── food-chain-code/
│   ├── SKILL.md                    ← architecture decision battles
│   └── references/
│       └── code-animal-library.md  ← 20 code-specific animals
├── food-chain-pitch/
│   ├── SKILL.md                    ← investor pitch battles
│   └── references/
│       └── pitch-animal-library.md ← 12 pitch-specific animals
├── apex-to-action/
│   └── SKILL.md                    ← battle output → 90-day plan
└── food-chain-monitor/
    └── SKILL.md                    ← re-test after changes
```

</details>

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Every new animal added by the
community makes every existing installation better retroactively.

---

<details>
<summary>Changelog</summary>

**v2.1.0**
- food-chain-pitch — investor pitch stress-tester with 12 pitch-specific animals
- Real-time data mode — agents search for current market data when web tools available
- Kill shot confidence tags — CONFIRMED / PROBABLE / SPECULATIVE on every attack
- Scoring reasoning — 1-line justification per scoring dimension
- Audience panel — 3 ICP simulations replace single audience agent
- Founder defense agent — active defense between attacks and scoring
- Animal selection reasoning — transparent selection logic in ecosystem design
- Battle gallery on website — 4 real battle transcripts browseable
- Spec alignment — all skills use when_to_use + argument-hint frontmatter

**v2.0.0**
- Subagent mode — architecturally enforced role-lock via independent agents
- Blind scoring agent — anonymous attack evaluation removes self-assessment bias
- Subagent evolution — one-line patch context enables angle evolution without breaking isolation
- Audience agent — ICP simulation reacts to evolved idea after battle
- Pivot engine — auto-generates and mini-battles 3 pivots when idea is killed
- food-chain-code — architecture decision stress-tester with 20 code-specific animals
- apex-to-action — battle output → 90-day execution plan with validation gates
- food-chain-monitor — delta re-testing after changes with 3 animals, 2 rounds max
- Restructured as multi-skill suite — one install, four skills

**v1.3.0**
- Input sharpening — mandatory ICP/geography/problem check before ecosystem design
- Battle quality score — role-lock integrity, animal specificity, kill shot lethality
- Next-move block — validate, build first, never build
- Battle log — compressed session memory for cross-session continuity

**v1.2.0**
- Pre-flight checks — ecosystem validated before battle starts
- God Agent hypothesis — kill prediction stated before round 1
- Early termination rule — strong ideas declared early

**v1.1.0**
- Anti-pattern combinations added to animal library

**v1.0.0**
- Initial release — 16 animals, elimination and absorption loop

</details>
