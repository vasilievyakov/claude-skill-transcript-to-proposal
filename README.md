# Transcript to Proposal

A Claude Code skill that transforms client call transcripts into professional commercial proposals with architecture diagrams and interactive prototypes.

![Demo](assets/demo.gif)

## What it does

You give Claude two things:
1. **Your product description** — what you sell, features, integrations
2. **A transcript** — recording of a client conversation

Claude gives you back three files:
- `proposal.md` — commercial proposal using client's own words
- `architecture.md` — technical architecture with Mermaid diagrams
- `prototype.html` — clickable prototype showing the solution

## How it works

```
┌─────────────────────────────────────────────────────────────┐
│  INPUT                                                       │
│  📦 Product description + 🎙️ Client transcript              │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  STEP 1: Extract & classify pains                           │
│                                                              │
│  🔴 Trigger events (buying now)                             │
│  🟡 Active problems (looking for solution)                  │
│  🟢 Latent issues (aware but passive)                       │
│                                                              │
│  ◆ CHECKPOINT: Confirm priorities with user                 │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  STEP 2: Map solutions                                       │
│                                                              │
│  Pain → Product feature → How it solves → Proof             │
│                                                              │
│  ◆ CHECKPOINT: Confirm architecture with user               │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  STEP 3: Generate proposal                                   │
│                                                              │
│  Using CLIENT'S words from transcript                        │
│  Every claim traces back to pain → feature → result         │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  STEP 4: Build prototype                                     │
│                                                              │
│  Interactive HTML showing the MAIN pain solved              │
│  Real data from client context                               │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  OUTPUT                                                      │
│  📄 proposal.md  📐 architecture.md  🖥️ prototype.html     │
└─────────────────────────────────────────────────────────────┘
```

## Installation

Copy `SKILL.md` to your Claude Code skills directory:

```bash
cp SKILL.md ~/.claude/skills/transcript-to-proposal/SKILL.md
```

Or create the directory first:

```bash
mkdir -p ~/.claude/skills/transcript-to-proposal
cp SKILL.md ~/.claude/skills/transcript-to-proposal/
```

## Usage

In Claude Code, invoke the skill:

```
/transcript-to-proposal
```

Or just mention what you need:

```
I have a transcript from a client call. Help me create a proposal.
```

Claude will ask for:
1. Your product description (paste or attach file)
2. The transcript (paste or attach file)

Then it walks you through the process with checkpoints.

## Example Output

See the full example in [`examples/`](examples/):
- [`transcript.md`](examples/transcript.md) — sales call with Meridian Hotels
- [`product.md`](examples/product.md) — Thornwood Contract Furniture
- [`proposal.md`](examples/proposal.md) — generated proposal
- [`architecture.md`](examples/architecture.md) — solution architecture
- [`prototype.html`](examples/prototype.html) — interactive dashboard

### Proposal excerpt

> **Understanding Your Situation**
>
> Your Q4 satisfaction scores told a clear story: "room comfort dropped 8 points." Ten-year-old sofas are showing their age, and as Marcus put it, you're spending "$40K on repairs across properties" just to keep things functional.
>
> The sleeper sofas are the real pain point. Mechanisms jam, mattresses are thin, housekeeping loses "5 minutes to room turnover" per room fighting with the fold-out systems.

### Architecture diagram

```mermaid
graph TB
    subgraph "Client Requirements"
        R1[847 Total Units]
        R2[70 Unit Pilot]
        R3[March 15 Deadline]
    end

    subgraph "Product Configuration"
        P1[EasyRest Sleeper Sofas]
        P2[Metropolitan Standard]
        P3[Fabric Program]
    end

    subgraph "Manufacturing"
        M1[Rush Production]
        M2[Quality Control]
        M3[Fire Compliance]
    end

    R2 --> P1
    R2 --> P2
    P1 --> M1
    P2 --> M1
    M1 --> M2
    M2 --> M3
```

### Prototype screenshot

![Prototype](assets/prototype-screenshot.png)

## Key Features

**Pain Classification Framework**
- **Level**: Strategic / Tactical / Operational
- **Urgency**: Trigger event / Active / Latent
- **Speaker**: Decision maker / Influencer / User

**Trigger Event Detection**
- "Management is asking..."
- "By end of quarter..."
- "We already tried X, didn't work..."
- External deadlines, compliance requirements

**Human-in-the-Loop**
- Checkpoint after pain analysis
- Checkpoint after architecture
- User confirms before each major step

## Why This Works

1. **Uses client's words** — proposals feel personal, not generic
2. **Traces every claim** — pain → feature → result chain
3. **Prioritizes trigger events** — focuses on what makes them buy NOW
4. **Shows, doesn't tell** — prototype demonstrates the solution

## License

MIT

## Credits

Built with [Claude Code](https://claude.ai/code) skills system.
