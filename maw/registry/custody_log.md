# custody_log 🍥

Chain of custody for everything that enters the Maw. Append only: new entries
go at the bottom; past entries are never edited. A correction is a new entry
that names the one it corrects.

Routine: `../ARRIVAL.md`.

## Entry format

One fenced block per entry:

```yaml
prima_clock: YYYYMMDDHHMM
event:       arrive | route | fracture | advance | flush | leave | pinnacle | correction
item:        <arrival folder, e.g. working/202609230702_example>
from:        <source, or prior pool for a route>
to:          <pool or plank reached>
by:          <who — e.g. eaprime1, nav1>
note:        <one line>
```

## Entries

```yaml
prima_clock: 202605191645
event:       arrive
item:        maw/ at commit f49467b (legacy exception, see below)
from:        Eaprime1/maw PR #1 (copilot/blackjack-iteration-21)
to:          1/3 PLANK / WORK
by:          eaprime1, Copilot
note:        founding Maw docs; recorded retroactively at 202609230702
```

### Legacy exception — the founding docs

The founding docs arrived before this routine existed, so they have no
`working/` arrival folder. Their manifest is fixed by commit: the files under
`maw/` at `f49467b` (the PR #1 merge). List them with:

```bash
git ls-tree -r --name-only f49467b maw/
```

Files added to `maw/` after that commit are not part of this arrival.
