# ARRIVAL — how content enters the Maw

Carbonite Timestamp: 202609230702  
State: 1/3 PLANK / WORK  
Chain of Custody: OPEN

The mechanics are already written in `PRIMAL_COSMOLOGY.md`, `events/` and the
pool folders. This file is the routine that walks material through them. It
does not add cosmology. Where the routine meets a question the canon hasn't
answered, it holds that question open (see **Open questions** below).

## The routine

```text
arrive → record → route → transform → advance → (leave)
```

### 1. Arrive — waterfall entry

Material crosses the waterfall threshold (`events/waterfall_entry.md`). In the
repo, that means one arrival folder under `working/`:

```text
maw/working/<prima-clock>_<slug>/
  ARRIVAL.md        ← carbonite header + arrival record (template below)
  <source files>    ← the material exactly as it arrived
```

- `<prima-clock>` is `YYYYMMDDHHMM` at arrival (`date '+%Y%m%d%H%M'`).
- `<slug>` is lowercase-with-hyphens. It names the mechanics, not the source
  (`registry/naming_protocol.md`).
- Source files land unedited. A `.docx` or `.pdf` source keeps its original;
  a `.md` rendering of it sits next to it as a witness copy and is marked as
  one.

### 2. Record — chain of custody

Append one entry to `registry/custody_log.md` in the same commit as the
arrival. No arrival without a log entry. The log is append only.

### 3. Route — choose a pool

Each arrival rests in exactly one place at a time. Routing moves the arrival
folder; the log records every move.

- **`working/`**: active germ material, being worked now
  (`working/README.md`).
- **`sacred_pools/`**: Commit-state, accumulating charge before flush
  (`sacred_pools/README.md`, `charge_tank_mechanics.md`).
- **`mobius_rings/`**: drifting, no assigned vector yet; held until a purpose
  is defined (`mobius_rings/README.md`).
- **`feeds/<feed>/`**: change of form is the work: `fractalization`,
  `pixelization` or `sparklization` (`feeds/*/README.md`).

An arrival that is unclear goes to `mobius_rings/`, not into `working/`.
Holding pattern is a valid state, not a failure.

### 4. Transform — fracture into components

Fracture writes new files; it never rewrites the arrival's source files.
Components go in the arrival folder under `components/`, each naming which
particle, event or feed it belongs to (`particles/particle_table.md`,
`events/`). The whole form stays readable beside its parts.

A cluster that must move as one body (transcript + references + core files)
is wrapped before flush: list its members in the arrival record under
**Testa Membrane** (`charge_tank_mechanics.md`).

### 5. Advance — plank progression

| Plank | Meaning here |
| --- | --- |
| 1/3 WORK | Arrived and recorded. Source intact, routed |
| 2/3 STRUCTURE | Components fractured and named against particles / events |
| 3/3 READY | Reviewed by eaprime1; ready for a Pinnacle decision |
| ♠️ Pinnacle | Only with a custody log entry naming the decision |

Each step up is a log entry and an update to the arrival's header.

### 6. Leave — held

Where material goes when it leaves the Maw is not settled (see below). Until
it is, nothing leaves: 3/3 material waits in place with its log entry.

## Arrival record template

Copy into `maw/working/<prima-clock>_<slug>/ARRIVAL.md`:

```markdown
# <slug>

Carbonite Timestamp: <prima-clock>  
State: 1/3 PLANK / WORK  
Chain of Custody: OPEN

- **Arrived from:** <where it came from — repo, Drive folder, chat, device>
- **Carried by:** <who brought it — e.g. eaprime1, nav1>
- **Form on arrival:** <files and formats, as they landed>
- **Pool:** working | sacred_pools | mobius_rings | feeds/<feed>
- **One-line signal:** <what it is, in one line>

## Testa Membrane

<files that must move together, or "none">

## Components

<filled at 2/3: component file → particle / event / feed>

## Open door

<one question this arrival leaves open>
```

## Checks before a PR

```bash
bash tools/scan_lexeme.sh maw/     # advisory: unfilled template fields
ls maw/working/                    # every arrival folder has an ARRIVAL.md
```

Every arrival folder in the PR has a matching `registry/custody_log.md` entry.

## Open questions — held for eaprime1

- **Where the Maw sits in the chain.** The Act II handoff reads
  *Unknowable → Maw → Known_naught → Nullus*. The nullus canon
  (`eaprime1/nullus`, `docs/architecture.md`) reads
  *ANTE-ESSE → THE/SPHINCTER → MAW → System Canon*. This repo's own
  `events/waterfall_entry.md` has material arriving *from* the Sphincter
  threshold, which matches the nullus reading. Carry both; pick neither.
- **Outbound.** Where 3/3 material goes (Nullus intake, System Canon, back to
  custos) follows from the question above.
- **Flush.** `charge_tank_mechanics.md` describes a flush at critical
  resonance. What a flush does to files in `sacred_pools/` (moves them
  deeper, releases them outbound) is not yet defined, so no flush happens by
  routine.
